<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DEVIN PORTAL - All India Digital Seva Hub</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f4f7f6;
            margin: 0;
            padding: 0;
            color: #333;
        }
        /* Navigation Bar */
        nav {
            background-color: #0f4c81;
            padding: 15px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 4px solid #ff9933;
        }
        .logo { color: white; font-weight: bold; font-size: 22px; letter-spacing: 1px; }
        .auth-status { color: #fff; font-weight: bold; }
        .logout-btn {
            background-color: #e65c00; color: white; border: none;
            padding: 8px 15px; border-radius: 5px; cursor: pointer; font-weight: bold;
            display: none;
        }

        /* Header */
        header {
            background: linear-gradient(rgba(15, 76, 129, 0.9), rgba(19, 48, 96, 0.9)), url('https://images.unsplash.com/photo-1532375811409-905115c3b4a3?auto=format&fit=crop&w=1200&q=80');
            background-size: cover; background-position: center;
            color: white; text-align: center; padding: 60px 20px;
        }
        header h1 { margin: 0; font-size: 38px; }
        header p { margin: 10px 0 0 0; color: #ff9933; font-weight: bold; font-size: 18px; }

        /* Lock Screen & Auth Boxes */
        .auth-container {
            max-width: 450px; margin: 50px auto; background: white;
            padding: 40px 30px; border-radius: 8px; box-shadow: 0 4px 15px rgba(0,0,0,0.1);
            text-align: center; border-top: 4px solid #ff9933;
        }
        .form-group { margin-bottom: 15px; text-align: left; }
        .form-group label { display: block; margin-bottom: 5px; font-weight: bold; }
        .form-group input { width: 100%; padding: 10px; border: 1px solid #ccc; border-radius: 5px; box-sizing: border-box; }
        .auth-btn { width: 100%; background-color: #0f4c81; color: white; border: none; padding: 12px; border-radius: 5px; font-size: 16px; font-weight: bold; cursor: pointer; margin-top: 10px; }
        .auth-switch { margin-top: 20px; font-size: 14px; color: #666; }
        .auth-switch a { color: #0f4c81; font-weight: bold; text-decoration: none; cursor: pointer; }

        /* Main Content Workspace */
        .workspace {
            display: none; max-width: 1400px; margin: 40px auto; padding: 0 20px;
        }
        .section-title { color: #0f4c81; margin-top: 35px; border-bottom: 2px solid #ff9933; padding-bottom: 8px; }
        .section-title:first-of-type { margin-top: 0; }
        
        /* Grid Layout */
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; margin-top: 20px; margin-bottom: 20px; }
        
        .card { 
            background: white; border-radius: 8px; padding: 20px; 
            box-shadow: 0 4px 6px rgba(0,0,0,0.05); border-left: 4px solid #0f4c81;
            cursor: pointer; transition: 0.2s;
        }
        .card:hover { transform: translateY(-3px); box-shadow: 0 6px 12px rgba(0,0,0,0.1); background-color: #fbfcfc; }
        .card h3 { margin-top: 0; color: #133060; font-size: 17px; }
        .card p { color: #666; font-size: 13px; line-height: 1.4; margin-bottom: 15px; height: 40px; overflow: hidden; }
        
        .action-area { display: flex; justify-content: space-between; align-items: center; gap: 8px; }
        .info-link { color: #0f4c81; font-weight: bold; font-size: 12px; text-decoration: underline; }
        
        .btn-group { display: flex; gap: 5px; }
        .card .btn { background-color: #ff9933; color: white; text-decoration: none; padding: 6px 12px; border-radius: 4px; font-weight: bold; font-size: 11px; text-align: center; }
        .card .btn-yt { background-color: #e62117; color: white; }

        /* Detail Panel Box */
        .detail-panel {
            display: none; background: #fff; border: 1px solid #ddd; 
            border-top: 4px solid #ff9933; border-radius: 8px; padding: 25px; 
            margin-top: 10px; margin-bottom: 20px; grid-column: 1 / -1; box-shadow: inset 0 2px 8px rgba(0,0,0,0.05);
        }
        .detail-panel h4 { margin-top: 0; color: #0f4c81; font-size: 19px; }
        .detail-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px; margin-top: 15px; }
        .detail-box { background: #f9fbfd; padding: 12px; border-radius: 5px; border: 1px solid #eaeaea; font-size: 13px; }
        .detail-box strong { color: #133060; display: block; margin-bottom: 5px; }
        .close-panel-btn { float: right; background: #ccc; border: none; padding: 4px 10px; border-radius: 3px; cursor: pointer; font-size: 12px; }

        /* SIMPLE AI WIDGET STYLES */
        .ai-widget {
            position: fixed; bottom: 20px; right: 20px; z-index: 1000;
            font-family: Arial, sans-serif; display: none;
        }
        .ai-button {
            background-color: #0f4c81; color: white; border: none;
            padding: 15px 20px; border-radius: 50px; font-weight: bold;
            cursor: pointer; box-shadow: 0 4px 10px rgba(0,0,0,0.2);
            display: flex; align-items: center; gap: 8px;
        }
        .ai-button:hover { background-color: #133060; }
        .ai-box {
            display: none; width: 335px; background: white;
            border-radius: 10px; border-top: 4px solid #ff9933;
            box-shadow: 0 5px 20px rgba(0,0,0,0.15); overflow: hidden;
            position: absolute; bottom: 65px; right: 0;
        }
        .ai-header { background: #0f4c81; color: white; padding: 12px; font-weight: bold; display: flex; justify-content: space-between; align-items: center; }
        .ai-close { cursor: pointer; background: none; border: none; color: white; font-size: 16px; }
        .ai-chat-logs { height: 220px; overflow-y: auto; padding: 10px; font-size: 13px; background: #f9f9f9; display: flex; flex-direction: column; gap: 8px; }
        .msg { padding: 8px 12px; border-radius: 5px; max-width: 85%; line-height: 1.4; }
        .msg.bot { background: #e2f0fd; color: #133060; align-self: flex-start; }
        .msg.user { background: #ff9933; color: white; align-self: flex-end; }
        .ai-input-area { display: flex; border-top: 1px solid #ddd; }
        .ai-input-area input { flex: 1; border: none; padding: 10px; outline: none; }
        .ai-input-area button { background: #ff9933; color: white; border: none; padding: 10px 15px; cursor: pointer; font-weight: bold; }

        footer { background-color: #222; color: #ccc; text-align: center; padding: 15px; margin-top: 60px; }
    </style>
</head>
<body>

    <!-- Top Navbar -->
    <nav>
        <div class="logo">🌐 DEVIN PORTAL</div>
        <div>
            <span id="navStatus" class="auth-status">🔒 Portal Locked</span>
            <button id="logoutBtn" class="logout-btn" onclick="logout()">Logout</button>
        </div>
    </nav>

    <!-- Header Banner -->
    <header>
        <h1>Welcome to DEVIN PORTAL</h1>
        <p>Your Secure Integrated Gateway for Indian Government Services & Directories</p>
    </header>

    <!-- 1. AUTHENTICATION MODULE -->
    <div id="authModule">
        <!-- Sign In Form -->
        <div class="auth-container" id="loginBox">
            <h2>Sign In to Access Network</h2>
            <p style="color: #666; font-size: 14px; margin-bottom: 25px;">Provide access keys to read nationwide government service databases.</p>
            <form onsubmit="handleLogin(event)">
                <div class="form-group">
                    <label>Operator ID / Email</label>
                    <input type="text" id="loginUser" placeholder="Enter username" required>
                </div>
                <div class="form-group">
                    <label>Password</label>
                    <input type="password" id="loginPass" placeholder="Enter password" required>
                </div>
                <button type="submit" class="auth-btn">Secure Login 🔓</button>
            </form>
            <div class="auth-switch">
                New Operator? <a onclick="switchAuth('signup')">Create an Account</a>
            </div>
        </div>

        <!-- Sign Up Form -->
        <div class="auth-container" id="signupBox" style="display: none;">
            <h2>Operator Registration (Sign Up)</h2>
            <p style="color: #666; font-size: 14px; margin-bottom: 25px;">Register new operator credentials to the local secure network infrastructure.</p>
            <form onsubmit="handleSignup(event)">
                <div class="form-group">
                    <label>Full Name</label>
                    <input type="text" id="regName" placeholder="Enter your full name" required>
                </div>
                <div class="form-group">
                    <label>Create Operator ID / Email</label>
                    <input type="text" id="regUser" placeholder="Choose username" required>
                </div>
                <div class="form-group">
                    <label>Choose Secure Password</label>
                    <input type="password" id="regPass" placeholder="Create password" required>
                </div>
                <button type="submit" class="auth-btn" style="background-color: #ff9933;">Register & Account Active 📝</button>
            </form>
            <div class="auth-switch">
                Already registered? <a onclick="switchAuth('login')">Sign In here</a>
            </div>
        </div>
    </div>

    <!-- 2. MAIN WORKSPACE -->
    <div class="workspace" id="mainWorkspace">
        
        <!-- CATEGORY 1: Central Government Core Services -->
        <h2 class="section-title">1. Central Government Core Services & Identity</h2>
        <div class="grid">
            
            <!-- Aadhaar Card -->
            <div class="card" onclick="toggleDetails('uidaiDetails')">
                <h3>Aadhaar Card (UIDAI)</h3>
                <p>Core national identification framework. Governs digital biometric updates and verification.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=how+to+update+aadhaar+card+online" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://uidai.gov.in" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="uidaiDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('uidaiDetails', event)">X Close</button>
                <h4>Aadhaar Card Service Details</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Who Needs It:</strong> All citizens of India.</div>
                    <div class="detail-box"><strong>Required Documents:</strong> Valid Birth Certificate, Parent ID, Address Proof.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Mandated for bank accounts, SIM cards, government welfare.</div>
                </div>
            </div>

            <!-- PAN Card -->
            <div class="card" style="border-left-color: #ff9933;" onclick="toggleDetails('panDetails')">
                <h3>PAN Card Portal</h3>
                <p>Permanent Account Number management used for identifying financial transactions and tax remittance.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=how+to+apply+pan+card+online" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://www.onlineservices.nsdl.com" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="panDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('panDetails', event)">X Close</button>
                <h4>PAN Card Service Details</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Who Needs It:</strong> Taxpayers, businesses, and bank clients.</div>
                    <div class="detail-box"><strong>Required Documents:</strong> Identity proof, Address Proof, Photos.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Mandatory for filing ITR and high-value transfers.</div>
                </div>
            </div>

            <!-- Passport Seva -->
            <div class="card" onclick="toggleDetails('passportDetails')">
                <h3>Passport Seva Portal</h3>
                <p>Official dynamic framework for processing new passport applications, renewals, and police verification.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=passport+online+apply+process" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://www.passportindia.gov.in" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="passportDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('passportDetails', event)">X Close</button>
                <h4>Passport Seva Service Details</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Who Needs It:</strong> Indian Citizens traveling abroad.</div>
                    <div class="detail-box"><strong>Required Documents:</strong> Aadhaar card, PAN, LC, utilities bill.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Global citizenship identification and travel authorization.</div>
                </div>
            </div>

            <!-- Voter ID -->
            <div class="card" style="border-left-color: #ff9933;" onclick="toggleDetails('voterDetails')">
                <h3>Voter Services (NVSP)</h3>
                <p>Electoral roll registration database system for issuing official voter identity profiles.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=how+to+apply+for+voter+id+card+online" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://voters.eci.gov.in" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="voterDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('voterDetails', event)">X Close</button>
                <h4>Voter Registration Details</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Eligibility:</strong> Indian Citizens aged 18 years or older.</div>
                    <div class="detail-box"><strong>Required Documents:</strong> Age proof and local Address Proof.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Gives right to vote and serves as identity validation.</div>
                </div>
            </div>

            <!-- DigiLocker -->
            <div class="card" onclick="toggleDetails('digilockerDetails')">
                <h3>DigiLocker Hub</h3>
                <p>Cloud-based platform for issuance, storage, and verification of authentic digital documents & certificates.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=how+to+use+digilocker+app" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://www.digilocker.gov.in" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="digilockerDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('digilockerDetails', event)">X Close</button>
                <h4>DigiLocker Service Details</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Who Needs It:</strong> Anyone looking for paperless document management.</div>
                    <div class="detail-box"><strong>Required Documents:</strong> Aadhaar Card linked with active Mobile Number.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Legally at par with original physical documents under IT Act.</div>
                </div>
            </div>
        </div>

        <!-- CATEGORY 2: Skill Development & Career Opportunities -->
        <h2 class="section-title">2. Skill India & Employment Portals</h2>
        <div class="grid">
            
            <!-- Skill India Digital -->
            <div class="card" style="border-left-color: #0f4c81;" onclick="toggleDetails('skillIndiaDetails')">
                <h3>Skill India Digital Portal</h3>
                <p>Unified platform for skill development courses, digital resumes, and direct industry job links.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=how+to+register+on+skill+india+digital" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://www.skillindiadigital.gov.in" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="skillIndiaDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('skillIndiaDetails', event)">X Close</button>
                <h4>Skill India Portal Details</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Target Audience:</strong> Students, youth, and workers looking to upgrade skills.</div>
                    <div class="detail-box"><strong>Courses Available:</strong> Technology, AI, craftsmanship, hospitality, and corporate trends.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Direct access to free certifications, government courses, and verified digital skill cards.</div>
                </div>
            </div>

            <!-- National Career Service -->
            <div class="card" style="border-left-color: #ff9933;" onclick="toggleDetails('ncsDetails')">
                <h3>National Career Service (NCS)</h3>
                <p>Ministry of Labour gateway connecting job seekers with open corporate and government job vacancies.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=national+career+service+registration" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://www.ncs.gov.in" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="ncsDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('ncsDetails', event)">X Close</button>
                <h4>NCS Employment Platform Matrix</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Who Can Register:</strong> Unemployed youth, freelancers, and working professionals.</div>
                    <div class="detail-box"><strong>Required Details:</strong> Education documents, basic identity credentials, work history.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Free job match systems, career counseling data, and genuine local job listings.</div>
                </div>
            </div>

            <!-- PMKVY Scheme -->
            <div class="card" style="border-left-color: #0f4c81;" onclick="toggleDetails('pmkvyDetails')">
                <h3>PM Kaushal Vikas Yojana (PMKVY)</h3>
                <p>Flagship outcome-based skill training scheme offering monetary rewards and placement assistance.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=pmkvy+free+course+admission+process" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://www.pmkvyofficial.org" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="pmkvyDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('pmkvyDetails', event)">X Close</button>
                <h4>PMKVY Scheme Details</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Eligibility:</strong> Unemployed youth or school/college dropouts with Indian citizenship.</div>
                    <div class="detail-box"><strong>Fees Structure:</strong> 100% Free training fully sponsored by the central government.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Industry-recognized certification, assessment alignment, and livelihood support.</div>
                </div>
            </div>
        </div>

        <!-- CATEGORY 3: Central Government Schemes & Travel (IRCTC) -->
        <h2 class="section-title">3. Central Schemes, Finance & Travel (IRCTC)</h2>
        <div class="grid">

            <!-- IRCTC Ticket Booking -->
            <div class="card" style="border-left-color: #ff9933;" onclick="toggleDetails('irctcDetails')">
                <h3>IRCTC Railway Booking</h3>
                <p>Official Indian Railways network gateway for passenger train ticket booking, PNR check, and schedules.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=how+to+book+train+ticket+in+irctc" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://www.irctc.co.in" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="irctcDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('irctcDetails', event)">X Close</button>
                <h4>IRCTC Ticket Booking Details</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Who Needs It:</strong> Anyone traveling across India via train network.</div>
                    <div class="detail-box"><strong>Required Documents:</strong> Valid ID Card during journey.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Instant digital seat allocation, easy cancellation, and refund tracking.</div>
                </div>
            </div>
            
            <!-- PM-Kisan Samman Nidhi -->
            <div class="card" onclick="toggleDetails('pmKisanDetails')">
                <h3>PM-Kisan Samman Nidhi</h3>
                <p>Central scheme providing financial backup and annual income support directly to all landholding farmers.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=pm+kisan+yojana+registration+process" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://pmkisan.gov.in" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="pmKisanDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('pmKisanDetails', event)">X Close</button>
                <h4>PM-Kisan Scheme Breakdown</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Financial Benefit:</strong> ₹6,000 per year transferred directly in 3 installments.</div>
                    <div class="detail-box"><strong>Required Documents:</strong> Land Registry Documents, Aadhaar Card, Bank Account.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Direct structural financial protection without any middlemen.</div>
                </div>
            </div>

            <!-- Ayushman Bharat (PM-JAY) -->
            <div class="card" style="border-left-color: #ff9933;" onclick="toggleDetails('ayushmanDetails')">
                <h3>Ayushman Bharat (PM-JAY)</h3>
                <p>National health protection mission offering paperless, cashless health insurance coverage for families.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=how+to+apply+ayushman+card+online" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://dashboard.pmjay.gov.in" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="ayushmanDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('ayushmanDetails', event)">X Close</button>
                <h4>Ayushman Bharat Service Details</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Insurance Limit:</strong> Free health cover up to ₹5 Lakhs per family per year.</div>
                    <div class="detail-box"><strong>Eligible Targets:</strong> Economically vulnerable or poor rural/urban families.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Cashless treatment access at secondary and tertiary hospitals.</div>
                </div>
            </div>

            <!-- Income Tax Department -->
            <div class="card" onclick="toggleDetails('itDetails')">
                <h3>Income Tax E-Filing</h3>
                <p>Federal fiscal repository handling financial year returns (ITR), tracking refunds, and checking link criteria.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=how+to+file+itr+online" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://www.incometax.gov.in" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="itDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('itDetails', event)">X Close</button>
                <h4>Income Tax Return Services</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Who Needs It:</strong> Salaried individuals, business operators, companies.</div>
                    <div class="detail-box"><strong>Required Documents:</strong> Form 16, Bank statements, Investment declarations.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Legal financial records, mandatory for processing visa.</div>
                </div>
            </div>

            <!-- GST Portal -->
            <div class="card" style="border-left-color: #ff9933;" onclick="toggleDetails('gstDetails')">
                <h3>GST Common Portal</h3>
                <p>Unified business architecture handling Goods and Services Tax ledger accounting, invoicing, and updates.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=gst+registration+and+return+filing" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://www.gst.gov.in" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="gstDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('gstDetails', event)">X Close</button>
                <h4>GST Portal System Matrix</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Who Needs It:</strong> Manufacturers, vendors, and business owners.</div>
                    <div class="detail-box"><strong>Required Documents:</strong> PAN card, business certificate, bank proof.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Smooth inter-state trading channels and valid tax credits.</div>
                </div>
            </div>
        </div>

        <!-- CATEGORY 4: State Infrastructure (Gujarat) -->
        <h2 class="section-title">4. Gujarat State Government Integrated Services</h2>
        <div class="grid">
            
            <!-- RTE Admission Portal -->
            <div class="card" onclick="toggleDetails('rteDetails')">
                <h3>RTE Admission (Right to Education)</h3>
                <p>Free primary education allocation framework under government quotas in private unassisted schools.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=rte+gujarat+admission+process" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://rte.orpgujarat.com" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="rteDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('rteDetails', event)">X Close</button>
                <h4>RTE Gujarat Admission Details</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Eligibility Criteria:</strong> Children aged 5+ years from economically weaker groups.</div>
                    <div class="detail-box"><strong>Required Documents:</strong> Birth Certificate, Parent Income, Residence Proof.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> 100% Free Primary Education in private schools.</div>
                </div>
            </div>

            <!-- Digital Gujarat -->
            <div class="card" style="border-left-color: #ff9933;" onclick="toggleDetails('gujDetails')">
                <h3>Digital Gujarat Portal</h3>
                <p>State unified portal processing Income Certificates, Caste verifications, and scholarships.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=digital+gujarat+scholarship+income+certificate" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://www.digitalgujarat.gov.in" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="gujDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('gujDetails', event)">X Close</button>
                <h4>Digital Gujarat Services Breakdown</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Services Included:</strong> Caste Proofs, EWS, Domicile, Ration Card edits.</div>
                    <div class="detail-box"><strong>Required Documents:</strong> Electricity bills, income affidavits, Panchayat records.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Access to state-level reservation systems and student scholarships.</div>
                </div>
            </div>

            <!-- AnyROR @ Anywhere -->
            <div class="card" onclick="toggleDetails('anyrorDetails')">
                <h3>AnyROR @ Anywhere</h3>
                <p>Verified revenue land intelligence infrastructure monitoring 7/12 (Satbara) and 8A records online.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=anyror+gujarat+7+12+satbara+online" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://anyror.gujarat.gov.in" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="anyrorDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('anyrorDetails', event)">X Close</button>
                <h4>AnyROR Land Record Details</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Who Needs It:</strong> Property buyers, farmers, legal land handlers.</div>
                    <div class="detail-box"><strong>Required Documents:</strong> District, Taluka, Village and Survey Number.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Protects against frauds; instant certified land record downloads.</div>
                </div>
            </div>

            <!-- i-Khedut -->
            <div class="card" style="border-left-color: #ff9933;" onclick="toggleDetails('ikhedutDetails')">
                <h3>i-Khedut Portal</h3>
                <p>Dedicated ecosystem offering technological subsidies, welfare tracking, and financial aid to state farmers.</p>
                <div class="action-area">
                    <span class="info-link">Click for Details ℹ️</span>
                    <div class="btn-group">
                        <a href="https://www.youtube.com/results?search_query=ikhedut+portal+gujarat+yojana" target="_blank" class="btn btn-yt" onclick="event.stopPropagation();">Watch Video 📺</a>
                        <a href="https://ikhedut.gujarat.gov.in" target="_blank" class="btn" onclick="event.stopPropagation();">Official Site</a>
                    </div>
                </div>
            </div>
            <div id="ikhedutDetails" class="detail-panel">
                <button class="close-panel-btn" onclick="closeDetails('ikhedutDetails', event)">X Close</button>
                <h4>i-Khedut Scheme Details</h4>
                <div class="detail-grid">
                    <div class="detail-box"><strong>Who Needs It:</strong> Registered farmers of Gujarat.</div>
                    <div class="detail-box"><strong>Required Documents:</strong> Land 8A/7-12 details, Bank passbook, Aadhaar.</div>
                    <div class="detail-box"><strong>Key Benefits:</strong> Direct financial support for tractor purchases and seeds.</div>
                </div>
            </div>
        </div>

    </div>

    <!-- 3. SIMPLE AI ASSISTANT WIDGET -->
    <div class="ai-widget" id="aiWidget">
        <button class="ai-button" onclick="toggleAiBox()">🤖 AI Help Desk</button>
        <div class="ai-box" id="aiBox">
            <div class="ai-header">
                <span>Devin AI Assistant</span>
                <button class="ai-close" onclick="toggleAiBox()">X</button>
            </div>
            <div class="ai-chat-logs" id="aiLogs">
                <div class="msg bot">Hello! If you are confused or facing any issue regarding any service, ask me here. I will guide you or open helpful videos for you!</div>
            </div>
            <div class="ai-input-area">
                <input type="text" id="aiInput" placeholder="Type your query here..." onkeypress="handleAiKey(event)">
                <button onclick="askSimpleAi()">Send</button>
            </div>
        </div>
    </div>

    <footer>
        <p>© 2026 DEVIN PORTAL - Integrated Digital India Infrastructure Hub. All rights reserved.</p>
    </footer>

    <!-- System Control Logic Script -->
    <script>
        if (!localStorage.getItem('devinUsers')) {
            var defaultDatabase = { "admin": "admin123" };
            localStorage.setItem('devinUsers', JSON.stringify(defaultDatabase));
        }

        function switchAuth(mode) {
            if(mode === 'signup') {
                document.getElementById('loginBox').style.display = 'none';
                document.getElementById('signupBox').style.display = 'block';
            } else {
                document.getElementById('loginBox').style.display = 'block';
                document.getElementById('signupBox').style.display = 'none';
            }
        }

        function handleSignup(event) {
            event.preventDefault();
            var username = document.getElementById('regUser').value.trim();
            var password = document.getElementById('regPass').value;
            var fullName = document.getElementById('regName').value;
            var currentUsers = JSON.parse(localStorage.getItem('devinUsers'));

            if(currentUsers[username]) {
                alert("This Operator ID is already registered!");
                switchAuth('login');
                return;
            }

            currentUsers[username] = password;
            localStorage.setItem('devinUsers', JSON.stringify(currentUsers));
            alert("Registration Successful for " + fullName + "!");
            switchAuth('login');
        }

        function handleLogin(event) {
            event.preventDefault();
            var user = document.getElementById('loginUser').value.trim();
            var pass = document.getElementById('loginPass').value;
            var currentUsers = JSON.parse(localStorage.getItem('devinUsers'));

            if (currentUsers[user] && currentUsers[user] === pass) {
                alert("Access Granted!");
                document.getElementById('authModule').style.display = 'none';
                document.getElementById('mainWorkspace').style.display = 'block'; 
                document.getElementById('logoutBtn').style.display = 'block';
                document.getElementById('aiWidget').style.display = 'block';
                
                var navStatus = document.getElementById('navStatus');
                navStatus.innerText = "🔓 Connected as: " + user;
                navStatus.style.color = "#a3e635"; 
            } else {
                alert("Invalid Operator ID or Password!");
            }
        }

        function logout() {
            if (confirm("Are you sure you want to log out?")) {
                document.getElementById('authModule').style.display = 'block';
                document.getElementById('mainWorkspace').style.display = 'none';
                document.getElementById('logoutBtn').style.display = 'none';
                document.getElementById('aiWidget').style.display = 'none';
                var navStatus = document.getElementById('navStatus');
                navStatus.innerText = "🔒 Portal Locked";
                navStatus.style.color = "#fff";
                switchAuth('login');
            }
        }

        function toggleDetails(panelId) {
            var panel = document.getElementById(panelId);
            if (panel.style.display === "block") {
                panel.style.display = "none";
            } else {
                var activePanels = document.querySelectorAll('.detail-panel');
                activePanels.forEach(function(p) { p.style.display = 'none'; });
                panel.style.display = "block";
            }
        }

        function closeDetails(panelId, event) {
            if (event) event.stopPropagation();
            document.getElementById(panelId).style.display = "none";
        }

        /* SIMPLE AI ENGINE LOGIC */
        function toggleAiBox() {
            var box = document.getElementById('aiBox');
            box.style.display = (box.style.display === 'block') ? 'none' : 'block';
        }

        function handleAiKey(e) {
            if(e.key === 'Enter') askSimpleAi();
        }

        function askSimpleAi() {
            var input = document.getElementById('aiInput');
            var text = input.value.trim().toLowerCase();
            if(!text) return;

            var logs = document.getElementById('aiLogs');
            logs.innerHTML += '<div class="msg user">' + input.value + '</div>';
            input.value = "";
            logs.scrollTop = logs.scrollHeight;

            setTimeout(function() {
                var reply = "I didn't quite catch that. Please type keywords like 'IRCTC', 'Skill', 'Job', 'Aadhaar', 'PAN', or 'Kisan' so I can assist you better.";
                
                if(text.includes('skill') || text.includes('course') || text.includes('pmkvy') || text.includes('training')) {
                    reply = "To learn new skills or find free government courses, check out the Skill India Digital and PMKVY cards. To check directly, <a href='https://www.youtube.com/results?search_query=skill+india+digital+free+courses+registration' target='_blank' style='color:#0f4c81; font-weight:bold;'>click here to watch the registration guide</a>.";
                } else if(text.includes('job') || text.includes('employment') || text.includes('ncs')) {
                    reply = "You can find job links inside the National Career Service (NCS) card. For a quick profile setup guide, <a href='https://www.youtube.com/results?search_query=national+career+service+portal+job+apply' target='_blank' style='color:#0f4c81; font-weight:bold;'>click here to watch the video tutorial</a>.";
                } else if(text.includes('irctc') || text.includes('train') || text.includes('ticket')) {
                    reply = "To book train tickets or track PNR, click on the 'Official Site' inside the IRCTC card. If you want a setup tutorial, <a href='https://www.youtube.com/results?search_query=irctc+account+create+and+ticket+booking' target='_blank' style='color:#0f4c81; font-weight:bold;'>click here to watch the complete YouTube guide</a>.";
                } else if(text.includes('aadhaar') || text.includes('aadhar')) {
                    reply = "To update or create an Aadhaar card, click on the red 'Watch Video' button on the Aadhaar card layout or use the Official Site. Still confused? <a href='https://www.youtube.com/results?search_query=aadhaar+card+online+help' target='_blank' style='color:#0f4c81; font-weight:bold;'>Click here to watch YouTube guide directly</a>.";
                } else if(text.includes('pan')) {
                    reply = "The PAN Card section includes a step-by-step 'Watch Video' button. Alternatively, you can <a href='https://www.youtube.com/results?search_query=pan+card+apply+online' target='_blank' style='color:#0f4c81; font-weight:bold;'>click here to watch the online application process</a>.";
                } else if(text.includes('kisan') || text.includes('pmkisan')) {
                    reply = "For PM-Kisan status adjustments or registrations, open the PM-Kisan card details panel or <a href='https://www.youtube.com/results?search_query=pm+kisan+yojana+payment+status+check' target='_blank' style='color:#0f4c81; font-weight:bold;'>click here to check payment status guidelines</a>.";
                } else if(text.includes('video') || text.includes('youtube') || text.includes('help')) {
                    reply = "No worries! If you're stuck, go directly to <a href='https://www.youtube.com' target='_blank' style='color:red; font-weight:bold;'>YouTube.com</a> and look up the government scheme name for live video guides.";
                }

                logs.innerHTML += '<div class="msg bot">' + reply + '</div>';
                logs.scrollTop = logs.scrollHeight;
            }, 600);
        }
    </script>
</body>
</html>
