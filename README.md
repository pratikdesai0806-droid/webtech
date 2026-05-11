This is a project for the CTA activity of my university of subject Web-development
The view and colour composition and everything about visuals and functions whuch get activated when clicked on buttons etc is given by a html code which is in
"Index.html" file 
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>MentorBridge – Portal</title>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:ital,wght@0,300;0,600;0,800;1,300&family=DM+Sans:wght@300;400;500;600&display=swap" rel="stylesheet"/>
<style>
:root{
  --coral:#e94560;--gold:#f5a623;--teal:#00b4d8;--violet:#533483;--green:#06d6a0;
  --dark:#1a1a2e;--bg:#f8f5f0;--white:#fff;--muted:#6b7280;--border:#e5e7eb;
  --shadow:0 24px 64px rgba(0,0,0,0.12);--radius:20px;--tr:0.3s cubic-bezier(.4,0,.2,1);
  --accent:#e94560;--glow:rgba(233,69,96,0.12);--sw:#e94560;
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
body{font-family:'DM Sans',sans-serif;background:var(--bg);min-height:100vh;overflow-x:hidden}

/* ── Blobs ── */
.blobs{position:fixed;inset:0;z-index:0;pointer-events:none;overflow:hidden}
.blob{position:absolute;border-radius:50%;filter:blur(80px);opacity:.15;animation:bf 12s ease-in-out infinite alternate}
.b1{width:600px;height:600px;background:#e94560;top:-200px;left:-150px}
.b2{width:500px;height:500px;background:#00b4d8;top:20%;right:-150px;animation-delay:3s}
.b3{width:400px;height:400px;background:#f5a623;bottom:-100px;left:30%;animation-delay:6s}
.b4{width:350px;height:350px;background:#533483;bottom:10%;right:10%;animation-delay:2s}
@keyframes bf{from{transform:scale(1)}to{transform:scale(1.08) translateY(-30px)}}

/* ── Brand ── */
.brand{position:fixed;top:24px;left:36px;z-index:200;display:flex;align-items:center;gap:10px}
.brand-logo{width:38px;height:38px;background:linear-gradient(135deg,var(--coral),var(--gold));border-radius:11px;display:flex;align-items:center;justify-content:center;font-size:18px;box-shadow:0 4px 15px rgba(233,69,96,.4)}
.brand-name{font-family:'Fraunces',serif;font-size:1.4rem;font-weight:800;color:var(--dark);letter-spacing:-.5px}
.brand-name span{color:var(--coral)}

/* ── Toast ── */
.toast{position:fixed;top:28px;right:28px;z-index:9999;padding:12px 20px;border-radius:14px;font-size:.85rem;font-weight:500;transform:translateY(-80px);opacity:0;transition:all .4s cubic-bezier(.34,1.56,.64,1);max-width:320px;display:flex;align-items:center;gap:8px}
.toast.s{background:var(--green);color:#fff;box-shadow:0 8px 24px rgba(6,214,160,.4)}
.toast.e{background:var(--coral);color:#fff;box-shadow:0 8px 24px rgba(233,69,96,.4)}
.toast.show{transform:translateY(0);opacity:1}

/* ── Pages ── */
.page{display:none;position:relative;z-index:1;min-height:100vh}
.page.active{display:flex}

/* ── AUTH PAGE ── */
#page-auth{align-items:center;justify-content:center;padding:40px 20px}
.auth-wrap{width:100%;max-width:860px}
.step{display:none}
.step.active{display:block;animation:si .5s cubic-bezier(.4,0,.2,1)}
@keyframes si{from{opacity:0;transform:translateY(20px) scale(.98)}to{opacity:1;transform:translateY(0) scale(1)}}

/* Role cards */
.role-section{text-align:center}
.role-headline{font-family:'Fraunces',serif;font-size:clamp(2rem,5vw,3.2rem);font-weight:800;color:var(--dark);line-height:1.1;margin-bottom:10px}
.role-headline em{color:var(--coral);font-style:italic}
.role-sub{color:var(--muted);margin-bottom:52px;font-weight:300}
.role-cards{display:grid;grid-template-columns:1fr 1fr;gap:24px;max-width:680px;margin:0 auto}
.rc{background:var(--white);border-radius:var(--radius);padding:40px 32px;cursor:pointer;border:2.5px solid transparent;box-shadow:var(--shadow);transition:var(--tr);position:relative;overflow:hidden}
.rc::before{content:'';position:absolute;inset:0;opacity:0;transition:var(--tr)}
.rc.mentor::before{background:linear-gradient(135deg,rgba(233,69,96,.06),rgba(245,166,35,.06))}
.rc.mentee::before{background:linear-gradient(135deg,rgba(0,180,216,.06),rgba(83,52,131,.06))}
.rc:hover{transform:translateY(-6px);box-shadow:0 32px 80px rgba(0,0,0,.16)}
.rc:hover::before{opacity:1}
.rc.mentor:hover{border-color:var(--coral)}
.rc.mentee:hover{border-color:var(--teal)}
.rc-icon{width:68px;height:68px;border-radius:18px;display:flex;align-items:center;justify-content:center;font-size:1.9rem;margin:0 auto 20px}
.rc.mentor .rc-icon{background:linear-gradient(135deg,#fde8ed,#fef3e2)}
.rc.mentee .rc-icon{background:linear-gradient(135deg,#e0f7ff,#ede7f6)}
.rc-title{font-family:'Fraunces',serif;font-size:1.4rem;font-weight:700;color:var(--dark);margin-bottom:8px}
.rc-desc{font-size:.88rem;color:var(--muted);line-height:1.6}
.rc-badge{display:inline-block;margin-top:18px;padding:5px 14px;border-radius:50px;font-size:.75rem;font-weight:600}
.rc.mentor .rc-badge{background:#fde8ed;color:var(--coral)}
.rc.mentee .rc-badge{background:#e0f7ff;color:#0077a8}

/* Auth container */
.auth-box{background:var(--white);border-radius:28px;box-shadow:var(--shadow);overflow:hidden;display:grid;grid-template-columns:1fr 1fr;min-height:560px}
.auth-left{padding:44px 40px;display:flex;flex-direction:column;justify-content:flex-start;overflow-y:auto;max-height:90vh}
.back-btn{display:inline-flex;align-items:center;gap:7px;color:var(--muted);font-size:.88rem;cursor:pointer;margin-bottom:28px;border:none;background:none;font-family:'DM Sans',sans-serif;transition:color .2s}
.back-btn:hover{color:var(--dark)}
.role-tag{display:inline-flex;align-items:center;gap:7px;padding:6px 14px;border-radius:50px;font-size:.8rem;font-weight:600;margin-bottom:16px;width:fit-content}
.role-tag.m{background:#fde8ed;color:var(--coral)}
.role-tag.s{background:#e0f7ff;color:#0077a8}
.auth-title{font-family:'Fraunces',serif;font-size:1.8rem;font-weight:800;color:var(--dark);margin-bottom:4px;line-height:1.2}
.auth-sub{font-size:.85rem;color:var(--muted);margin-bottom:24px}
.toggle-row{display:flex;background:#f3f4f6;border-radius:11px;padding:4px;margin-bottom:20px;width:fit-content}
.tog{padding:8px 22px;border-radius:8px;border:none;background:transparent;font-family:'DM Sans',sans-serif;font-size:.86rem;font-weight:500;cursor:pointer;color:var(--muted);transition:var(--tr)}
.tog.on{background:var(--white);color:var(--dark);box-shadow:0 2px 8px rgba(0,0,0,.1)}
.alert{padding:9px 13px;border-radius:10px;font-size:.81rem;margin-bottom:14px;display:none;align-items:center;gap:7px}
.alert.err{background:#fff0f3;border:1.5px solid #ffc0cc;color:#c0392b}
.alert.ok{background:#edfff8;border:1.5px solid #a8efd0;color:#0a6640}
.alert.show{display:flex}
.form{display:flex;flex-direction:column;gap:12px}
.row2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.field{display:flex;flex-direction:column;gap:5px}
.field label{font-size:.78rem;font-weight:500;color:#4b5563}
.field input,.field select{padding:10px 13px;border-radius:10px;border:2px solid var(--border);font-family:'DM Sans',sans-serif;font-size:.88rem;color:var(--dark);background:#fafafa;transition:border-color .2s,box-shadow .2s;outline:none;appearance:none}
.field input:focus,.field select:focus{border-color:var(--accent);box-shadow:0 0 0 4px var(--glow);background:#fff}
.field select{cursor:pointer;background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 24 24' fill='none' stroke='%236b7280' stroke-width='2'%3E%3Cpath d='M6 9l6 6 6-6'/%3E%3C/svg%3E");background-repeat:no-repeat;background-position:right 12px center;padding-right:32px}
.mentor-sel-card{margin-top:4px;padding:12px 14px;border-radius:12px;border:2px solid var(--border);background:#fafafa;cursor:pointer;transition:border-color .2s}
.mentor-sel-card:hover{border-color:var(--accent)}
.mentor-sel-card.picked{border-color:var(--teal);background:#f0fbff}
.mentor-sel-card .mc-name{font-size:.9rem;font-weight:600;color:var(--dark)}
.mentor-sel-card .mc-dept{font-size:.78rem;color:var(--muted)}
.mentor-sel-card .mc-count{font-size:.74rem;color:var(--teal);margin-top:3px}
.mentor-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px;max-height:180px;overflow-y:auto;padding-right:2px}
.btn{padding:12px 24px;border:none;border-radius:12px;font-family:'DM Sans',sans-serif;font-size:.9rem;font-weight:600;cursor:pointer;color:#fff;transition:transform .2s,box-shadow .2s,opacity .2s;letter-spacing:.2px;margin-top:6px}
.btn:hover:not(:disabled){transform:translateY(-2px)}
.btn:disabled{opacity:.6;cursor:not-allowed}
.btn.m-btn{background:linear-gradient(135deg,var(--coral),var(--gold));box-shadow:0 8px 24px rgba(233,69,96,.35)}
.btn.s-btn{background:linear-gradient(135deg,var(--teal),var(--violet));box-shadow:0 8px 24px rgba(0,180,216,.35)}
.switch-txt{font-size:.82rem;color:var(--muted);text-align:center;margin-top:6px}
.switch-txt a{color:var(--sw);cursor:pointer;font-weight:500}
.spinner{display:inline-block;width:14px;height:14px;border:2px solid rgba(255,255,255,.4);border-top-color:#fff;border-radius:50%;animation:spin .6s linear infinite;margin-right:6px;vertical-align:middle}
@keyframes spin{to{transform:rotate(360deg)}}

/* Right panel */
.auth-right{border-radius:0 28px 28px 0;padding:48px 36px;display:flex;flex-direction:column;justify-content:center;position:relative;overflow:hidden}
.auth-right.mr{background:linear-gradient(150deg,#1a1a2e,#2d1b3d,#3d0d20)}
.auth-right.sr{background:linear-gradient(150deg,#0f3460,#16213e,#0a1628)}
.rdc{position:absolute;inset:0;pointer-events:none;overflow:hidden}
.rdc div{position:absolute;border-radius:50%;opacity:.12}
.mr .rdc div:nth-child(1){width:280px;height:280px;background:var(--coral);top:-60px;right:-60px}
.mr .rdc div:nth-child(2){width:180px;height:180px;background:var(--gold);bottom:40px;left:-30px}
.sr .rdc div:nth-child(1){width:280px;height:280px;background:var(--teal);top:-60px;right:-60px}
.sr .rdc div:nth-child(2){width:180px;height:180px;background:var(--green);bottom:40px;left:-30px}
.rq{font-family:'Fraunces',serif;font-style:italic;font-size:1.35rem;font-weight:300;color:rgba(255,255,255,.9);line-height:1.4;margin-bottom:28px;position:relative;z-index:1}
.rq strong{font-style:normal;font-weight:700}
.feats{position:relative;z-index:1;display:flex;flex-direction:column;gap:14px}
.feat{display:flex;align-items:flex-start;gap:12px}
.feat-dot{width:30px;height:30px;border-radius:9px;flex-shrink:0;display:flex;align-items:center;justify-content:center;font-size:13px}
.mr .feat-dot{background:rgba(233,69,96,.25)}
.sr .feat-dot{background:rgba(0,180,216,.25)}
.feat strong{display:block;font-size:.84rem;font-weight:600;color:rgba(255,255,255,.9)}
.feat span{font-size:.77rem;color:rgba(255,255,255,.5)}

/* ══════════════════════════════════════════════
   DASHBOARD PAGE
══════════════════════════════════════════════ */
#page-dash{flex-direction:column;background:var(--bg)}

/* Topbar */
.topbar{background:var(--white);border-bottom:1px solid var(--border);padding:0 32px;height:64px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:100;box-shadow:0 1px 12px rgba(0,0,0,.06)}
.topbar-brand{display:flex;align-items:center;gap:10px}
.topbar-logo{width:34px;height:34px;border-radius:10px;background:linear-gradient(135deg,var(--coral),var(--gold));display:flex;align-items:center;justify-content:center;font-size:16px}
.topbar-name{font-family:'Fraunces',serif;font-size:1.2rem;font-weight:800;color:var(--dark)}
.topbar-name span{color:var(--coral)}
.topbar-right{display:flex;align-items:center;gap:14px}
.user-pill{display:flex;align-items:center;gap:9px;padding:6px 14px;border-radius:50px;font-size:.84rem;font-weight:500;color:var(--dark)}
.user-pill.m{background:#fde8ed}
.user-pill.s{background:#e0f7ff}
.avatar{width:30px;height:30px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:.78rem;font-weight:700;color:#fff;flex-shrink:0}
.avatar.m{background:linear-gradient(135deg,var(--coral),var(--gold))}
.avatar.s{background:linear-gradient(135deg,var(--teal),var(--violet))}
.logout-btn{padding:7px 16px;border-radius:10px;border:1.5px solid var(--border);background:transparent;font-family:'DM Sans',sans-serif;font-size:.82rem;cursor:pointer;color:var(--muted);transition:all .2s}
.logout-btn:hover{border-color:var(--coral);color:var(--coral)}

/* Dash content */
.dash-content{padding:32px;max-width:1200px;margin:0 auto;width:100%}
.dash-greeting{margin-bottom:28px}
.dash-greeting h1{font-family:'Fraunces',serif;font-size:2rem;font-weight:800;color:var(--dark);margin-bottom:4px}
.dash-greeting p{color:var(--muted);font-size:.95rem}

/* Stats row */
.stats-row{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:16px;margin-bottom:32px}
.stat-card{background:var(--white);border-radius:16px;padding:20px 22px;box-shadow:0 2px 16px rgba(0,0,0,.06);border:1px solid var(--border)}
.stat-label{font-size:.78rem;color:var(--muted);font-weight:500;margin-bottom:8px;text-transform:uppercase;letter-spacing:.5px}
.stat-val{font-family:'Fraunces',serif;font-size:2rem;font-weight:800;color:var(--dark);line-height:1}
.stat-sub{font-size:.76rem;color:var(--muted);margin-top:4px}

/* Section */
.section{background:var(--white);border-radius:20px;padding:24px 26px;box-shadow:0 2px 16px rgba(0,0,0,.06);border:1px solid var(--border);margin-bottom:24px}
.section-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:20px}
.section-title{font-family:'Fraunces',serif;font-size:1.2rem;font-weight:700;color:var(--dark)}
.section-badge{padding:4px 12px;border-radius:50px;font-size:.76rem;font-weight:600}
.badge-coral{background:#fde8ed;color:var(--coral)}
.badge-teal{background:#e0f7ff;color:#0077a8}
.badge-violet{background:#ede7f6;color:var(--violet)}

/* Mentor info card */
.mentor-info-card{display:flex;align-items:center;gap:20px;padding:20px;border-radius:16px;border:2px solid var(--teal);background:linear-gradient(135deg,#f0fbff,#f8f4ff)}
.mi-avatar{width:60px;height:60px;border-radius:16px;background:linear-gradient(135deg,var(--teal),var(--violet));display:flex;align-items:center;justify-content:center;font-size:1.4rem;color:#fff;font-weight:700;flex-shrink:0}
.mi-name{font-size:1.1rem;font-weight:700;color:var(--dark);margin-bottom:3px}
.mi-dept{font-size:.85rem;color:var(--muted)}
.mi-email{font-size:.82rem;color:var(--teal);margin-top:4px}
.no-mentor{text-align:center;padding:32px;color:var(--muted)}
.no-mentor .nm-icon{font-size:2.5rem;margin-bottom:12px}
.no-mentor p{font-size:.9rem;margin-bottom:16px}

/* Mentee table */
.mentee-table{width:100%;border-collapse:collapse}
.mentee-table th{text-align:left;padding:10px 14px;font-size:.76rem;font-weight:600;color:var(--muted);text-transform:uppercase;letter-spacing:.5px;border-bottom:2px solid var(--border)}
.mentee-table td{padding:13px 14px;border-bottom:1px solid #f3f4f6;font-size:.88rem;color:var(--dark)}
.mentee-table tr:last-child td{border-bottom:none}
.mentee-table tr:hover td{background:#fafafa}
.td-name{font-weight:600}
.td-roll{font-size:.8rem;color:var(--muted)}
.online-dot{width:8px;height:8px;border-radius:50%;display:inline-block;margin-right:5px}
.dot-green{background:var(--green)}
.dot-grey{background:#d1d5db}
.empty-state{text-align:center;padding:40px;color:var(--muted)}
.empty-icon{font-size:2.5rem;margin-bottom:10px}

/* Mentor selection grid (in dashboard) */
.mentor-select-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(220px,1fr));gap:14px}
.msc{background:var(--white);border:2px solid var(--border);border-radius:16px;padding:18px;cursor:pointer;transition:var(--tr)}
.msc:hover{border-color:var(--teal);transform:translateY(-3px);box-shadow:0 8px 24px rgba(0,0,0,.1)}
.msc.selected{border-color:var(--teal);background:linear-gradient(135deg,#f0fbff,#f8f4ff)}
.msc-avatar{width:44px;height:44px;border-radius:12px;background:linear-gradient(135deg,var(--teal),var(--violet));display:flex;align-items:center;justify-content:center;color:#fff;font-weight:700;font-size:.9rem;margin-bottom:12px}
.msc-name{font-size:.92rem;font-weight:700;color:var(--dark);margin-bottom:2px}
.msc-dept{font-size:.78rem;color:var(--muted)}
.msc-count{font-size:.75rem;color:var(--teal);margin-top:6px;font-weight:500}
.select-confirm-btn{margin-top:20px;padding:11px 28px;border-radius:12px;border:none;background:linear-gradient(135deg,var(--teal),var(--violet));color:#fff;font-family:'DM Sans',sans-serif;font-weight:600;font-size:.9rem;cursor:pointer;transition:transform .2s,opacity .2s;display:none}
.select-confirm-btn:hover{transform:translateY(-2px)}
.select-confirm-btn.show{display:inline-block}

/* Loading overlay */
.loading{display:none;position:fixed;inset:0;background:rgba(248,245,240,.85);z-index:500;align-items:center;justify-content:center;flex-direction:column;gap:16px}
.loading.show{display:flex}
.loading-ring{width:48px;height:48px;border:4px solid var(--border);border-top-color:var(--coral);border-radius:50%;animation:spin .8s linear infinite}
.loading-txt{font-size:.9rem;color:var(--muted)}

@media(max-width:700px){
  .auth-right{display:none}
  .auth-box{grid-template-columns:1fr}
  .auth-left{padding:32px 24px}
  .role-cards,.row2,.mentor-grid{grid-template-columns:1fr}
  .brand{left:16px}
  .dash-content{padding:16px}
  .topbar{padding:0 16px}
  .stats-row{grid-template-columns:1fr 1fr}
  .mentor-select-grid{grid-template-columns:1fr 1fr}
}
</style>
</head>
<body>

<div class="blobs">
  <div class="blob b1"></div><div class="blob b2"></div>
  <div class="blob b3"></div><div class="blob b4"></div>
</div>

<div class="brand" id="top-brand">
  <div class="brand-logo">🎓</div>
  <div class="brand-name">Mentor<span>Bridge</span></div>
</div>

<div class="toast" id="toast"></div>

<div class="loading" id="loading">
  <div class="loading-ring"></div>
  <div class="loading-txt">Loading…</div>
</div>

<!-- ══════════════ AUTH PAGE ══════════════ -->
<div class="page active" id="page-auth">
<div class="auth-wrap">

  <!-- Step 1: Role -->
  <div class="step active" id="step-role">
    <div class="role-section">
      <h1 class="role-headline">Who are you <em>today?</em></h1>
      <p class="role-sub">Select your role to continue to your personalised portal</p>
      <div class="role-cards">
        <div class="rc mentor" onclick="selectRole('mentor')">
          <div class="rc-icon">🧑‍🏫</div>
          <div class="rc-title">I'm a Mentor</div>
          <p class="rc-desc">Faculty guiding students through academic milestones and personal development goals.</p>
          <span class="rc-badge">Faculty / Professor</span>
        </div>
        <div class="rc mentee" onclick="selectRole('mentee')">
          <div class="rc-icon">🎒</div>
          <div class="rc-title">I'm a Mentee</div>
          <p class="rc-desc">A student seeking structured guidance, tracking progress with faculty support.</p>
          <span class="rc-badge">Student</span>
        </div>
      </div>
    </div>
  </div>

  <!-- Step 2: Login/Signup -->
  <div class="step" id="step-auth">
    <div class="auth-box">
      <div class="auth-left">
        <button class="back-btn" onclick="goBack()">
          <svg width="15" height="15" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M15 18l-6-6 6-6"/></svg>
          Back
        </button>
        <div class="role-tag m" id="role-tag">🧑‍🏫 Mentor</div>
        <div class="auth-title" id="auth-title">Welcome back</div>
        <div class="auth-sub" id="auth-sub">Sign in to manage your mentee cohort</div>
        <div class="toggle-row">
          <button class="tog on" id="tog-login" onclick="switchMode('login')">Login</button>
          <button class="tog" id="tog-signup" onclick="switchMode('signup')">Sign Up</button>
        </div>
        <div class="alert err" id="err-box">⚠ <span id="err-msg"></span></div>
        <div class="alert ok"  id="ok-box">✓ <span id="ok-msg"></span></div>

        <!-- LOGIN FORM -->
        <div id="frm-login">
          <div class="form">
            <div class="field"><label>Institutional Email</label><input type="email" id="l-email" placeholder="you@institution.edu"/></div>
            <div class="field"><label>Password</label><input type="password" id="l-pass" placeholder="Your password"/></div>
            <button class="btn m-btn" id="login-btn" onclick="doLogin()">Sign In →</button>
            <div class="switch-txt">No account? <a onclick="switchMode('signup')">Create one</a></div>
          </div>
        </div>

        <!-- SIGNUP FORM -->
        <div id="frm-signup" style="display:none">
          <div class="form">
            <div class="row2">
              <div class="field"><label>First Name</label><input type="text" id="s-fn" placeholder="Anya"/></div>
              <div class="field"><label>Last Name</label><input type="text" id="s-ln" placeholder="Sharma"/></div>
            </div>
            <div class="field"><label>Institutional Email</label><input type="email" id="s-email" placeholder="you@institution.edu"/></div>
            <div class="field"><label>Department</label><input type="text" id="s-dept" placeholder="Computer Science"/></div>
            <div class="field"><label id="s-id-lbl">Employee ID</label><input type="text" id="s-id" placeholder="EMP-XXXXXX"/></div>
            <div class="row2">
              <div class="field"><label>Password</label><input type="password" id="s-pass" placeholder="Min 8 chars"/></div>
              <div class="field"><label>Confirm Password</label><input type="password" id="s-conf" placeholder="Repeat"/></div>
            </div>
            <!-- Mentor selection (mentee only) -->
            <div id="mentor-pick-wrap" style="display:none">
              <div class="field">
                <label>Choose Your Mentor <span style="color:var(--muted);font-weight:400">(optional)</span></label>
                <div class="mentor-grid" id="mentor-pick-grid">
                  <div style="color:var(--muted);font-size:.82rem;padding:8px">Loading mentors…</div>
                </div>
              </div>
            </div>
            <button class="btn m-btn" id="signup-btn" onclick="doSignup()">Create Account →</button>
            <div class="switch-txt">Have an account? <a onclick="switchMode('login')">Sign in</a></div>
          </div>
        </div>
      </div>

      <div class="auth-right mr" id="auth-right">
        <div class="rdc"><div></div><div></div></div>
        <p class="rq" id="rq">"<strong>Great mentors</strong> don't give answers — they reveal pathways."</p>
        <div class="feats">
          <div class="feat"><div class="feat-dot">📋</div><div><strong>Meeting Records</strong><span>Log every session with structured notes</span></div></div>
          <div class="feat"><div class="feat-dot">📈</div><div><strong>Progress Tracking</strong><span>Monitor academic & personal growth</span></div></div>
          <div class="feat"><div class="feat-dot">🎯</div><div><strong>Goal Management</strong><span>Set and review development goals</span></div></div>
          <div class="feat"><div class="feat-dot">🗂️</div><div><strong>Action Plans</strong><span>Track structured improvement plans</span></div></div>
        </div>
      </div>
    </div>
  </div>

</div>
</div>

<!-- ══════════════ DASHBOARD PAGE ══════════════ -->
<div class="page" id="page-dash">

  <div class="topbar">
    <div class="topbar-brand">
      <div class="topbar-logo">🎓</div>
      <div class="topbar-name">Mentor<span>Bridge</span></div>
    </div>
    <div class="topbar-right">
      <div class="user-pill m" id="user-pill">
        <div class="avatar m" id="user-avatar">?</div>
        <span id="user-name-pill">User</span>
      </div>
      <button class="logout-btn" onclick="doLogout()">Sign Out</button>
    </div>
  </div>

  <div class="dash-content">
    <div class="dash-greeting">
      <h1 id="dash-greeting-h">Welcome back! 👋</h1>
      <p id="dash-greeting-p">Here's your mentorship overview</p>
    </div>

    <!-- Stats -->
    <div class="stats-row" id="stats-row"></div>

    <!-- MENTOR DASHBOARD -->
    <div id="mentor-dash" style="display:none">
      <div class="section">
        <div class="section-header">
          <div class="section-title">My Mentees</div>
          <span class="section-badge badge-coral" id="mentee-count-badge">0 students</span>
        </div>
        <div id="mentee-table-wrap"></div>
      </div>
    </div>

    <!-- MENTEE DASHBOARD -->
    <div id="mentee-dash" style="display:none">
      <div class="section">
        <div class="section-header">
          <div class="section-title">My Mentor</div>
          <span class="section-badge badge-teal" id="mentor-status-badge">–</span>
        </div>
        <div id="my-mentor-wrap"></div>
      </div>

      <div class="section">
        <div class="section-header">
          <div class="section-title">Browse & Select a Mentor</div>
          <span class="section-badge badge-violet">All Faculty</span>
        </div>
        <div class="mentor-select-grid" id="all-mentors-grid"></div>
        <button class="select-confirm-btn" id="confirm-mentor-btn" onclick="confirmMentorSelection()">
          ✓ Confirm Selection
        </button>
      </div>
    </div>

  </div>
</div>

<script>
// ══════════════════════════════════════════════
// CONFIG
// ══════════════════════════════════════════════
const API = 'api';

// ══════════════════════════════════════════════
// STATE
// ══════════════════════════════════════════════
let currentRole = 'mentor';
let currentMode = 'login';
let currentUser = null;
let selectedMentorId = null;
let pickedMentorInSignup = null;

// ══════════════════════════════════════════════
// UTILITIES
// ══════════════════════════════════════════════
function toast(msg, type='s'){
  const t=document.getElementById('toast');
  t.textContent=msg; t.className=`toast ${type} show`;
  setTimeout(()=>t.classList.remove('show'),3800);
}
function showErr(msg){ const e=document.getElementById('err-box'); document.getElementById('err-msg').textContent=msg; e.classList.add('show'); document.getElementById('ok-box').classList.remove('show'); }
function showOk(msg){  const e=document.getElementById('ok-box');  document.getElementById('ok-msg').textContent=msg;  e.classList.add('show'); document.getElementById('err-box').classList.remove('show'); }
function clearAlerts(){ document.getElementById('err-box').classList.remove('show'); document.getElementById('ok-box').classList.remove('show'); }
function setLoading(id,on){
  const b=document.getElementById(id);
  b.disabled=on;
  const orig={'login-btn':'Sign In →','signup-btn':'Create Account →'};
  b.innerHTML=on?'<span class="spinner"></span> Please wait…':orig[id];
}
function loading(on){ document.getElementById('loading').classList.toggle('show',on); }
async function api(endpoint, method='GET', body=null){
  const opts={method,headers:{'Content-Type':'application/json'}};
  if(body) opts.body=JSON.stringify(body);
  const r=await fetch(`${API}/${endpoint}`,opts);
  return r.json();
}
function initials(name){ return name.split(' ').map(w=>w[0]).join('').toUpperCase().slice(0,2); }
function formatDate(d){ if(!d) return 'Never'; return new Date(d).toLocaleDateString('en-IN',{day:'numeric',month:'short',year:'numeric'}); }

// ══════════════════════════════════════════════
// AUTH NAVIGATION
// ══════════════════════════════════════════════
function selectRole(role){
  currentRole=role;
  applyRole();
  document.getElementById('step-role').classList.remove('active');
  document.getElementById('step-auth').classList.add('active');
  if(role==='mentee' && currentMode==='signup') loadMentorsForSignup();
}
function goBack(){
  document.getElementById('step-auth').classList.remove('active');
  document.getElementById('step-role').classList.add('active');
  clearAlerts(); switchMode('login');
}
function switchMode(mode){
  currentMode=mode;
  const isL=mode==='login';
  document.getElementById('tog-login').className='tog'+(isL?' on':'');
  document.getElementById('tog-signup').className='tog'+(!isL?' on':'');
  document.getElementById('frm-login').style.display=isL?'block':'none';
  document.getElementById('frm-signup').style.display=!isL?'block':'none';
  document.getElementById('mentor-pick-wrap').style.display=(!isL && currentRole==='mentee')?'block':'none';
  if(!isL && currentRole==='mentee') loadMentorsForSignup();
  clearAlerts(); applyRole();
}
function applyRole(){
  const isM=currentRole==='mentor'; const isL=currentMode==='login';
  const tag=document.getElementById('role-tag');
  tag.textContent=isM?'🧑‍🏫 Mentor':'🎒 Student';
  tag.className='role-tag '+(isM?'m':'s');
  document.getElementById('auth-right').className='auth-right '+(isM?'mr':'sr');
  document.getElementById('s-id-lbl').textContent=isM?'Employee ID':'Student Roll No.';
  document.getElementById('s-id').placeholder=isM?'EMP-XXXXXX':'ROLL-XXXXXX';
  document.getElementById('rq').innerHTML=isM
    ? '"<strong>Great mentors</strong> don\'t give answers — they reveal pathways."'
    : '"<strong>The secret</strong> of getting ahead is getting started — with the right guide."';
  document.getElementById('auth-title').textContent=isL?'Welcome back':(isM?'Join as Faculty':'Join as Student');
  document.getElementById('auth-sub').textContent=isL
    ? (isM?'Sign in to manage your mentee cohort':'Sign in to track your mentorship journey')
    : (isM?'Create your mentor account to get started':'Register and select your assigned mentor');
  const bClass=isM?'btn m-btn':'btn s-btn';
  document.getElementById('login-btn').className=bClass;
  document.getElementById('signup-btn').className=bClass;
  document.documentElement.style.setProperty('--accent',isM?'#e94560':'#00b4d8');
  document.documentElement.style.setProperty('--glow',isM?'rgba(233,69,96,0.12)':'rgba(0,180,216,0.12)');
  document.documentElement.style.setProperty('--sw',isM?'#e94560':'#00b4d8');
}

// ══════════════════════════════════════════════
// MENTOR PICKER (signup)
// ══════════════════════════════════════════════
async function loadMentorsForSignup(){
  const grid=document.getElementById('mentor-pick-grid');
  grid.innerHTML='<div style="color:var(--muted);font-size:.82rem;padding:8px">Loading…</div>';
  try{
    const data=await api('get_mentors.php');
    if(!data.success || !data.mentors.length){
      grid.innerHTML='<div style="color:var(--muted);font-size:.82rem;padding:8px">No mentors registered yet.</div>';
      return;
    }
    grid.innerHTML=data.mentors.map(m=>`
      <div class="mentor-sel-card" id="mpick-${m.id}" onclick="pickMentor(${m.id})">
        <div class="mc-name">Dr. ${m.first_name} ${m.last_name}</div>
        <div class="mc-dept">${m.department}</div>
        <div class="mc-count">${m.mentee_count} mentee${m.mentee_count!=1?'s':''}</div>
      </div>`).join('');
  }catch(e){ grid.innerHTML='<div style="color:var(--muted);font-size:.82rem;padding:8px">Could not load mentors.</div>'; }
}
function pickMentor(id){
  pickedMentorInSignup=id;
  document.querySelectorAll('.mentor-sel-card').forEach(c=>c.classList.remove('picked'));
  const el=document.getElementById('mpick-'+id);
  if(el) el.classList.add('picked');
}

// ══════════════════════════════════════════════
// LOGIN
// ══════════════════════════════════════════════
async function doLogin(){
  clearAlerts();
  const email=document.getElementById('l-email').value.trim();
  const pass=document.getElementById('l-pass').value;
  if(!email||!pass){showErr('Please fill in all fields.');return;}
  setLoading('login-btn',true);
  try{
    const data=await api('login.php','POST',{role:currentRole,email,password:pass});
    if(data.success){
      currentUser=data.user;
      sessionStorage.setItem('mb_user',JSON.stringify(currentUser));
      toast(`👋 Welcome back, ${currentUser.first_name||currentUser.name}!`);
      showDashboard();
    } else { showErr(data.message||'Login failed.'); }
  }catch(e){ showErr('Server unreachable. Check your connection.'); }
  finally{ setLoading('login-btn',false); }
}

// ══════════════════════════════════════════════
// SIGNUP
// ══════════════════════════════════════════════
async function doSignup(){
  clearAlerts();
  const fn=document.getElementById('s-fn').value.trim();
  const ln=document.getElementById('s-ln').value.trim();
  const email=document.getElementById('s-email').value.trim();
  const dept=document.getElementById('s-dept').value.trim();
  const id=document.getElementById('s-id').value.trim();
  const pass=document.getElementById('s-pass').value;
  const conf=document.getElementById('s-conf').value;
  if(!fn||!ln||!email||!dept||!id||!pass||!conf){showErr('Please fill in all fields.');return;}
  if(pass.length<8){showErr('Password must be at least 8 characters.');return;}
  if(pass!==conf){showErr('Passwords do not match.');return;}
  setLoading('signup-btn',true);
  try{
    const payload={role:currentRole,first_name:fn,last_name:ln,email,department:dept,id_number:id,password:pass,confirm_password:conf};
    if(currentRole==='mentee' && pickedMentorInSignup) payload.mentor_id=pickedMentorInSignup;
    const data=await api('signup.php','POST',payload);
    if(data.success){
      toast('🎉 Account created! Please sign in.');
      showOk('Account created successfully! You can now sign in.');
      ['s-fn','s-ln','s-email','s-dept','s-id','s-pass','s-conf'].forEach(x=>document.getElementById(x).value='');
      pickedMentorInSignup=null;
      setTimeout(()=>switchMode('login'),1800);
    } else { showErr(data.message||'Signup failed.'); }
  }catch(e){ showErr('Server unreachable.'); }
  finally{ setLoading('signup-btn',false); }
}

// ══════════════════════════════════════════════
// DASHBOARD
// ══════════════════════════════════════════════
function showDashboard(){
  document.getElementById('page-auth').classList.remove('active');
  document.getElementById('page-dash').classList.add('active');
  document.getElementById('top-brand').style.display='none';
  document.getElementById('blobs')?.remove();
  loadDashboard();
}

async function loadDashboard(){
  loading(true);
  const u=currentUser;
  // Topbar
  const pill=document.getElementById('user-pill');
  pill.className='user-pill '+(u.role==='mentor'?'m':'s');
  document.getElementById('user-avatar').className='avatar '+(u.role==='mentor'?'m':'s');
  document.getElementById('user-avatar').textContent=initials(u.name);
  document.getElementById('user-name-pill').textContent=u.name;
  document.getElementById('dash-greeting-h').textContent=`Welcome, ${u.first_name||u.name.split(' ')[0]}! 👋`;
  document.getElementById('dash-greeting-p').textContent=u.role==='mentor'
    ? 'Here\'s your mentee cohort overview'
    : 'Here\'s your mentorship dashboard';

  try{
    const data=await api(`dashboard.php?role=${u.role}&id=${u.id}`);
    if(!data.success){ loading(false); return; }

    if(u.role==='mentor') renderMentorDash(data);
    else renderMenteeDash(data);
  }catch(e){ toast('Failed to load dashboard.','e'); }
  loading(false);
}

// ── MENTOR DASHBOARD ──
function renderMentorDash(data){
  const {mentor, mentees, stats} = data;
  document.getElementById('mentor-dash').style.display='block';
  document.getElementById('mentee-dash').style.display='none';

  // Stats
  document.getElementById('stats-row').innerHTML=`
    <div class="stat-card">
      <div class="stat-label">Total Mentees</div>
      <div class="stat-val">${stats.total_mentees}</div>
      <div class="stat-sub">Students under your guidance</div>
    </div>
    <div class="stat-card">
      <div class="stat-label">Active Mentees</div>
      <div class="stat-val">${stats.active_mentees}</div>
      <div class="stat-sub">Logged in at least once</div>
    </div>
    <div class="stat-card">
      <div class="stat-label">Department</div>
      <div class="stat-val" style="font-size:1.1rem;margin-top:4px">${mentor.department}</div>
      <div class="stat-sub">Employee ID: ${mentor.employee_id}</div>
    </div>
    <div class="stat-card">
      <div class="stat-label">Member Since</div>
      <div class="stat-val" style="font-size:1rem;margin-top:4px">${formatDate(mentor.created_at)}</div>
      <div class="stat-sub">Last login: ${formatDate(mentor.last_login)}</div>
    </div>`;

  // Mentee count badge
  document.getElementById('mentee-count-badge').textContent=`${mentees.length} student${mentees.length!=1?'s':''}`;

  // Mentee table
  const wrap=document.getElementById('mentee-table-wrap');
  if(!mentees.length){
    wrap.innerHTML=`<div class="empty-state"><div class="empty-icon">👥</div><p>No mentees assigned yet.<br><span style="font-size:.82rem">Students will appear here once they select you as their mentor.</span></p></div>`;
    return;
  }
  wrap.innerHTML=`<table class="mentee-table">
    <thead><tr>
      <th>Student</th><th>Roll No.</th><th>Department</th><th>Joined</th><th>Last Active</th>
    </tr></thead>
    <tbody>${mentees.map(m=>`
      <tr>
        <td>
          <div style="display:flex;align-items:center;gap:10px">
            <div class="avatar s" style="width:34px;height:34px;font-size:.76rem;border-radius:9px;flex-shrink:0">${initials(m.first_name+' '+m.last_name)}</div>
            <div>
              <div class="td-name">${m.first_name} ${m.last_name}</div>
              <div style="font-size:.76rem;color:var(--muted)">${m.email}</div>
            </div>
          </div>
        </td>
        <td class="td-roll">${m.roll_number}</td>
        <td>${m.department}</td>
        <td style="font-size:.82rem;color:var(--muted)">${formatDate(m.created_at)}</td>
        <td><span class="online-dot ${m.last_login?'dot-green':'dot-grey'}"></span>${formatDate(m.last_login)}</td>
      </tr>`).join('')}
    </tbody>
  </table>`;
}

// ── MENTEE DASHBOARD ──
function renderMenteeDash(data){
  const {mentee, mentor, all_mentors} = data;
  document.getElementById('mentee-dash').style.display='block';
  document.getElementById('mentor-dash').style.display='none';

  // Stats
  document.getElementById('stats-row').innerHTML=`
    <div class="stat-card">
      <div class="stat-label">My Mentor</div>
      <div class="stat-val" style="font-size:1rem;margin-top:4px">${mentor ? mentor.first_name+' '+mentor.last_name : 'Not assigned'}</div>
      <div class="stat-sub">${mentor ? mentor.department : 'Select a mentor below'}</div>
    </div>
    <div class="stat-card">
      <div class="stat-label">Roll Number</div>
      <div class="stat-val" style="font-size:1.1rem;margin-top:4px">${mentee.roll_number}</div>
      <div class="stat-sub">${mentee.department}</div>
    </div>
    <div class="stat-card">
      <div class="stat-label">Member Since</div>
      <div class="stat-val" style="font-size:1rem;margin-top:4px">${formatDate(mentee.created_at)}</div>
      <div class="stat-sub">Last login: ${formatDate(mentee.last_login)}</div>
    </div>
    <div class="stat-card">
      <div class="stat-label">Available Mentors</div>
      <div class="stat-val">${all_mentors.length}</div>
      <div class="stat-sub">Faculty available to guide you</div>
    </div>`;

  // My mentor section
  const mWrap=document.getElementById('my-mentor-wrap');
  const mBadge=document.getElementById('mentor-status-badge');
  if(mentor){
    mBadge.textContent='Assigned'; mBadge.className='section-badge badge-teal';
    mWrap.innerHTML=`
      <div class="mentor-info-card">
        <div class="mi-avatar">${initials(mentor.first_name+' '+mentor.last_name)}</div>
        <div>
          <div class="mi-name">Dr. ${mentor.first_name} ${mentor.last_name}</div>
          <div class="mi-dept">${mentor.department} &nbsp;·&nbsp; ${mentor.employee_id}</div>
          <div class="mi-email">${mentor.email}</div>
        </div>
      </div>
      <p style="margin-top:14px;font-size:.84rem;color:var(--muted)">You can change your mentor by selecting a different one from the list below and clicking Confirm.</p>`;
  } else {
    mBadge.textContent='Not assigned'; mBadge.className='section-badge badge-coral';
    mWrap.innerHTML=`<div class="no-mentor"><div class="nm-icon">🔍</div><p>You haven't selected a mentor yet.<br>Browse the faculty list below and choose one.</p></div>`;
  }

  // All mentors grid
  selectedMentorId = mentor ? mentor.id : null;
  const grid=document.getElementById('all-mentors-grid');
  if(!all_mentors.length){
    grid.innerHTML='<p style="color:var(--muted);font-size:.88rem">No mentors registered yet.</p>';
    return;
  }
  grid.innerHTML=all_mentors.map(m=>`
    <div class="msc ${selectedMentorId===m.id?'selected':''}" id="msc-${m.id}" onclick="pickDashMentor(${m.id})">
      <div class="msc-avatar">${initials(m.first_name+' '+m.last_name)}</div>
      <div class="msc-name">Dr. ${m.first_name} ${m.last_name}</div>
      <div class="msc-dept">${m.department}</div>
      <div class="msc-count">👥 ${m.mentee_count} mentee${m.mentee_count!=1?'s':''}</div>
    </div>`).join('');
}

function pickDashMentor(id){
  selectedMentorId=id;
  document.querySelectorAll('.msc').forEach(c=>c.classList.remove('selected'));
  const el=document.getElementById('msc-'+id);
  if(el) el.classList.add('selected');
  const btn=document.getElementById('confirm-mentor-btn');
  btn.classList.add('show');
}

async function confirmMentorSelection(){
  if(!selectedMentorId||!currentUser) return;
  const btn=document.getElementById('confirm-mentor-btn');
  btn.disabled=true; btn.textContent='Saving…';
  try{
    const data=await api('select_mentor.php','POST',{mentee_id:currentUser.id,mentor_id:selectedMentorId});
    if(data.success){
      toast('✅ Mentor assigned successfully!');
      currentUser.mentor_id=selectedMentorId;
      sessionStorage.setItem('mb_user',JSON.stringify(currentUser));
      setTimeout(()=>loadDashboard(),800);
    } else { toast(data.message||'Failed to assign mentor.','e'); }
  }catch(e){ toast('Server error.','e'); }
  btn.disabled=false; btn.textContent='✓ Confirm Selection';
}

function doLogout(){
  sessionStorage.removeItem('mb_user');
  currentUser=null;
  document.getElementById('page-dash').classList.remove('active');
  document.getElementById('page-auth').classList.add('active');
  document.getElementById('top-brand').style.display='flex';
  document.getElementById('step-auth').classList.remove('active');
  document.getElementById('step-role').classList.add('active');
  switchMode('login');
  toast('Signed out successfully.');
}

// ══════════════════════════════════════════════
// ENTER KEY + AUTO-LOGIN FROM SESSION
// ══════════════════════════════════════════════
document.addEventListener('keydown',e=>{
  if(e.key==='Enter'){
    if(document.getElementById('page-auth').classList.contains('active')){
      if(currentMode==='login') doLogin();
      else doSignup();
    }
  }
});

// Restore session on refresh
const saved=sessionStorage.getItem('mb_user');
if(saved){ try{ currentUser=JSON.parse(saved); showDashboard(); }catch(e){ sessionStorage.removeItem('mb_user'); } }
</script>
</body>
</html>

The database part of website is handled be many php codes like
Login.php
<?php
require_once __DIR__ . '/../config/db.php';
require_once __DIR__ . '/../includes/helpers.php';
corsHeaders();
if ($_SERVER['REQUEST_METHOD'] !== 'POST') jsonResponse(false, 'POST only.');

$body     = json_decode(file_get_contents('php://input'), true);
$role     = clean($body['role']     ?? '');
$email    = strtolower(clean($body['email'] ?? ''));
$password = $body['password'] ?? '';

if (!in_array($role, ['mentor','mentee'], true)) jsonResponse(false, 'Invalid role.');
if (!validEmail($email))  jsonResponse(false, 'Invalid email.');
if (empty($password))     jsonResponse(false, 'Password required.');

$db    = getDB();
$table = $role === 'mentor' ? 'mentors' : 'mentees';
$stmt  = $db->prepare("SELECT * FROM {$table} WHERE email=:e AND is_active=1 LIMIT 1");
$stmt->execute([':e' => $email]);
$user  = $stmt->fetch();

if (!$user || !password_verify($password, $user['password_hash'])) {
    if ($user) logLoginAttempt($db, $role, $user['id'], 'failed');
    jsonResponse(false, 'Invalid email or password.');
}

logLoginAttempt($db, $role, $user['id'], 'success');
touchLastLogin($db, $table, $user['id']);

$safeUser = [
    'id'         => $user['id'],
    'role'       => $role,
    'name'       => $user['first_name'] . ' ' . $user['last_name'],
    'first_name' => $user['first_name'],
    'email'      => $user['email'],
    'department' => $user['department'],
];
if ($role === 'mentor') {
    $safeUser['employee_id'] = $user['employee_id'];
} else {
    $safeUser['roll_number'] = $user['roll_number'];
    $safeUser['mentor_id']   = $user['mentor_id'];
}

jsonResponse(true, 'Login successful!', ['user' => $safeUser]);

Signup.php
<?php
require_once __DIR__ . '/../config/db.php';
require_once __DIR__ . '/../includes/helpers.php';
corsHeaders();
if ($_SERVER['REQUEST_METHOD'] !== 'POST') jsonResponse(false, 'POST only.');

$body = json_decode(file_get_contents('php://input'), true);
if (!$body) jsonResponse(false, 'Invalid JSON.');

$role            = clean($body['role']             ?? '');
$firstName       = clean($body['first_name']       ?? '');
$lastName        = clean($body['last_name']        ?? '');
$email           = strtolower(clean($body['email'] ?? ''));
$department      = clean($body['department']       ?? '');
$idNumber        = clean($body['id_number']        ?? '');
$password        = $body['password']               ?? '';
$confirmPassword = $body['confirm_password']       ?? '';
$mentorId        = isset($body['mentor_id']) ? (int)$body['mentor_id'] : null;

if (!in_array($role, ['mentor','mentee'], true)) jsonResponse(false, 'Invalid role.');
if (empty($firstName) || empty($lastName))        jsonResponse(false, 'Name is required.');
if (!validEmail($email))                           jsonResponse(false, 'Invalid email.');
if (empty($department))                            jsonResponse(false, 'Department is required.');
if (empty($idNumber))                              jsonResponse(false, 'ID number is required.');
if (strlen($password) < 8)                        jsonResponse(false, 'Password must be at least 8 characters.');
if ($password !== $confirmPassword)               jsonResponse(false, 'Passwords do not match.');

$db   = getDB();
$hash = password_hash($password, PASSWORD_BCRYPT, ['cost' => 12]);

if ($role === 'mentor') {
    $check = $db->prepare('SELECT id FROM mentors WHERE email=:e OR employee_id=:eid LIMIT 1');
    $check->execute([':e' => $email, ':eid' => $idNumber]);
    if ($check->fetch()) jsonResponse(false, 'Email or Employee ID already exists.');

    $stmt = $db->prepare('INSERT INTO mentors (first_name,last_name,email,employee_id,department,password_hash)
                          VALUES (:fn,:ln,:e,:eid,:dept,:hash)');
    $stmt->execute([':fn'=>$firstName,':ln'=>$lastName,':e'=>$email,':eid'=>$idNumber,':dept'=>$department,':hash'=>$hash]);
    $newId = (int)$db->lastInsertId();
    jsonResponse(true, 'Mentor account created!', ['user'=>['id'=>$newId,'role'=>'mentor','name'=>"$firstName $lastName",'email'=>$email,'department'=>$department]]);

} else {
    $check = $db->prepare('SELECT id FROM mentees WHERE email=:e OR roll_number=:r LIMIT 1');
    $check->execute([':e' => $email, ':r' => $idNumber]);
    if ($check->fetch()) jsonResponse(false, 'Email or Roll Number already exists.');

    // Validate mentor_id if provided
    if ($mentorId) {
        $mCheck = $db->prepare('SELECT id FROM mentors WHERE id=:id AND is_active=1 LIMIT 1');
        $mCheck->execute([':id' => $mentorId]);
        if (!$mCheck->fetch()) jsonResponse(false, 'Selected mentor not found.');
    }

    $stmt = $db->prepare('INSERT INTO mentees (first_name,last_name,email,roll_number,department,password_hash,mentor_id)
                          VALUES (:fn,:ln,:e,:r,:dept,:hash,:mid)');
    $stmt->execute([':fn'=>$firstName,':ln'=>$lastName,':e'=>$email,':r'=>$idNumber,':dept'=>$department,':hash'=>$hash,':mid'=>$mentorId]);
    $newId = (int)$db->lastInsertId();
    jsonResponse(true, 'Student account created!', ['user'=>['id'=>$newId,'role'=>'mentee','name'=>"$firstName $lastName",'email'=>$email,'department'=>$department,'mentor_id'=>$mentorId]]);
}

And the code to handle everything in the backend when ran on a server is done by Mysql language 
-- ============================================================
--  MentorBridge v2 – Migration SQL
--  Run this in phpMyAdmin on your existing mentorbridge DB
--  (works on both local WAMP and InfinityFree)
-- ============================================================

-- Add mentor_id column to mentees if not already there
ALTER TABLE mentees
  ADD COLUMN IF NOT EXISTS mentor_id INT UNSIGNED NULL AFTER password_hash;

-- Sessions table – tracks who is logged in
CREATE TABLE IF NOT EXISTS sessions (
    id           INT UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    session_token VARCHAR(128) NOT NULL UNIQUE,
    role         ENUM('mentor','mentee') NOT NULL,
    user_id      INT UNSIGNED NOT NULL,
    created_at   TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    expires_at   TIMESTAMP NOT NULL,
    INDEX idx_token (session_token)
) ENGINE=InnoDB;

