[index.html](https://github.com/user-attachments/files/26880483/index.html)
# OPI<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>CVS Pharmacy — Weekly Task Checklist</title>
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,sans-serif;background:#F1EFE8;min-height:100vh;display:flex;align-items:flex-start;justify-content:center;padding:1rem}
.app{width:100%;max-width:960px;background:#fff;border-radius:12px;overflow:hidden;box-shadow:0 1px 4px rgba(0,0,0,0.08)}
.screen{display:none}.screen.active{display:block}
.login-wrap{min-height:420px;display:flex;align-items:center;justify-content:center;padding:2rem}
.login-card{background:#fff;border:0.5px solid #D3D1C7;border-radius:12px;padding:2rem;width:100%;max-width:360px}
.login-logo{background:#534AB7;border-radius:8px;padding:10px 14px;display:inline-block;margin-bottom:1.25rem}
.login-logo-text{color:#EEEDFE;font-size:13px;font-weight:500}
.login-title{font-size:16px;font-weight:500;color:#2C2C2A;margin-bottom:4px}
.login-sub{font-size:12px;color:#5F5E5A;margin-bottom:1.25rem;line-height:1.5}
.field-label{font-size:11px;color:#5F5E5A;margin-bottom:4px;font-weight:500}
.field-wrap{margin-bottom:14px}
.login-input{width:100%;height:38px;font-size:13px;padding:0 10px;border-radius:8px;border:0.5px solid #B4B2A9;background:#fff;color:#2C2C2A;outline:none}
.login-input:focus{border-color:#534AB7}
.login-input.err{border-color:#A32D2D}
.login-btn{width:100%;height:38px;background:#534AB7;color:#EEEDFE;border:none;border-radius:8px;font-size:13px;font-weight:500;cursor:pointer;margin-top:2px}
.login-btn:hover{background:#3C3489}
.login-btn:disabled{background:#AFA9EC;cursor:not-allowed}
.login-err{font-size:12px;color:#A32D2D;margin-top:8px;display:none}
.login-err.show{display:block}
.login-toggle{font-size:11px;color:#5F5E5A;margin-top:14px;text-align:center}
.login-toggle a{color:#534AB7;cursor:pointer;text-decoration:underline}
.top-bar{background:#534AB7;padding:10px 16px;display:flex;align-items:center;justify-content:space-between;gap:8px;flex-wrap:wrap}
.top-bar-title{color:#EEEDFE;font-size:14px;font-weight:500}
.top-bar-sub{color:#AFA9EC;font-size:11px;margin-top:1px}
.top-bar-right{display:flex;align-items:center;gap:8px;flex-wrap:wrap}
.signout-btn{font-size:11px;color:#AFA9EC;background:rgba(255,255,255,0.1);border:0.5px solid #AFA9EC;border-radius:8px;padding:4px 10px;cursor:pointer}
.signout-btn:hover{background:rgba(255,255,255,0.2)}
.user-chip{font-size:11px;color:#EEEDFE;background:rgba(255,255,255,0.12);border:0.5px solid rgba(255,255,255,0.25);border-radius:10px;padding:3px 10px;white-space:nowrap}
.sync-dot{width:7px;height:7px;border-radius:50%;background:#5DCAA5;display:inline-block;margin-right:4px}
.sync-dot.err{background:#F0997B}
.sync-dot.syncing{background:#FAC775}
.stat-row{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:8px;padding:10px 14px;background:#F1EFE8}
.stat{background:#fff;border:0.5px solid #D3D1C7;border-radius:8px;padding:7px 10px}
.stat-label{font-size:11px;color:#5F5E5A;margin-bottom:1px}
.stat-val{font-size:19px;font-weight:500;color:#2C2C2A}
.stat-val.green{color:#0F6E56}.stat-val.amber{color:#BA7517}
.period-bar{display:flex;gap:8px;padding:8px 14px;background:#F1EFE8;border-bottom:0.5px solid #D3D1C7;flex-wrap:wrap}
.period-chip{font-size:11px;padding:3px 10px;border-radius:10px;border:0.5px solid #D3D1C7;background:#fff;color:#5F5E5A}
.period-chip span{font-weight:500;color:#2C2C2A}
.main{display:grid;grid-template-columns:minmax(0,1.6fr) minmax(0,1fr)}
@media(max-width:600px){.main{grid-template-columns:1fr}.stat-row{grid-template-columns:repeat(2,1fr)}}
.checklist-col{border-right:0.5px solid #D3D1C7}
.section-hdr{padding:6px 14px;font-size:10px;font-weight:500;letter-spacing:.06em;text-transform:uppercase;color:#5F5E5A;background:#F1EFE8;border-bottom:0.5px solid #D3D1C7;border-top:0.5px solid #D3D1C7;display:flex;align-items:center;justify-content:space-between}
.reset-badge{font-size:9px;font-weight:400;padding:1px 6px;border-radius:8px;letter-spacing:0}
.reset-daily{background:#E1F5EE;color:#085041}
.reset-weekly{background:#EEEDFE;color:#3C3489}
.reset-monthly{background:#FAEEDA;color:#633806}
.task-row{display:flex;align-items:center;gap:10px;padding:7px 14px;border-bottom:0.5px solid #D3D1C7;cursor:pointer;transition:background .1s}
.task-row:hover{background:#F1EFE8}
.task-row.done{background:#E1F5EE}
.task-row.done .task-label{color:#085041;text-decoration:line-through}
.task-row.done .check{background:#1D9E75;border-color:#1D9E75}
.task-row.done .check svg{display:block}
.task-row.loading{opacity:.5;pointer-events:none}
.check{width:16px;height:16px;border-radius:3px;border:1px solid #B4B2A9;flex-shrink:0;display:flex;align-items:center;justify-content:center;background:#fff}
.check svg{display:none;width:9px;height:9px}
.task-label{font-size:13px;color:#2C2C2A;line-height:1.4;flex:1}
.task-meta{font-size:10px;color:#5F5E5A;white-space:nowrap;max-width:90px;overflow:hidden;text-overflow:ellipsis}
.monthly-section{padding:8px 0}
.monthly-row{display:flex;align-items:flex-start;gap:10px;padding:7px 14px;border-bottom:0.5px solid #D3D1C7;cursor:pointer;transition:background .1s}
.monthly-row:hover{background:#F1EFE8}
.monthly-row.done{background:#E1F5EE}
.monthly-row.done .task-label{color:#085041;text-decoration:line-through}
.monthly-row.done .check{background:#1D9E75;border-color:#1D9E75}
.monthly-row.done .check svg{display:block}
.monthly-row.loading{opacity:.5;pointer-events:none}
.monthly-note{font-size:11px;color:#5F5E5A;line-height:1.4;margin-top:2px}
.monthly-row.done .monthly-note{color:#1D9E75}
.right-col{background:#fff}
.right-hdr{padding:8px 14px;font-size:10px;font-weight:500;letter-spacing:.06em;text-transform:uppercase;color:#5F5E5A;background:#F1EFE8;border-bottom:0.5px solid #D3D1C7}
.activity-item{display:flex;gap:10px;padding:7px 14px;border-bottom:0.5px solid #D3D1C7;align-items:flex-start}
.activity-dot{width:8px;height:8px;border-radius:50%;flex-shrink:0;margin-top:3px}
.activity-dot.c{background:#1D9E75}.activity-dot.u{background:#D85A30}
.activity-text{font-size:12px;color:#2C2C2A;line-height:1.4;flex:1}
.activity-text span{color:#5F5E5A;font-size:10px;display:block;margin-top:1px}
.empty-msg{padding:20px 14px;font-size:12px;color:#5F5E5A;text-align:center}
.progress-bar{height:4px;background:#D3D1C7;overflow:hidden}
.progress-fill{height:100%;background:#1D9E75;transition:width .4s}
.week-label{padding:5px 14px 7px;font-size:11px;color:#5F5E5A;display:flex;justify-content:space-between}
.celebrate-banner{display:none;background:#085041;padding:12px 16px;text-align:center;border-top:2px solid #1D9E75}
.celebrate-banner.show{display:block}
.celebrate-text{color:#9FE1CB;font-size:14px;font-weight:500}
.celebrate-sub{color:#5DCAA5;font-size:11px;margin-top:3px}
canvas#confetti-canvas{position:fixed;top:0;left:0;width:100%;height:100%;pointer-events:none;z-index:999}
.mgr-stat-row{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:8px;padding:10px 14px;background:#F1EFE8}
.store-cards{display:grid;grid-template-columns:repeat(auto-fill,minmax(180px,1fr));gap:10px;padding:14px}
.store-card{background:#fff;border:0.5px solid #D3D1C7;border-radius:12px;padding:12px;cursor:pointer;transition:border .15s}
.store-card:hover{border-color:#534AB7}
.store-card-num{font-size:13px;font-weight:500;color:#2C2C2A;margin-bottom:4px}
.store-card-pct{font-size:22px;font-weight:500}
.store-card-bar{height:4px;background:#D3D1C7;border-radius:2px;margin:6px 0 4px;overflow:hidden}
.store-card-fill{height:100%;border-radius:2px;transition:width .4s}
.store-card-sub{font-size:10px;color:#5F5E5A}
.store-card-time{font-size:10px;color:#888780;margin-top:3px}
.drill-hdr{display:flex;align-items:center;gap:10px;padding:10px 14px;border-bottom:0.5px solid #D3D1C7;background:#F1EFE8}
.back-btn{font-size:12px;color:#534AB7;cursor:pointer;background:none;border:none;padding:0}
.back-btn:hover{text-decoration:underline}
.drill-title{font-size:13px;font-weight:500;color:#2C2C2A}
.no-stores{padding:2rem;text-align:center;font-size:13px;color:#5F5E5A}
.mgr-badge{background:rgba(255,255,255,0.15);color:#EEEDFE;font-size:11px;padding:3px 8px;border-radius:10px;border:0.5px solid rgba(255,255,255,0.3)}
.refresh-btn{font-size:11px;color:#AFA9EC;background:rgba(255,255,255,0.1);border:0.5px solid #AFA9EC;border-radius:8px;padding:4px 10px;cursor:pointer}
.refresh-btn:hover{background:rgba(255,255,255,0.2)}
.mgr-search-bar{display:flex;align-items:center;gap:8px;padding:10px 14px;background:#fff;border-bottom:0.5px solid #D3D1C7;flex-wrap:wrap}
.mgr-search-input{height:34px;font-size:13px;padding:0 10px;border-radius:8px;border:0.5px solid #B4B2A9;background:#fff;color:#2C2C2A;outline:none;width:180px}
.mgr-search-input:focus{border-color:#534AB7}
.mgr-search-btn{height:34px;padding:0 14px;background:#534AB7;color:#EEEDFE;border:none;border-radius:8px;font-size:12px;font-weight:500;cursor:pointer}
.mgr-search-btn:hover{background:#3C3489}
.mgr-search-clear{height:34px;padding:0 12px;background:#fff;color:#5F5E5A;border:0.5px solid #D3D1C7;border-radius:8px;font-size:12px;cursor:pointer}
.mgr-search-clear:hover{background:#F1EFE8}
.search-result-banner{padding:7px 14px;font-size:12px;background:#EEEDFE;color:#3C3489;border-bottom:0.5px solid #D3D1C7;display:none}
.search-result-banner.show{display:block}
.history-panel{border-top:0.5px solid #D3D1C7}
.history-hdr{display:flex;align-items:center;justify-content:space-between;padding:10px 14px;background:#F1EFE8;border-bottom:0.5px solid #D3D1C7}
.history-hdr-title{font-size:13px;font-weight:500;color:#2C2C2A}
.history-toolbar{display:flex;align-items:center;gap:8px;padding:8px 14px;background:#fff;border-bottom:0.5px solid #D3D1C7;flex-wrap:wrap}
.history-date-range{display:flex;align-items:center;gap:6px;flex-wrap:wrap}
.range-label{font-size:11px;color:#5F5E5A;white-space:nowrap}
.history-summary{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:8px;padding:10px 14px;background:#F1EFE8}
.history-feed{max-height:320px;overflow-y:auto}
.history-mode-banner{background:#EEEDFE;border-bottom:0.5px solid #AFA9EC;padding:7px 14px;font-size:12px;color:#3C3489;display:none}
.history-mode-banner.show{display:flex;align-items:center;justify-content:space-between;gap:8px}
.history-mode-back{font-size:11px;color:#534AB7;cursor:pointer;background:none;border:none;padding:0;font-weight:500;white-space:nowrap}
.history-mode-back:hover{text-decoration:underline}
.task-row.history-checked{background:#E1F5EE;cursor:default}
.task-row.history-checked .task-label{color:#085041}
.task-row.history-checked .check{background:#1D9E75;border-color:#1D9E75}
.task-row.history-checked .check svg{display:block}
.task-row.history-unchecked{background:#fff;cursor:default;opacity:0.5}
.monthly-row.history-checked{background:#E1F5EE;cursor:default}
.monthly-row.history-checked .task-label{color:#085041}
.monthly-row.history-checked .check{background:#1D9E75;border-color:#1D9E75}
.monthly-row.history-checked .check svg{display:block}
.monthly-row.history-unchecked{background:#fff;cursor:default;opacity:0.5}
.activity-toolbar{display:flex;align-items:center;gap:8px;padding:8px 14px;background:#F1EFE8;border-bottom:0.5px solid #D3D1C7;flex-wrap:wrap}
.activity-toolbar label{font-size:11px;color:#5F5E5A;font-weight:500;white-space:nowrap}
.date-picker{height:30px;font-size:12px;padding:0 8px;border-radius:8px;border:0.5px solid #B4B2A9;background:#fff;color:#2C2C2A;outline:none}
.date-picker:focus{border-color:#534AB7}
.date-go-btn{height:30px;padding:0 12px;background:#534AB7;color:#EEEDFE;border:none;border-radius:8px;font-size:12px;font-weight:500;cursor:pointer;white-space:nowrap}
.date-go-btn:hover{background:#3C3489}
.today-btn{height:30px;padding:0 10px;background:#fff;color:#534AB7;border:0.5px solid #534AB7;border-radius:8px;font-size:12px;cursor:pointer;white-space:nowrap}
.today-btn:hover{background:#EEEDFE}
.activity-date-label{font-size:11px;color:#5F5E5A;padding:6px 14px 4px;font-style:italic}
</style>
</head>
<body>
<canvas id="confetti-canvas"></canvas>
<div class="app">

<!-- LOGIN -->
<div id="screen-login" class="screen active">
  <div class="login-wrap">
    <div class="login-card">
      <div class="login-logo"><span class="login-logo-text">CVS Pharmacy</span></div>
      <div class="login-title" id="login-title">Pharmacy Task Checklist</div>
      <div class="login-sub" id="login-sub">Enter your details to get started</div>
      <div id="store-fields">
        <div class="field-wrap">
          <div class="field-label">Store number</div>
          <input class="login-input" id="f-store" placeholder="e.g. 04281">
        </div>
        <div class="field-wrap">
          <div class="field-label">Your name</div>
          <input class="login-input" id="f-name" placeholder="e.g. Maria R.">
        </div>
      </div>
      <div id="mgr-fields" style="display:none">
        <div class="field-wrap">
          <div class="field-label">Manager PIN</div>
          <input class="login-input" id="f-pin" placeholder="Enter PIN" type="password">
        </div>
      </div>
      <div class="login-err" id="login-err">Please fill in all fields.</div>
      <button class="login-btn" id="login-btn" onclick="doLogin()">Start my shift</button>
      <div class="login-toggle" id="login-toggle"><a onclick="toggleMode()">Manager login</a></div>
    </div>
  </div>
</div>

<!-- STORE VIEW -->
<div id="screen-store" class="screen">
  <div class="top-bar">
    <div>
      <div class="top-bar-title" id="store-bar-title">Store checklist</div>
      <div class="top-bar-sub" id="store-bar-sub"></div>
    </div>
    <div class="top-bar-right">
      <span class="user-chip"><span class="sync-dot" id="sync-dot"></span><span id="sync-label">Live</span></span>
      <span class="user-chip" id="user-chip"></span>
      <button class="signout-btn" onclick="signOut()">Sign out</button>
    </div>
  </div>
  <div class="progress-bar"><div class="progress-fill" id="store-progress"></div></div>
  <div class="week-label"><span id="store-week-lbl"></span><span id="store-pct-lbl" style="font-weight:500;color:#0F6E56"></span></div>
  <div class="period-bar">
    <div class="period-chip">Today: <span id="chip-today"></span></div>
    <div class="period-chip">Week resets: <span id="chip-week"></span></div>
    <div class="period-chip">Month resets: <span id="chip-month"></span></div>
  </div>
  <div class="stat-row">
    <div class="stat"><div class="stat-label">Total tasks</div><div class="stat-val" id="st-total">0</div></div>
    <div class="stat"><div class="stat-label">Completed</div><div class="stat-val green" id="st-done">0</div></div>
    <div class="stat"><div class="stat-label">Remaining</div><div class="stat-val amber" id="st-remain">0</div></div>
    <div class="stat"><div class="stat-label">Daily progress</div><div class="stat-val green" id="st-daily">0%</div></div>
  </div>
  <div class="celebrate-banner" id="celebrate-banner">
    <div class="celebrate-text" id="celebrate-text">All daily tasks complete!</div>
    <div class="celebrate-sub" id="celebrate-sub">Outstanding work today.</div>
  </div>
  <div class="main">
    <div class="checklist-col">
      <div class="history-mode-banner" id="history-mode-banner">
        <span id="history-mode-text">Viewing history</span>
        <button class="history-mode-back" onclick="backToToday()">← Back to today</button>
      </div>
      <div class="section-hdr">Before lunch <span class="reset-badge reset-daily">resets daily</span></div>
      <div id="s-tasks-before-lunch"></div>
      <div class="section-hdr">Before close <span class="reset-badge reset-daily">resets daily</span></div>
      <div id="s-tasks-before-close"></div>
      <div class="section-hdr">Weekly tasks <span class="reset-badge reset-weekly">resets Sunday</span></div>
      <div id="s-tasks-weekly"></div>
      <div class="section-hdr" style="color:#BA7517">Monthly reminders <span class="reset-badge reset-monthly">resets 1st</span></div>
      <div class="monthly-section" id="s-tasks-monthly"></div>
    </div>
    <div class="right-col">
      <div class="right-hdr">Activity — this store</div>
      <div class="activity-toolbar">
        <label>View date:</label>
        <input type="date" class="date-picker" id="store-date-picker">
        <button class="date-go-btn" onclick="loadStoreActivityForDate()">View</button>
        <button class="today-btn" onclick="resetStoreToToday()">Today</button>
      </div>
      <div class="activity-date-label" id="store-date-label"></div>
      <div id="store-activity"><div class="empty-msg">Check-offs will appear here</div></div>
    </div>
  </div>
</div>

<!-- MANAGER VIEW -->
<div id="screen-manager" class="screen">
  <div class="top-bar">
    <div>
      <div class="top-bar-title">Manager dashboard</div>
      <div class="top-bar-sub">All store locations — live</div>
    </div>
    <div class="top-bar-right">
      <span class="mgr-badge">Manager view</span>
      <button class="refresh-btn" onclick="renderManagerDashboard()">Refresh</button>
      <button class="signout-btn" onclick="signOut()">Sign out</button>
    </div>
  </div>
  <div class="mgr-stat-row">
    <div class="stat"><div class="stat-label">Stores active</div><div class="stat-val" id="m-stores">0</div></div>
    <div class="stat"><div class="stat-label">Avg completion</div><div class="stat-val green" id="m-avg">0%</div></div>
    <div class="stat"><div class="stat-label">Fully complete</div><div class="stat-val green" id="m-full">0</div></div>
  </div>
  <div id="mgr-overview">
    <div class="mgr-search-bar">
      <input class="mgr-search-input" id="mgr-search-input" placeholder="Search store number..." oninput="filterStoreCards()" onkeydown="if(event.key==='Enter')searchStoreHistory()">
      <button class="mgr-search-btn" onclick="searchStoreHistory()">View store history</button>
      <button class="mgr-search-clear" onclick="clearSearch()" id="mgr-clear-btn" style="display:none">Clear</button>
    </div>
    <div class="search-result-banner" id="search-banner"></div>
    <div style="padding:10px 14px 4px;font-size:11px;font-weight:500;color:#5F5E5A;letter-spacing:.05em;text-transform:uppercase" id="mgr-cards-label">All locations — click any store to drill in</div>
    <div class="store-cards" id="store-cards"></div>
    <div class="no-stores" id="no-stores" style="display:none">No store activity yet. Stores will appear once they log in and start checking off tasks.</div>
  </div>

  <!-- STORE HISTORY PANEL -->
  <div id="mgr-history" style="display:none">
    <div class="history-hdr">
      <span class="history-hdr-title" id="history-title">Store history</span>
      <button class="back-btn" onclick="closeHistory()">← Back to all stores</button>
    </div>
    <div class="history-toolbar">
      <div class="history-date-range">
        <span class="range-label">From:</span>
        <input type="date" class="date-picker" id="hist-from">
        <span class="range-label">To:</span>
        <input type="date" class="date-picker" id="hist-to">
        <button class="date-go-btn" onclick="loadStoreHistory()">Load history</button>
        <button class="today-btn" onclick="setHistoryToWeek()">This week</button>
        <button class="today-btn" onclick="setHistoryToMonth()">This month</button>
      </div>
    </div>
    <div class="history-summary">
      <div class="stat"><div class="stat-label">Total check-offs</div><div class="stat-val green" id="hist-total">0</div></div>
      <div class="stat"><div class="stat-label">Unique staff</div><div class="stat-val" id="hist-staff">0</div></div>
      <div class="stat"><div class="stat-label">Days active</div><div class="stat-val" id="hist-days">0</div></div>
    </div>
    <div class="history-feed" id="history-feed">
      <div class="empty-msg">Select a date range and click Load history</div>
    </div>
  </div>
  <div id="mgr-drill" style="display:none">
    <div class="drill-hdr">
      <button class="back-btn" onclick="closeDrill()">← All stores</button>
      <span class="drill-title" id="drill-title">Store detail</span>
    </div>
    <div class="main">
      <div class="checklist-col">
        <div class="section-hdr">Before lunch <span class="reset-badge reset-daily">resets daily</span></div><div id="d-tasks-before-lunch"></div>
        <div class="section-hdr">Before close <span class="reset-badge reset-daily">resets daily</span></div><div id="d-tasks-before-close"></div>
        <div class="section-hdr">Weekly tasks <span class="reset-badge reset-weekly">resets Sunday</span></div><div id="d-tasks-weekly"></div>
        <div class="section-hdr" style="color:#BA7517">Monthly reminders <span class="reset-badge reset-monthly">resets 1st</span></div>
        <div class="monthly-section" id="d-tasks-monthly"></div>
      </div>
      <div class="right-col">
        <div class="right-hdr">Activity log</div>
        <div class="activity-toolbar">
          <label>View activity for:</label>
          <input type="date" class="date-picker" id="drill-date-picker">
          <button class="date-go-btn" onclick="loadDrillActivity()">View</button>
          <button class="today-btn" onclick="resetDrillToToday()">Today</button>
        </div>
        <div class="activity-date-label" id="drill-date-label"></div>
        <div id="drill-activity"></div>
      </div>
    </div>
  </div>
</div>

</div>
<script>
const SB_URL="https://emfermnjlejhdrxvfmdl.supabase.co";
const SB_KEY="eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImVtZmVybW5qbGVqaGRyeHZmbWRsIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NzYzMDcyODgsImV4cCI6MjA5MTg4MzI4OH0.cw8ltlE1ivcLzk3EkczEmuiyltPRnqmw7eKtqS7ZGKQ";
const HDR={"Content-Type":"application/json","apikey":SB_KEY,"Authorization":"Bearer "+SB_KEY};
const MANAGER_PIN="7391";

const TASKS={
  "before-lunch":["Log TempAlert (by noon)","Complete WSAB","Sign RPh Logbook","Day 14s RTS (no Day 15)","Check mCC & respond to surveys","Do the daily huddle in Service Huddle Binder","Epic Credentials not being shared","OV Check In & Complete QI","WH & PSE Check in (same day)","Cycle Counts"],
  "before-close":["File Hardcopies","Empty Trash & fill printers/vials","Log TempAlert (by end of night)","Complete myWork Tasks & emails","CII State Counts","Unreconciled C2s are reconciled","Act on ALT+F3 Notification","RTS Maintenance"],
  "weekly":["EBOH","StrongPak","OV Returns","Order supplies (by 3pm on poll day)","Review M1-11 for PCC execution","Review Colleague Level POS Prompt Results","Review training exceptions & upcoming due dates","Update requests off, colleague availability, and truck changes in mySchedule","Publish myschedule"]
};
const MONTHLY=[
  {name:"Inmar",note:"Pull and send out 1x1s by the 10th of every month"},
  {name:"Regulatory Review",note:"Opens 2nd fiscal Friday of the month"},
  {name:"Warehouse Returns",note:"Review at ALT+3 for notification"},
  {name:"2 E-kits",note:"Double check the expiration dates"}
];
const DAILY_SECTIONS=["before-lunch","before-close"];

// ── Period key helpers ──────────────────────────────────────────────────────
// Each task key is prefixed with a period string so tasks from a different
// day/week/month never match and are effectively invisible (expired).
function todayKey(){
  let d=new Date();
  return d.getFullYear()+"-"+(d.getMonth()+1)+"-"+d.getDate();
}
function weekKey(){
  // Sunday = start of week; find the most recent Sunday
  let d=new Date();
  let day=d.getDay(); // 0=Sun
  let sun=new Date(d);
  sun.setDate(d.getDate()-day);
  return sun.getFullYear()+"-"+(sun.getMonth()+1)+"-"+sun.getDate();
}
function monthKey(){
  let d=new Date();
  return d.getFullYear()+"-"+(d.getMonth()+1);
}
function periodPrefix(section){
  if(section==="weekly") return "W:"+weekKey()+":";
  if(section==="monthly") return "M:"+monthKey()+":";
  return "D:"+todayKey()+":";
}
function tk(section,idx){return periodPrefix(section)+section+"__"+idx;}

// ── Period display strings ──────────────────────────────────────────────────
function fmtDate(d){return d.toLocaleDateString([],{month:"short",day:"numeric"});}
function updatePeriodChips(){
  let now=new Date();
  document.getElementById("chip-today").textContent=fmtDate(now);
  let daysUntilSun=(7-now.getDay())%7||7;
  let nextSun=new Date(now);nextSun.setDate(now.getDate()+daysUntilSun);
  document.getElementById("chip-week").textContent="Sunday "+fmtDate(nextSun);
  let nextFirst=new Date(now.getFullYear(),now.getMonth()+1,1);
  document.getElementById("chip-month").textContent=fmtDate(nextFirst);
}

let currentRole=null,currentStore=null,currentName=null;
let storeState={},wasAllDailyDone=false,isMgrMode=false,pollTimer=null;

async function sbGet(table,params=""){
  try{let r=await fetch(SB_URL+"/rest/v1/"+table+"?"+params,{headers:{...HDR,"Prefer":"return=representation"}});return r.ok?r.json():[];}catch(e){return[];}
}
async function sbUpsert(table,body){
  try{let r=await fetch(SB_URL+"/rest/v1/"+table,{method:"POST",headers:{...HDR,"Prefer":"resolution=merge-duplicates,return=minimal"},body:JSON.stringify(body)});return r.ok;}catch(e){return false;}
}
async function sbDelete(table,params){
  try{let r=await fetch(SB_URL+"/rest/v1/"+table+"?"+params,{method:"DELETE",headers:HDR});return r.ok;}catch(e){return false;}
}
async function sbInsert(table,body){
  try{let r=await fetch(SB_URL+"/rest/v1/"+table,{method:"POST",headers:{...HDR,"Prefer":"return=minimal"},body:JSON.stringify(body)});return r.ok;}catch(e){return false;}
}

function setSyncStatus(s){
  let dot=document.getElementById("sync-dot"),lbl=document.getElementById("sync-label");
  if(!dot||!lbl)return;
  dot.className="sync-dot"+(s==="err"?" err":s==="syncing"?" syncing":"");
  lbl.textContent=s==="err"?"Offline":s==="syncing"?"Syncing...":"Live";
}
function chkSVG(){return`<svg viewBox="0 0 9 9" fill="none"><path d="M1 4.5L3.5 7L8 1.5" stroke="white" stroke-width="1.5" stroke-linecap="round"/></svg>`;}
function fmtWeek(v){if(!v)return"";try{return new Date(v+"T12:00:00").toLocaleDateString([],{month:"long",day:"numeric",year:"numeric"});}catch(e){return v;}}
function fmtTime(iso){if(!iso)return"";try{const d=new Date(iso);return d.toLocaleTimeString([],{hour:"2-digit",minute:"2-digit"})+" · "+d.toLocaleDateString([],{month:"short",day:"numeric"});}catch(e){return iso;}}

function toggleMode(){
  isMgrMode=!isMgrMode;
  document.getElementById("store-fields").style.display=isMgrMode?"none":"";
  document.getElementById("mgr-fields").style.display=isMgrMode?"":"none";
  document.getElementById("login-title").textContent=isMgrMode?"Manager login":"Pharmacy Task Checklist";
  document.getElementById("login-sub").textContent=isMgrMode?"Enter your PIN to view all locations":"Enter your details to get started";
  document.getElementById("login-btn").textContent=isMgrMode?"Access dashboard":"Start my shift";
  document.getElementById("login-toggle").innerHTML=isMgrMode?'<a onclick="toggleMode()">← Store login</a>':'<a onclick="toggleMode()">Manager login</a>';
  document.getElementById("login-err").classList.remove("show");
  if(isMgrMode)setTimeout(()=>document.getElementById("f-pin").focus(),50);
}

async function doLogin(){
  let err=document.getElementById("login-err");
  err.classList.remove("show");
  let btn=document.getElementById("login-btn");
  try{
    if(isMgrMode){
      if(document.getElementById("f-pin").value.trim()!==MANAGER_PIN){err.textContent="Incorrect PIN.";err.classList.add("show");return;}
      currentRole="manager";showScreen("screen-manager");await renderManagerDashboard();
      pollTimer=setInterval(renderManagerDashboard,8000);
    }else{
      let store=document.getElementById("f-store").value.trim();
      let name=document.getElementById("f-name").value.trim();
      if(!store){document.getElementById("f-store").classList.add("err");err.textContent="Please enter your store number.";err.classList.add("show");return;}
      if(!name){document.getElementById("f-name").classList.add("err");err.textContent="Please enter your name.";err.classList.add("show");return;}
      ["f-store","f-name"].forEach(id=>document.getElementById(id).classList.remove("err"));
      btn.disabled=true;btn.textContent="Connecting...";
      currentRole="store";currentStore=store;currentName=name;
      let now=new Date();
      document.getElementById("store-bar-title").textContent="Store "+store;
      document.getElementById("store-bar-sub").textContent=now.toLocaleDateString([],{weekday:"long",month:"long",day:"numeric",year:"numeric"});
      document.getElementById("store-week-lbl").textContent="Store "+store+" · "+now.toLocaleDateString([],{weekday:"long",month:"long",day:"numeric"});
      document.getElementById("user-chip").textContent=name+" · Store "+store;
      updatePeriodChips();
      document.getElementById("store-date-picker").value=new Date().toISOString().split("T")[0];
      showScreen("screen-store");
      await loadStoreState();renderStoreChecklist();await renderStoreActivity();
      btn.disabled=false;btn.textContent="Start my shift";
      pollTimer=setInterval(async()=>{
        await loadStoreState();renderStoreChecklist();
        let picker=document.getElementById("store-date-picker");
        let todayISO=new Date().toISOString().split("T")[0];
        if(!picker.value||picker.value===todayISO) await renderStoreActivity();
      },6000);
    }
  }catch(e){
    btn.disabled=false;btn.textContent="Start my shift";
    err.textContent="Connection error: "+e.message+". Check your internet connection.";
    err.classList.add("show");
    currentRole=null;currentStore=null;currentName=null;
  }
  document.getElementById("f-pin").value="";
}

document.addEventListener("keydown",e=>{if(e.key==="Enter"&&document.getElementById("screen-login").classList.contains("active"))doLogin();});

function signOut(){
  if(pollTimer){clearInterval(pollTimer);pollTimer=null;}
  currentRole=null;currentStore=null;currentName=null;storeState={};wasAllDailyDone=false;
  if(isMgrMode)toggleMode();
  showScreen("screen-login");
}
function showScreen(id){document.querySelectorAll(".screen").forEach(s=>s.classList.remove("active"));document.getElementById(id).classList.add("active");}

async function loadStoreState(){
  setSyncStatus("syncing");
  try{
    // Only load keys that match current period prefixes — expired keys are ignored automatically
    let rows=await sbGet("checklist_state","store_id=eq."+encodeURIComponent(currentStore)+"&select=task_key,who,checked_at");
    storeState={};
    let validPrefixes=["D:"+todayKey()+":","W:"+weekKey()+":","M:"+monthKey()+":"];
    if(Array.isArray(rows))rows.forEach(r=>{
      if(validPrefixes.some(p=>r.task_key.startsWith(p)))
        storeState[r.task_key]={who:r.who,time:fmtTime(r.checked_at)};
    });
    setSyncStatus("ok");
  }catch(e){setSyncStatus("err");}
}

function allDailyDone(){
  for(let sec of DAILY_SECTIONS)for(let i=0;i<TASKS[sec].length;i++)if(!storeState[tk(sec,i)])return false;
  return true;
}

function renderStoreChecklist(){
  // Clear history mode if active
  let histBanner=document.getElementById("history-mode-banner");
  if(histBanner) histBanner.classList.remove("show");
  let total=0,done=0,dTotal=0,dDone=0;
  let prev=wasAllDailyDone;
  Object.keys(TASKS).forEach(sec=>{
    let id="s-tasks-"+(sec==="before-lunch"?"before-lunch":sec==="before-close"?"before-close":"weekly");
    let el=document.getElementById(id);if(!el)return;el.innerHTML="";
    TASKS[sec].forEach((task,idx)=>{
      let k=tk(sec,idx),isDone=!!storeState[k];
      total++;if(isDone)done++;
      if(DAILY_SECTIONS.includes(sec)){dTotal++;if(isDone)dDone++;}
      let row=document.createElement("div");row.className="task-row"+(isDone?" done":"");
      row.innerHTML=`<div class="check">${isDone?chkSVG():""}</div><div class="task-label">${task}</div>${isDone&&storeState[k]&&storeState[k].who?`<div class="task-meta">${storeState[k].who}</div>`:""}`;
      row.addEventListener("click",()=>toggleTask(row,sec,idx,task));
      el.appendChild(row);
    });
  });
  let mel=document.getElementById("s-tasks-monthly");if(!mel)return;mel.innerHTML="";
  MONTHLY.forEach((item,idx)=>{
    let k=tk("monthly",idx),isDone=!!storeState[k];
    total++;if(isDone)done++;
    let row=document.createElement("div");row.className="monthly-row"+(isDone?" done":"");
    row.innerHTML=`<div class="check" style="margin-top:2px">${isDone?chkSVG():""}</div><div style="flex:1"><div class="task-label">${item.name}${isDone&&storeState[k]&&storeState[k].who?` <span style="font-size:10px;color:#085041"> · ${storeState[k].who}</span>`:""}</div><div class="monthly-note">${item.note}</div></div>`;
    row.addEventListener("click",()=>toggleMonthly(row,idx,item.name));
    mel.appendChild(row);
  });
  let pct=total?Math.round(done/total*100):0;
  let dpct=dTotal?Math.round(dDone/dTotal*100):0;
  document.getElementById("st-total").textContent=total;
  document.getElementById("st-done").textContent=done;
  document.getElementById("st-remain").textContent=total-done;
  document.getElementById("st-daily").textContent=dpct+"%";
  document.getElementById("store-progress").style.width=pct+"%";
  document.getElementById("store-pct-lbl").textContent=pct+"% complete";
  let nowDone=allDailyDone();
  let celebBanner=document.getElementById("celebrate-banner");
  if(nowDone){
    celebBanner.classList.add("show");
    let names=[...new Set(Object.values(storeState).filter(v=>v&&v.who).map(v=>v.who))];
    document.getElementById("celebrate-text").textContent="All daily tasks complete — great work, Store "+currentStore+"!";
    document.getElementById("celebrate-sub").textContent=names.length?"Completed by: "+names.slice(0,4).join(", ")+(names.length>4?" + more":""):"Outstanding teamwork today.";
    if(!prev)launchConfetti();
  }else{celebBanner.classList.remove("show");}
  wasAllDailyDone=nowDone;
}

async function toggleTask(row,sec,idx,taskName){
  row.classList.add("loading");setSyncStatus("syncing");
  let k=tk(sec,idx),isDone=!!storeState[k];
  if(isDone){
    await sbDelete("checklist_state","store_id=eq."+encodeURIComponent(currentStore)+"&task_key=eq."+encodeURIComponent(k));
    await sbInsert("checklist_log",{store_id:currentStore,action:"unchecked",task_name:taskName,who:currentName});
    delete storeState[k];
  }else{
    await sbUpsert("checklist_state",{store_id:currentStore,task_key:k,who:currentName,checked_at:new Date().toISOString()});
    await sbInsert("checklist_log",{store_id:currentStore,action:"checked",task_name:taskName,who:currentName});
    storeState[k]={who:currentName,time:fmtTime(new Date().toISOString())};
  }
  setSyncStatus("ok");renderStoreChecklist();await renderStoreActivity();
}

async function toggleMonthly(row,idx,taskName){
  row.classList.add("loading");setSyncStatus("syncing");
  let k=tk("monthly",idx),isDone=!!storeState[k];
  if(isDone){
    await sbDelete("checklist_state","store_id=eq."+encodeURIComponent(currentStore)+"&task_key=eq."+encodeURIComponent(k));
    await sbInsert("checklist_log",{store_id:currentStore,action:"unchecked",task_name:taskName,who:currentName});
    delete storeState[k];
  }else{
    await sbUpsert("checklist_state",{store_id:currentStore,task_key:k,who:currentName,checked_at:new Date().toISOString()});
    await sbInsert("checklist_log",{store_id:currentStore,action:"checked",task_name:taskName,who:currentName});
    storeState[k]={who:currentName,time:fmtTime(new Date().toISOString())};
  }
  setSyncStatus("ok");renderStoreChecklist();await renderStoreActivity();
}

// Returns the ISO date range [start, end] for the current day
function currentDayRange(){
  let t=new Date().toISOString().split("T")[0];
  return [t+"T00:00:00.000Z", t+"T23:59:59.999Z"];
}
// Returns ISO date range for the current week (Sun–Sat)
function currentWeekRange(){
  let now=new Date();
  let sun=new Date(now); sun.setDate(now.getDate()-now.getDay()); sun.setHours(0,0,0,0);
  let sat=new Date(sun); sat.setDate(sun.getDate()+6); sat.setHours(23,59,59,999);
  return [sun.toISOString(), sat.toISOString()];
}
// Returns ISO date range for the current calendar month
function currentMonthRange(){
  let now=new Date();
  let start=new Date(now.getFullYear(),now.getMonth(),1);
  let end=new Date(now.getFullYear(),now.getMonth()+1,0,23,59,59,999);
  return [start.toISOString(), end.toISOString()];
}

async function renderStoreActivity(){
  // Default: show today only — set picker to today and load
  let picker=document.getElementById("store-date-picker");
  if(!picker.value) picker.value=new Date().toISOString().split("T")[0];
  await loadStoreActivityForDate();
}

async function loadStoreActivityForDate(){
  let picker=document.getElementById("store-date-picker");
  let lbl=document.getElementById("store-date-label");
  let feed=document.getElementById("store-activity");
  if(!feed)return;
  feed.innerHTML='<div class="empty-msg">Loading...</div>';

  let dateVal=picker.value||new Date().toISOString().split("T")[0];
  let start=dateVal+"T00:00:00.000Z";
  let end=dateVal+"T23:59:59.999Z";
  let isToday=dateVal===new Date().toISOString().split("T")[0];
  let d=new Date(dateVal+"T12:00:00");
  lbl.textContent=isToday?"Today's activity":"Activity for "+d.toLocaleDateString([],{weekday:"long",month:"long",day:"numeric",year:"numeric"});

  let params="store_id=eq."+encodeURIComponent(currentStore)
    +"&order=logged_at.desc&limit=100"
    +"&logged_at=gte."+encodeURIComponent(start)
    +"&logged_at=lte."+encodeURIComponent(end);

  let rows=await sbGet("checklist_log",params);
  feed.innerHTML="";
  if(!Array.isArray(rows)||!rows.length){
    feed.innerHTML='<div class="empty-msg">No activity found for this date</div>';
    // If past date, also update left checklist to show empty state
    if(!isToday) renderHistoryChecklist({}, dateVal);
    else renderStoreChecklist();
    return;
  }
  rows.forEach(e=>{
    let item=document.createElement("div");item.className="activity-item";
    item.innerHTML=`<div class="activity-dot ${e.action==="checked"?"c":"u"}"></div><div class="activity-text"><strong style="font-weight:500">${e.who}</strong> ${e.action==="checked"?"completed":"unchecked"} <em style="font-style:normal">${e.task_name}</em><span>${fmtTime(e.logged_at)}</span></div>`;
    feed.appendChild(item);
  });

  // Build a completed-task map from the log for the left checklist
  if(!isToday){
    // Find the last action per task — if "checked" it was done, "unchecked" it wasn't
    let taskFinalState={};
    // rows are desc by time; iterate reversed to get chronological order
    [...rows].reverse().forEach(r=>{taskFinalState[r.task_name]=r;});
    renderHistoryChecklist(taskFinalState, dateVal);
  } else {
    renderStoreChecklist();
  }
}

// Renders the left checklist in read-only history mode
function renderHistoryChecklist(taskFinalState, dateVal){
  let d=new Date(dateVal+"T12:00:00");
  let dateStr=d.toLocaleDateString([],{weekday:"long",month:"long",day:"numeric",year:"numeric"});

  // Show history mode banner
  let histModeBanner=document.getElementById("history-mode-banner");
  histModeBanner.classList.add("show");
  document.getElementById("history-mode-text").textContent="Viewing: "+dateStr+" (read-only)";

  // Build set of completed task names
  let completed=new Set();
  let completedBy={};
  Object.values(taskFinalState).forEach(r=>{
    if(r.action==="checked"){completed.add(r.task_name);completedBy[r.task_name]=r.who;}
  });

  Object.keys(TASKS).forEach(sec=>{
    let id="s-tasks-"+(sec==="before-lunch"?"before-lunch":sec==="before-close"?"before-close":"weekly");
    let el=document.getElementById(id);if(!el)return;el.innerHTML="";
    TASKS[sec].forEach((task)=>{
      let isDone=completed.has(task);
      let row=document.createElement("div");
      row.className="task-row "+(isDone?"history-checked":"history-unchecked");
      row.innerHTML=`<div class="check">${isDone?chkSVG():""}</div><div class="task-label">${task}</div>${isDone&&completedBy[task]?`<div class="task-meta">${completedBy[task]}</div>`:""}`;
      el.appendChild(row);
    });
  });

  let mel=document.getElementById("s-tasks-monthly");if(!mel)return;mel.innerHTML="";
  MONTHLY.forEach((item)=>{
    let isDone=completed.has(item.name);
    let row=document.createElement("div");
    row.className="monthly-row "+(isDone?"history-checked":"history-unchecked");
    row.innerHTML=`<div class="check" style="margin-top:2px">${isDone?chkSVG():""}</div><div style="flex:1"><div class="task-label">${item.name}${isDone&&completedBy[item.name]?` <span style="font-size:10px;color:#085041"> · ${completedBy[item.name]}</span>`:""}</div><div class="monthly-note">${item.note}</div></div>`;
    mel.appendChild(row);
  });

  // Update stats to reflect history snapshot
  let total=Object.values(TASKS).reduce((a,t)=>a+t.length,0)+MONTHLY.length;
  let done=completed.size;
  document.getElementById("st-total").textContent=total;
  document.getElementById("st-done").textContent=done;
  document.getElementById("st-remain").textContent=total-done;
  document.getElementById("st-daily").textContent="—";
  document.getElementById("store-progress").style.width=(total?Math.round(done/total*100):0)+"%";
  document.getElementById("store-pct-lbl").textContent=(total?Math.round(done/total*100):0)+"% that day";
  document.getElementById("celebrate-banner").classList.remove("show");
}

function backToToday(){
  let picker=document.getElementById("store-date-picker");
  picker.value=new Date().toISOString().split("T")[0];
  document.getElementById("history-mode-banner").classList.remove("show");
  loadStoreActivityForDate();
}

function resetStoreToToday(){
  backToToday();
}

async function renderManagerDashboard(){
  let allRows=await sbGet("checklist_state","select=store_id,task_key,who,checked_at&order=store_id");
  let logRows=await sbGet("checklist_log","select=store_id,logged_at&order=logged_at.desc");
  let cardsEl=document.getElementById("store-cards"),noEl=document.getElementById("no-stores");
  if(!cardsEl)return;
  // Manager sees current-period tasks only
  let validPrefixes=["D:"+todayKey()+":","W:"+weekKey()+":","M:"+monthKey()+":"];
  let storeMap={};
  if(Array.isArray(allRows))allRows.forEach(r=>{
    if(!validPrefixes.some(p=>r.task_key.startsWith(p)))return;
    if(!storeMap[r.store_id])storeMap[r.store_id]={state:{}};
    storeMap[r.store_id].state[r.task_key]=r;
  });
  let lastAct={};
  if(Array.isArray(logRows))logRows.forEach(r=>{if(!lastAct[r.store_id])lastAct[r.store_id]=r.logged_at;});
  let stores=Object.keys(storeMap);
  cardsEl.innerHTML="";
  if(!stores.length){noEl.style.display="";cardsEl.style.display="none";["m-stores","m-avg","m-full"].forEach(id=>document.getElementById(id).textContent=id==="m-avg"?"0%":"0");return;}
  noEl.style.display="none";cardsEl.style.display="";
  let totalTasks=Object.values(TASKS).reduce((a,t)=>a+t.length,0)+MONTHLY.length;
  let tPct=0,fullCount=0;
  stores.sort().forEach(s=>{
    let done=Object.keys(storeMap[s].state).length;
    let pct=Math.round(done/totalTasks*100);
    tPct+=pct;if(pct===100)fullCount++;
    let color=pct>=80?"#1D9E75":pct>=50?"#BA7517":"#D85A30";
    let last=lastAct[s]?fmtTime(lastAct[s]):"No activity yet";
    let card=document.createElement("div");card.className="store-card";
    card.innerHTML=`<div class="store-card-num">Store ${s}</div><div class="store-card-pct" style="color:${color}">${pct}%</div><div class="store-card-bar"><div class="store-card-fill" style="width:${pct}%;background:${color}"></div></div><div class="store-card-sub">${done} of ${totalTasks} tasks done</div><div class="store-card-time">Last: ${last}</div>`;
    card.addEventListener("click",()=>openDrill(s,storeMap[s].state));
    cardsEl.appendChild(card);
  });
  document.getElementById("m-stores").textContent=stores.length;
  document.getElementById("m-avg").textContent=(stores.length?Math.round(tPct/stores.length):0)+"%";
  document.getElementById("m-full").textContent=fullCount;
}

let drillStoreNum=null;

function openDrill(storeNum,state){
  drillStoreNum=storeNum;
  document.getElementById("mgr-overview").style.display="none";
  document.getElementById("mgr-drill").style.display="";
  document.getElementById("drill-title").textContent="Store "+storeNum+" — task detail";

  // Set date picker to today
  let todayISO=new Date().toISOString().split("T")[0];
  document.getElementById("drill-date-picker").value=todayISO;

  Object.keys(TASKS).forEach(sec=>{
    let id="d-tasks-"+(sec==="before-lunch"?"before-lunch":sec==="before-close"?"before-close":"weekly");
    let el=document.getElementById(id);if(!el)return;el.innerHTML="";
    TASKS[sec].forEach((task,idx)=>{
      let k=tk(sec,idx),isDone=!!state[k];
      let row=document.createElement("div");row.className="task-row"+(isDone?" done":"");row.style.cursor="default";
      row.innerHTML=`<div class="check">${isDone?chkSVG():""}</div><div class="task-label">${task}</div>${isDone&&state[k]&&state[k].who?`<div class="task-meta">${state[k].who}</div>`:""}`;
      el.appendChild(row);
    });
  });
  let mel=document.getElementById("d-tasks-monthly");if(!mel)return;mel.innerHTML="";
  MONTHLY.forEach((item,idx)=>{
    let k=tk("monthly",idx),isDone=!!state[k];
    let row=document.createElement("div");row.className="monthly-row"+(isDone?" done":"");row.style.cursor="default";
    row.innerHTML=`<div class="check" style="margin-top:2px">${isDone?chkSVG():""}</div><div style="flex:1"><div class="task-label">${item.name}${isDone&&state[k]&&state[k].who?` <span style="font-size:10px;color:#085041"> · ${state[k].who}</span>`:""}</div><div class="monthly-note">${item.note}</div></div>`;
    mel.appendChild(row);
  });
  loadDrillActivity();
}

async function loadDrillActivity(){
  if(!drillStoreNum)return;
  let picker=document.getElementById("drill-date-picker");
  let dateVal=picker.value;
  let feed=document.getElementById("drill-activity");
  let lbl=document.getElementById("drill-date-label");
  feed.innerHTML='<div class="empty-msg">Loading...</div>';

  let params="store_id=eq."+encodeURIComponent(drillStoreNum)+"&order=logged_at.desc&limit=100";

  if(dateVal){
    // Filter to the selected calendar day (UTC date range)
    let start=dateVal+"T00:00:00.000Z";
    let end=dateVal+"T23:59:59.999Z";
    params+="&logged_at=gte."+encodeURIComponent(start)+"&logged_at=lte."+encodeURIComponent(end);
    let d=new Date(dateVal+"T12:00:00");
    let isToday=dateVal===new Date().toISOString().split("T")[0];
    lbl.textContent=isToday?"Showing today's activity":"Showing activity for "+d.toLocaleDateString([],{weekday:"long",month:"long",day:"numeric",year:"numeric"});
  } else {
    lbl.textContent="Showing all recent activity";
  }

  let rows=await sbGet("checklist_log",params);
  feed.innerHTML="";
  if(!Array.isArray(rows)||!rows.length){
    feed.innerHTML='<div class="empty-msg">No activity found for this date</div>';
    return;
  }
  rows.forEach(e=>{
    let item=document.createElement("div");item.className="activity-item";
    item.innerHTML=`<div class="activity-dot ${e.action==="checked"?"c":"u"}"></div><div class="activity-text"><strong style="font-weight:500">${e.who}</strong> ${e.action==="checked"?"completed":"unchecked"} <em style="font-style:normal">${e.task_name}</em><span>${fmtTime(e.logged_at)}</span></div>`;
    feed.appendChild(item);
  });
}

function resetDrillToToday(){
  let todayISO=new Date().toISOString().split("T")[0];
  document.getElementById("drill-date-picker").value=todayISO;
  loadDrillActivity();
}

function closeDrill(){
  document.getElementById("mgr-overview").style.display="";
  document.getElementById("mgr-drill").style.display="none";
  renderManagerDashboard();
}

// ── Store search & filter ───────────────────────────────────────────────────
function filterStoreCards(){
  let q=(document.getElementById("mgr-search-input").value||"").trim().toLowerCase();
  let cards=document.querySelectorAll("#store-cards .store-card");
  let visible=0;
  cards.forEach(card=>{
    let num=card.querySelector(".store-card-num").textContent.toLowerCase();
    let show=!q||num.includes(q);
    card.style.display=show?"":"none";
    if(show)visible++;
  });
  document.getElementById("mgr-clear-btn").style.display=q?"":"none";
  document.getElementById("mgr-cards-label").textContent=q
    ?"Showing "+visible+" matching store"+(visible!==1?"s":"")+" — click to drill in"
    :"All locations — click any store to drill in";
}

function clearSearch(){
  document.getElementById("mgr-search-input").value="";
  filterStoreCards();
  document.getElementById("search-banner").classList.remove("show");
  document.getElementById("mgr-clear-btn").style.display="none";
}

async function searchStoreHistory(){
  let q=(document.getElementById("mgr-search-input").value||"").trim();
  if(!q)return;
  let searchBanner=document.getElementById("search-banner");
  searchBanner.textContent="Loading history for Store "+q+"...";
  searchBanner.classList.add("show");
  document.getElementById("mgr-clear-btn").style.display="";
  openHistoryPanel(q);
}

// ── Store history panel ─────────────────────────────────────────────────────
let historyStoreNum=null;

function openHistoryPanel(storeNum){
  historyStoreNum=storeNum;
  document.getElementById("mgr-history").style.display="";
  document.getElementById("history-title").textContent="Store "+storeNum+" — activity history";
  document.getElementById("search-banner").textContent="Showing history for Store "+storeNum;
  document.getElementById("search-banner").classList.add("show");
  // Default to this week
  setHistoryToWeek();
}

function closeHistory(){
  document.getElementById("mgr-history").style.display="none";
  document.getElementById("search-banner").classList.remove("show");
  historyStoreNum=null;
}

function setHistoryToWeek(){
  let now=new Date();
  let sun=new Date(now);sun.setDate(now.getDate()-now.getDay());
  let sat=new Date(sun);sat.setDate(sun.getDate()+6);
  document.getElementById("hist-from").value=sun.toISOString().split("T")[0];
  document.getElementById("hist-to").value=sat.toISOString().split("T")[0];
  loadStoreHistory();
}

function setHistoryToMonth(){
  let now=new Date();
  let first=new Date(now.getFullYear(),now.getMonth(),1);
  let last=new Date(now.getFullYear(),now.getMonth()+1,0);
  document.getElementById("hist-from").value=first.toISOString().split("T")[0];
  document.getElementById("hist-to").value=last.toISOString().split("T")[0];
  loadStoreHistory();
}

async function loadStoreHistory(){
  if(!historyStoreNum)return;
  let from=document.getElementById("hist-from").value;
  let to=document.getElementById("hist-to").value;
  let feed=document.getElementById("history-feed");
  feed.innerHTML='<div class="empty-msg">Loading...</div>';
  if(!from||!to){feed.innerHTML='<div class="empty-msg">Please select a date range</div>';return;}

  let start=from+"T00:00:00.000Z";
  let end=to+"T23:59:59.999Z";
  let params="store_id=eq."+encodeURIComponent(historyStoreNum)
    +"&action=eq.checked"
    +"&order=logged_at.desc&limit=200"
    +"&logged_at=gte."+encodeURIComponent(start)
    +"&logged_at=lte."+encodeURIComponent(end);

  let rows=await sbGet("checklist_log",params);
  feed.innerHTML="";

  if(!Array.isArray(rows)||!rows.length){
    document.getElementById("hist-total").textContent=0;
    document.getElementById("hist-staff").textContent=0;
    document.getElementById("hist-days").textContent=0;
    feed.innerHTML='<div class="empty-msg">No activity found for this period</div>';
    return;
  }

  // Summary stats
  let uniqueStaff=new Set(rows.map(r=>r.who)).size;
  let uniqueDays=new Set(rows.map(r=>r.logged_at.split("T")[0])).size;
  document.getElementById("hist-total").textContent=rows.length;
  document.getElementById("hist-staff").textContent=uniqueStaff;
  document.getElementById("hist-days").textContent=uniqueDays;

  // Group by date
  let byDate={};
  rows.forEach(r=>{
    let d=r.logged_at.split("T")[0];
    if(!byDate[d])byDate[d]=[];
    byDate[d].push(r);
  });

  Object.keys(byDate).sort().reverse().forEach(date=>{
    let d=new Date(date+"T12:00:00");
    let dayHdr=document.createElement("div");
    dayHdr.style.cssText="padding:6px 14px;font-size:11px;font-weight:500;color:#fff;background:#444441;letter-spacing:.04em;";
    dayHdr.textContent=d.toLocaleDateString([],{weekday:"long",month:"long",day:"numeric",year:"numeric"})+" — "+byDate[date].length+" task"+(byDate[date].length!==1?"s":"")+" completed";
    feed.appendChild(dayHdr);
    byDate[date].forEach(e=>{
      let item=document.createElement("div");item.className="activity-item";
      item.innerHTML=`<div class="activity-dot c"></div><div class="activity-text"><strong style="font-weight:500">${e.who}</strong> completed <em style="font-style:normal">${e.task_name}</em><span>${fmtTime(e.logged_at)}</span></div>`;
      feed.appendChild(item);
    });
  });
}

function launchConfetti(){
  let canvas=document.getElementById("confetti-canvas");
  let ctx=canvas.getContext("2d");
  canvas.width=window.innerWidth;canvas.height=window.innerHeight;
  let colors=["#534AB7","#1D9E75","#BA7517","#D85A30","#AFA9EC","#5DCAA5","#FAC775","#F0997B","#CECBF6","#9FE1CB"];
  let pieces=Array.from({length:180},()=>({x:Math.random()*canvas.width,y:-10-Math.random()*120,w:7+Math.random()*8,h:4+Math.random()*5,color:colors[Math.floor(Math.random()*colors.length)],rot:Math.random()*Math.PI*2,vx:(Math.random()-.5)*4,vy:2.5+Math.random()*3.5,vr:(Math.random()-.5)*.18,shape:Math.random()>.5?"rect":"circle"}));
  let frame=0;
  function draw(){ctx.clearRect(0,0,canvas.width,canvas.height);pieces.forEach(p=>{ctx.save();ctx.translate(p.x,p.y);ctx.rotate(p.rot);ctx.fillStyle=p.color;if(p.shape==="circle"){ctx.beginPath();ctx.arc(0,0,p.w/2,0,Math.PI*2);ctx.fill();}else{ctx.fillRect(-p.w/2,-p.h/2,p.w,p.h);}ctx.restore();p.x+=p.vx;p.y+=p.vy;p.rot+=p.vr;p.vy+=.05;if(p.y>canvas.height+20){p.y=-15;p.x=Math.random()*canvas.width;p.vy=2.5+Math.random()*3;}});frame++;if(frame<300)requestAnimationFrame(draw);else ctx.clearRect(0,0,canvas.width,canvas.height);}
  draw();
}
</script>
</body>
</html>
