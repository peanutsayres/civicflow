<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>CivicFlow | Township Workflow Automation for Microsoft 365</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;600;700&family=Inter:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
  <style>
    :root{
      --navy:#0f1c2e;--navy-2:#162640;--steel:#29425f;--accent:#3d7ebf;--accent-2:#5a9fd4;
      --warm:#c8a96e;--ink:#1c2b3a;--muted:#5d7083;--bg:#edf3f8;--card:#ffffff;
      --rule:rgba(27,54,85,.12);--green:#1f7a49;--green-bg:#e9f6ef;
      --amber:#a96a08;--amber-bg:#fff3de;--red:#b73a3a;--red-bg:#fdeaea;
      --blue-bg:#ebf2fc;--shadow:0 18px 50px rgba(15,28,46,.08);
      --display:'Playfair Display',serif;--body:'Inter',sans-serif;--mono:'IBM Plex Mono',monospace;
      --max:1180px;--gutter:clamp(20px,4vw,44px);--radius:18px
    }
    *{box-sizing:border-box;margin:0;padding:0}
    html{scroll-behavior:smooth}
    body{font-family:var(--body);background:var(--bg);color:var(--ink);line-height:1.6;-webkit-font-smoothing:antialiased}
    a{text-decoration:none;color:inherit}
    .wrap{max-width:var(--max);margin:0 auto;padding:0 var(--gutter)}
    .mono{font-family:var(--mono);text-transform:uppercase;letter-spacing:.14em;font-size:.72rem}
    .section{padding:84px 0}.section-tight{padding:56px 0}
    .eyebrow{color:var(--accent);margin-bottom:14px;font-weight:500}
    h1{font-family:var(--display);font-size:clamp(2.5rem,5vw,4.7rem);line-height:1.05;color:#fff;letter-spacing:-.02em;margin:0 0 14px}
    h2{font-family:var(--display);font-size:clamp(1.9rem,3vw,3rem);line-height:1.1;color:var(--navy);letter-spacing:-.02em;margin:0 0 14px}
    h3{font-size:1.05rem;color:var(--navy);margin:0 0 10px}
    h4{font-size:1rem;color:var(--navy);margin:0 0 8px}
    p{margin:0 0 16px;color:var(--muted);font-size:1.02rem}
    p:last-child{margin-bottom:0}

    /* NAV */
    .topbar{position:sticky;top:0;z-index:10;backdrop-filter:blur(12px);background:rgba(15,28,46,.9);border-bottom:1px solid rgba(255,255,255,.08)}
    .topbar-inner{display:flex;align-items:center;justify-content:space-between;gap:16px;padding:14px var(--gutter);max-width:var(--max);margin:0 auto}
    .brand img{height:44px;width:auto;display:block}
    .nav-cta{display:flex;gap:10px;align-items:center}
    .btn{display:inline-flex;align-items:center;justify-content:center;gap:8px;padding:12px 22px;border-radius:999px;font-weight:600;font-size:.95rem;transition:.2s ease;border:1px solid transparent;cursor:pointer;font-family:var(--body)}
    .btn-primary{background:var(--accent);color:#fff;box-shadow:0 10px 24px rgba(61,126,191,.25)}
    .btn-primary:hover{background:var(--accent-2)}
    .btn-secondary{background:transparent;color:#fff;border-color:rgba(255,255,255,.2)}
    .btn-secondary:hover{background:rgba(255,255,255,.08)}
    .btn-lg{padding:16px 32px;font-size:1rem}

    /* HERO */
    .hero{background:radial-gradient(circle at top right,rgba(90,159,212,.2),transparent 30%),linear-gradient(135deg,var(--navy),var(--navy-2));padding:80px 0 68px;overflow:hidden}
    .hero-grid{display:grid;grid-template-columns:1.1fr .9fr;gap:48px;align-items:center}
    .hero-copy p{color:rgba(255,255,255,.72);font-size:1.08rem;max-width:620px}
    .hero-badges{display:flex;flex-wrap:wrap;gap:10px;margin:22px 0 28px}
    .pill{background:rgba(255,255,255,.08);color:#dce8f5;border:1px solid rgba(255,255,255,.12);padding:9px 14px;border-radius:999px;font-size:.88rem;font-weight:500}
    .hero-actions{display:flex;gap:12px;flex-wrap:wrap}
    .hero-card{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.1);border-radius:24px;padding:22px;box-shadow:var(--shadow)}
    .hero-stat-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:14px;margin-bottom:16px}
    .stat{background:rgba(255,255,255,.94);border-radius:18px;padding:18px}
    .stat strong{display:block;font-size:1.6rem;color:var(--navy);line-height:1.1;margin-bottom:4px}
    .stat span{font-size:.86rem;color:var(--muted)}
    .mini-note{background:rgba(255,255,255,.94);border-radius:18px;padding:18px}
    .mini-note p{color:var(--muted);font-size:.92rem}

    /* ORIGIN STORY */
    .origin{background:linear-gradient(135deg,var(--navy),var(--steel));padding:72px 0}
    .origin-grid{display:grid;grid-template-columns:1fr 1fr;gap:56px;align-items:center}
    .origin-left h2{color:#fff;margin-bottom:16px}
    .origin-left p{color:rgba(255,255,255,.7);font-size:1rem;line-height:1.8;margin-bottom:16px}
    .origin-quote{border-left:3px solid var(--warm);padding:16px 20px;margin:24px 0}
    .origin-quote p{color:rgba(255,255,255,.9);font-family:var(--display);font-size:1.1rem;font-style:italic;line-height:1.6}
    .origin-stats{display:grid;grid-template-columns:repeat(3,1fr);gap:16px}
    .origin-stat{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.1);border-radius:18px;padding:22px;text-align:center}
    .origin-stat strong{display:block;font-size:2rem;color:#fff;font-family:var(--display);line-height:1;margin-bottom:6px}
    .origin-stat span{font-size:.82rem;color:rgba(255,255,255,.55);line-height:1.4}

    /* CARDS & LISTS */
    .problem-grid,.solution-grid,.result-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:24px}
    .card{background:var(--card);border:1px solid var(--rule);border-radius:var(--radius);padding:28px;box-shadow:var(--shadow)}
    .list{display:grid;gap:12px;margin-top:16px}
    .list-item{display:flex;gap:12px;align-items:flex-start;color:var(--ink);font-size:.98rem}
    .list-item span:first-child{width:28px;height:28px;flex:0 0 28px;border-radius:50%;display:grid;place-items:center;font-size:.88rem;font-weight:700}
    .bad span:first-child{background:var(--red-bg);color:var(--red)}
    .good span:first-child{background:var(--green-bg);color:var(--green)}
    .problem-punch{margin-top:20px;padding:18px 20px;border-radius:16px;background:var(--navy);color:#fff}
    .problem-punch strong{display:block;font-size:1.08rem;margin-bottom:4px}
    .problem-punch span{color:rgba(255,255,255,.68);font-size:.95rem}

    /* FEATURE STRIP */
    .feature-strip{background:linear-gradient(135deg,var(--navy),var(--steel));border-radius:24px;padding:28px;color:#fff;border:1px solid rgba(255,255,255,.08)}
    .feature-strip p{color:rgba(255,255,255,.7)}
    .feature-strip-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:14px;margin-top:20px}
    .feature-box{background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.1);padding:18px;border-radius:16px}
    .feature-box strong{display:block;color:#fff;margin-bottom:6px;font-size:.98rem}
    .feature-box span{font-size:.9rem;color:rgba(255,255,255,.65)}

    /* STEPS */
    .steps{display:grid;grid-template-columns:repeat(6,1fr);gap:12px;margin-top:28px}
    .step{background:var(--card);border:1px solid var(--rule);border-radius:18px;padding:20px;box-shadow:var(--shadow)}
    .step-num{font-family:var(--mono);color:var(--accent);font-size:.78rem;margin-bottom:10px}
    .step p{font-size:.9rem;color:var(--muted);margin-top:8px}

    /* BANNER */
    .banner{background:linear-gradient(135deg,#fff,#f6f9fd);border:1px solid var(--rule);border-radius:24px;padding:32px;display:grid;grid-template-columns:1.1fr .9fr;gap:28px;align-items:center;box-shadow:var(--shadow)}
    .kpis{display:grid;grid-template-columns:repeat(2,1fr);gap:14px}
    .kpi{background:var(--blue-bg);border:1px solid rgba(61,126,191,.12);border-radius:18px;padding:18px}
    .kpi strong{display:block;font-size:1.05rem;color:var(--navy);margin-bottom:4px}
    .kpi span{font-size:.88rem;color:var(--muted)}

    /* DEMO */
    .demo-shell{background:var(--navy);border-radius:24px;padding:18px;border:1px solid rgba(255,255,255,.08);box-shadow:var(--shadow)}
    .browser-bar{display:flex;gap:8px;align-items:center;padding:8px 8px 16px}
    .browser-dot{width:11px;height:11px;border-radius:50%;background:#8797aa}
    .browser-view{background:#f9fbfd;border-radius:18px;overflow:hidden}
    .demo-tabs{display:flex;gap:10px;flex-wrap:wrap;padding:18px;background:#f4f7fb;border-bottom:1px solid var(--rule)}
    .demo-tab{border:none;background:#fff;border:1px solid var(--rule);padding:10px 16px;border-radius:999px;cursor:pointer;font-weight:600;color:var(--muted);font-family:var(--body);font-size:.9rem;transition:.2s}
    .demo-tab.active{background:var(--accent);color:#fff;border-color:var(--accent)}
    .demo-panel{display:none;padding:24px}
    .demo-panel.active{display:block}
    .demo-process{display:grid;grid-template-columns:repeat(7,1fr);gap:8px;margin-bottom:20px}
    .demo-stage{background:#fff;border:1px solid var(--rule);border-radius:14px;padding:12px;text-align:center;font-size:.78rem;color:var(--muted)}
    .demo-stage strong{display:block;color:var(--navy);font-size:.88rem;margin-bottom:4px}
    .demo-stage.done{background:var(--green-bg);border-color:rgba(31,122,73,.2)}
    .demo-stage.done strong{color:var(--green)}
    .demo-stage.active-s{background:var(--blue-bg);border-color:rgba(61,126,191,.2)}
    .demo-stage.active-s strong{color:#2359a9}
    .demo-layout{display:grid;grid-template-columns:1.35fr .85fr;gap:18px}
    .demo-card{background:#fff;border:1px solid var(--rule);border-radius:18px;padding:20px}
    .demo-meta{display:flex;flex-wrap:wrap;gap:8px;margin:10px 0 14px}
    .demo-badge{font-size:.77rem;padding:6px 12px;border-radius:999px;font-weight:600}
    .b-blue{background:var(--blue-bg);color:#2359a9}
    .b-amber{background:var(--amber-bg);color:var(--amber)}
    .b-green{background:var(--green-bg);color:var(--green)}
    .b-red{background:var(--red-bg);color:var(--red)}
    .demo-copy{font-size:.93rem;color:var(--muted);line-height:1.7}
    .logic{background:#f6f8fb;border:1px solid var(--rule);border-radius:14px;padding:14px;font-family:var(--mono);font-size:.74rem;color:var(--steel);line-height:1.8;margin-top:14px}
    .timeline{display:grid;gap:10px;margin-top:14px}
    .timeline-row{display:flex;gap:10px;align-items:flex-start;font-size:.87rem;color:var(--muted)}
    .dot{width:10px;height:10px;border-radius:50%;margin-top:5px;flex-shrink:0;background:var(--accent)}
    .dot-red{background:var(--red)}
    .dot-green{background:var(--green)}
    .ai-note{background:linear-gradient(135deg,#f8f0ff,#f0f4ff);border:1px solid #d8c8f0;border-radius:14px;padding:14px;margin-top:14px;font-size:.85rem;color:#6040a0;line-height:1.6}
    .ai-note strong{display:block;margin-bottom:4px;font-size:.72rem;text-transform:uppercase;letter-spacing:.1em}

    /* CTA */
    .cta-block{background:linear-gradient(135deg,var(--navy),var(--steel));border-radius:28px;padding:52px 40px;color:#fff;text-align:center;box-shadow:var(--shadow)}
    .cta-block h2{color:#fff;margin-bottom:12px}
    .cta-block p{color:rgba(255,255,255,.72);max-width:580px;margin:0 auto 8px;font-size:1rem}
    .cta-sub{font-size:.9rem !important;color:rgba(255,255,255,.5) !important;margin-bottom:28px !important}
    .cta-notes{display:flex;justify-content:center;gap:20px;flex-wrap:wrap;margin-top:18px;color:rgba(255,255,255,.5);font-size:.88rem}
    .cta-notes span{display:flex;align-items:center;gap:6px}

    /* FOOTER */
    footer{padding:32px 0 48px;text-align:center;color:var(--muted);font-size:.9rem}

    /* MOBILE CTA */
    .mobile-cta{position:fixed;left:0;right:0;bottom:0;z-index:20;display:none;padding:12px 16px calc(12px + env(safe-area-inset-bottom));background:rgba(15,28,46,.96);backdrop-filter:blur(10px);border-top:1px solid rgba(255,255,255,.08)}
    .mobile-cta .btn{width:100%}

    /* RESPONSIVE */
    @media(max-width:1080px){
      .hero-grid,.banner,.demo-layout,.problem-grid,.solution-grid,.result-grid,.origin-grid{grid-template-columns:1fr}
      .steps{grid-template-columns:repeat(3,1fr)}
      .feature-strip-grid{grid-template-columns:repeat(2,1fr)}
      .demo-process{grid-template-columns:repeat(4,1fr)}
      .origin-grid{gap:36px}
    }
    @media(max-width:720px){
      .nav-cta .btn-secondary{display:none}
      .topbar{position:relative}
      .hero{padding:40px 0 44px}
      .hero-grid{gap:24px}
      .steps,.feature-strip-grid,.hero-stat-grid,.kpis{grid-template-columns:1fr 1fr}
      .demo-process{display:flex;overflow-x:auto;gap:10px;padding-bottom:8px;scroll-snap-type:x proximity}
      .demo-stage{min-width:130px;scroll-snap-align:start}
      .demo-tabs{overflow-x:auto;flex-wrap:nowrap;padding-bottom:14px}
      .demo-tab{white-space:nowrap;min-height:44px}
      .origin-stats{grid-template-columns:1fr 1fr}
    }
    @media(max-width:560px){
      .topbar-inner{flex-direction:column;align-items:stretch}
      .brand{justify-content:center}
      .nav-cta{width:100%}
      .steps,.feature-strip-grid,.hero-stat-grid,.kpis,.origin-stats{grid-template-columns:1fr}
      .hero-actions{flex-direction:column;align-items:stretch}
      .btn{width:100%;min-height:48px}
      .section{padding:56px 0}
      .section-tight{padding:40px 0}
      .card,.cta-block,.feature-strip,.banner,.hero-card{padding:20px}
      .problem-grid,.solution-grid,.result-grid,.demo-layout{grid-template-columns:1fr}
      .demo-panel{padding:16px}
      .cta-block{padding:36px 20px 96px}
      .mobile-cta{display:flex}
    }
  </style>
</head>
<body>

<!-- NAV -->
<header class="topbar">
  <div class="topbar-inner">
    <div class="brand">
      <img src="civicflow-logo.jpg" alt="CivicFlow by Avalon Systems">
    </div>
    <div class="nav-cta">
      <a class="btn btn-secondary" href="#demo">See Demo</a>
      <a class="btn btn-primary" href="#cta">Get Your Workflow Mapped</a>
    </div>
  </div>
</header>

<!-- HERO -->
<section class="hero">
  <div class="wrap hero-grid">
    <div class="hero-copy">
      <div class="eyebrow mono">Township workflow automation · Microsoft 365</div>
      <h1>Nothing falls through the cracks in your township anymore.</h1>
      <p>CivicFlow turns resident requests into tracked, assigned, and resolved cases — using the Microsoft 365 tools your team already has. No new software. No long rollout. Live in 14 days.</p>
      <div class="hero-badges">
        <div class="pill">No new software</div>
        <div class="pill">Built on Microsoft 365</div>
        <div class="pill">Live in 14 days</div>
        <div class="pill">AI assists. Humans decide.</div>
      </div>
      <div class="hero-actions">
        <a class="btn btn-primary btn-lg" href="#cta">See This In Your Township</a>
        <a class="btn btn-secondary btn-lg" href="#demo">Watch How It Works</a>
      </div>
    </div>
    <div class="hero-card">
      <div class="hero-stat-grid">
        <div class="stat"><strong>100%</strong><span>of requests tracked with a case number</span></div>
        <div class="stat"><strong>&lt; 1 day</strong><span>same-day acknowledgment becomes standard</span></div>
        <div class="stat"><strong>14 days</strong><span>from kickoff to live workflow</span></div>
        <div class="stat"><strong>0 guesswork</strong><span>clear ownership, follow-up, and escalation</span></div>
      </div>
      <div class="mini-note">
        <div class="eyebrow mono" style="color:var(--accent);margin-bottom:8px">Designed for small township teams</div>
        <p>Built for township administrators, clerks, trustees, and local government offices still handling resident requests through phone calls, email, paper forms, or scattered inboxes.</p>
      </div>
    </div>
  </div>
</section>

<!-- ORIGIN STORY -->
<section class="origin">
  <div class="wrap origin-grid">
    <div class="origin-left">
      <div class="eyebrow mono" style="color:#9fd0ff">Built from real operational experience</div>
      <h2>We didn't build this from the outside.</h2>
      <p>CivicFlow grew out of nine years of operational work inside The Avalon Foundation — a working organization where broken intake processes had real consequences for real people.</p>
      <p>We didn't study this problem as consultants. We solved it under pressure with small teams, limited resources, and no margin for error. We know what breaks because we were the ones who had to fix it when it did.</p>
      <div class="origin-quote">
        <p>We build for organizations where a dropped request isn't just an inconvenience — it's a failure of public trust. That's not a positioning statement. It's where we came from.</p>
      </div>
      <p style="color:rgba(255,255,255,.5);font-size:.88rem">CivicFlow is a product of Avalon Systems · Northwest Ohio</p>
    </div>
    <div>
      <div class="origin-stats">
        <div class="origin-stat">
          <strong>9</strong>
          <span>Years of operational practice building and breaking real intake systems</span>
        </div>
        <div class="origin-stat">
          <strong>14</strong>
          <span>Days from kickoff to a fully live workflow inside your Microsoft 365 tenant</span>
        </div>
        <div class="origin-stat">
          <strong>0</strong>
          <span>New platforms required — everything runs inside what you already pay for</span>
        </div>
      </div>
      <div style="background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.1);border-radius:18px;padding:22px;margin-top:16px">
        <div class="eyebrow mono" style="color:#9fd0ff;margin-bottom:12px">Why townships specifically</div>
        <p style="color:rgba(255,255,255,.65);font-size:.93rem;line-height:1.8">Small township offices handle the same volume and complexity as larger departments — with a fraction of the staff. When the process lives in one person's head, turnover becomes a crisis. CivicFlow makes the process survive the people, not the other way around.</p>
      </div>
    </div>
  </div>
</section>

<!-- PROBLEM -->
<section class="section">
  <div class="wrap">
    <div class="problem-grid">
      <div>
        <div class="eyebrow mono">The problem</div>
        <h2>This is how most township requests are handled today.</h2>
        <p>Calls become sticky notes. Emails sit in a shared inbox. Paper forms land on a desk. Residents call back and staff have to start over because there is no case number, no ownership, and no audit trail.</p>
        <p>It's not a staffing problem. It's not a motivation problem. The process was never designed — it just accumulated.</p>
        <div class="problem-punch">
          <strong>When a resident calls back, you start over.</strong>
          <span>That is the operational failure CivicFlow removes.</span>
        </div>
      </div>
      <div class="card">
        <div class="eyebrow mono" style="color:var(--red)">What happens today in most townships</div>
        <div class="list">
          <div class="list-item bad"><span>✕</span><span>Calls go to voicemail or get written down by hand</span></div>
          <div class="list-item bad"><span>✕</span><span>Emails sit in a shared inbox with no tracking</span></div>
          <div class="list-item bad"><span>✕</span><span>Paper forms live on a desk — not in a system</span></div>
          <div class="list-item bad"><span>✕</span><span>No case number for residents to reference later</span></div>
          <div class="list-item bad"><span>✕</span><span>No clear owner for who handles what next</span></div>
          <div class="list-item bad"><span>✕</span><span>Follow-up depends entirely on memory</span></div>
          <div class="list-item bad"><span>✕</span><span>When a key person leaves, the process leaves with them</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FEATURE STRIP -->
<section class="section-tight">
  <div class="wrap">
    <div class="feature-strip">
      <div class="eyebrow mono" style="color:#9fd0ff">What CivicFlow changes immediately</div>
      <h2 style="color:#fff;margin-bottom:10px">Every request becomes a tracked case from the moment it is submitted.</h2>
      <p>Residents get acknowledgment. Staff get assignment clarity. Leadership gets visibility. Nothing gets lost.</p>
      <div class="feature-strip-grid">
        <div class="feature-box"><strong>Case ID</strong><span>Every request gets a reference number instantly — residents can follow up without starting over.</span></div>
        <div class="feature-box"><strong>Auto-routing</strong><span>Zoning, roads, code, and admin requests go to the right person automatically.</span></div>
        <div class="feature-box"><strong>Same-day acknowledgment</strong><span>Residents know their request was received before anyone manually touches it.</span></div>
        <div class="feature-box"><strong>Built-in follow-up</strong><span>Escalations fire automatically if a case sits too long — no one has to remember.</span></div>
      </div>
    </div>
  </div>
</section>

<!-- BEFORE / AFTER -->
<section class="section">
  <div class="wrap">
    <div class="solution-grid">
      <div class="card">
        <div class="eyebrow mono">Before CivicFlow</div>
        <h3>Manual, inconsistent, hard to see</h3>
        <div class="list">
          <div class="list-item bad"><span>✕</span><span>No unified intake — requests arrive through five different channels</span></div>
          <div class="list-item bad"><span>✕</span><span>Manual triage based on who saw it first</span></div>
          <div class="list-item bad"><span>✕</span><span>Inconsistent response timing and quality</span></div>
          <div class="list-item bad"><span>✕</span><span>No audit trail when questions arise later</span></div>
          <div class="list-item bad"><span>✕</span><span>No visibility into what's open, pending, or overdue</span></div>
        </div>
      </div>
      <div class="card">
        <div class="eyebrow mono" style="color:var(--green)">With CivicFlow</div>
        <h3>Structured, visible, and in control</h3>
        <div class="list">
          <div class="list-item good"><span>✓</span><span>Every request captured in one place — regardless of how it arrived</span></div>
          <div class="list-item good"><span>✓</span><span>Automatic routing by request type and urgency level</span></div>
          <div class="list-item good"><span>✓</span><span>Consistent responses — same quality whether it's Monday or Friday</span></div>
          <div class="list-item good"><span>✓</span><span>Full case history in SharePoint — permanent audit trail</span></div>
          <div class="list-item good"><span>✓</span><span>Real-time visibility into every open case and its status</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- BANNER -->
<section class="section-tight">
  <div class="wrap">
    <div class="banner">
      <div>
        <div class="eyebrow mono">Fast implementation</div>
        <h2>You do not need new software or a long rollout.</h2>
        <p>CivicFlow runs inside Microsoft 365 using SharePoint, Forms, and Power Automate — tools most township offices already have. We configure the workflow around how your office actually operates. Your staff keeps using familiar tools.</p>
      </div>
      <div class="kpis">
        <div class="kpi"><strong>No new logins</strong><span>Built entirely inside your existing Microsoft 365 environment</span></div>
        <div class="kpi"><strong>14-day install</strong><span>Workflow mapping, configuration, testing, and staff walkthrough</span></div>
        <div class="kpi"><strong>Human review</strong><span>No AI response goes out without staff approval — ever</span></div>
        <div class="kpi"><strong>Your data</strong><span>Everything stays inside your Microsoft 365 tenant — we don't host anything</span></div>
      </div>
    </div>
  </div>
</section>

<!-- DEMO -->
<section class="section" id="demo">
  <div class="wrap">
    <div class="eyebrow mono">Interactive demo</div>
    <h2>See exactly how a real request is handled.</h2>
    <p style="max-width:600px;margin-bottom:32px">Select a request type to walk through intake, routing, AI drafting, and follow-up — end to end. This is the same system that runs in Microsoft 365.</p>
    <div class="demo-shell">
      <div class="browser-bar">
        <div class="browser-dot"></div><div class="browser-dot"></div><div class="browser-dot"></div>
      </div>
      <div class="browser-view">
        <div class="demo-tabs">
          <button class="demo-tab active" data-panel="zoning">🏗 Zoning Permit</button>
          <button class="demo-tab" data-panel="road">🚧 Road Complaint</button>
          <button class="demo-tab" data-panel="code">🏠 Code Complaint</button>
          <button class="demo-tab" data-panel="general">📋 General Concern</button>
        </div>

        <!-- ZONING -->
        <div class="demo-panel active" id="panel-zoning">
          <div class="demo-process">
            <div class="demo-stage done"><strong>✓ 1</strong>Form submitted</div>
            <div class="demo-stage done"><strong>✓ 2</strong>Auto-routed</div>
            <div class="demo-stage done"><strong>✓ 3</strong>Priority set</div>
            <div class="demo-stage active-s"><strong>→ 4</strong>AI draft ready</div>
            <div class="demo-stage"><strong>5</strong>Staff review</div>
            <div class="demo-stage"><strong>6</strong>Response sent</div>
            <div class="demo-stage"><strong>7</strong>Follow-up</div>
          </div>
          <div class="demo-layout">
            <div class="demo-card">
              <div class="eyebrow mono">Case TWP-2026-0178 · April 13, 2026 · 3:42 PM</div>
              <h4>Zoning Permit — Detached Garage Construction</h4>
              <div class="demo-meta">
                <span class="demo-badge b-blue">● New</span>
                <span class="demo-badge b-amber">Medium Priority</span>
                <span class="demo-badge b-green">Zoning Inspector</span>
              </div>
              <p class="demo-copy">Sarah Thompson at 456 County Road 12 requests a zoning permit for a 24×30 detached garage. She has reviewed setback regulations and believes her project complies.</p>
              <div class="logic">IF RequestType = "Zoning Permit"<br>→ WorkflowArea = "Zoning"<br>→ AssignedTo = Zoning Inspector<br>→ Priority = "Soon → Medium"<br>→ FollowUpDue = +7 days</div>
              <div class="ai-note">
                <strong>✦ AI Draft — awaiting staff review</strong>
                Dear Ms. Thompson, thank you for your zoning permit request. We have logged your application under case <strong>TWP-2026-0178</strong>. Our Zoning Inspector will review within 7 business days and contact you regarding next steps and payment.
              </div>
            </div>
            <div class="demo-card">
              <div class="eyebrow mono" style="margin-bottom:12px">Case timeline</div>
              <div class="timeline">
                <div class="timeline-row"><div class="dot"></div><div><strong>3:42 PM</strong> — case created in SharePoint</div></div>
                <div class="timeline-row"><div class="dot"></div><div><strong>3:42 PM</strong> — auto-routed to Zoning Inspector</div></div>
                <div class="timeline-row"><div class="dot"></div><div><strong>3:42 PM</strong> — auto-reply with case ID sent to resident</div></div>
                <div class="timeline-row"><div class="dot dot-green" style="background:var(--green)"></div><div><strong>3:43 PM</strong> — AI draft ready for staff review</div></div>
                <div class="timeline-row"><div class="dot b-amber" style="background:var(--amber)"></div><div><strong>Apr 20</strong> — follow-up reminder scheduled</div></div>
              </div>
              <div style="background:var(--green-bg);border-radius:14px;padding:14px;margin-top:14px;font-size:.85rem;color:var(--green)">
                <strong style="display:block;margin-bottom:4px">Resident auto-reply sent immediately</strong>
                "Your request has been received under case TWP-2026-0178. You will hear from us within 7 business days."
              </div>
            </div>
          </div>
        </div>

        <!-- ROAD -->
        <div class="demo-panel" id="panel-road">
          <div class="demo-process">
            <div class="demo-stage done"><strong>✓ 1</strong>Form submitted</div>
            <div class="demo-stage done"><strong>✓ 2</strong>Urgent route</div>
            <div class="demo-stage done"><strong>✓ 3</strong>High priority</div>
            <div class="demo-stage done"><strong>✓ 4</strong>AI draft ready</div>
            <div class="demo-stage active-s"><strong>→ 5</strong>Staff review</div>
            <div class="demo-stage"><strong>6</strong>Response sent</div>
            <div class="demo-stage"><strong>7</strong>Escalation</div>
          </div>
          <div class="demo-layout">
            <div class="demo-card">
              <div class="eyebrow mono">Case TWP-2026-0179 · April 13, 2026 · 4:11 PM</div>
              <h4>Road Complaint — Pothole Safety Hazard</h4>
              <div class="demo-meta">
                <span class="demo-badge b-red">🔴 Urgent</span>
                <span class="demo-badge b-red">High Priority</span>
                <span class="demo-badge b-green">Roads Supervisor</span>
              </div>
              <p class="demo-copy">Large pothole on eastbound County Road 8, approx. 0.5 miles north of US-20. Worsening after recent rain. Safety hazard — vehicles swerving to avoid it.</p>
              <div class="logic">IF RequestType = "Road/Pothole" AND Urgency = "Urgent"<br>→ WorkflowArea = "Roads/Maintenance"<br>→ Priority = "Urgent → High"<br>→ AssignedTo = Roads Supervisor<br>→ FollowUpDue = +48 hours</div>
              <div class="ai-note">
                <strong>✦ AI Draft — awaiting staff review</strong>
                Dear Mr. Kowalski, thank you for reporting this hazard. Case <strong>TWP-2026-0179</strong> has been flagged urgent and assigned to our Roads crew. The location on County Road 8 will be assessed within 48 hours.
              </div>
            </div>
            <div class="demo-card">
              <div class="eyebrow mono" style="margin-bottom:12px">Case timeline</div>
              <div class="timeline">
                <div class="timeline-row"><div class="dot"></div><div><strong>4:11 PM</strong> — case created, urgent flag detected</div></div>
                <div class="timeline-row"><div class="dot dot-red" style="background:var(--red)"></div><div><strong>4:11 PM</strong> — high priority set, routed to Roads Supervisor</div></div>
                <div class="timeline-row"><div class="dot"></div><div><strong>4:11 PM</strong> — resident auto-reply with case ID sent</div></div>
                <div class="timeline-row"><div class="dot dot-green" style="background:var(--green)"></div><div><strong>4:12 PM</strong> — AI draft ready for staff review</div></div>
                <div class="timeline-row"><div class="dot dot-red" style="background:var(--red)"></div><div><strong>Apr 15</strong> — escalation fires if unresolved</div></div>
              </div>
              <div style="background:var(--red-bg);border-radius:14px;padding:14px;margin-top:14px;font-size:.85rem;color:var(--red)">
                <strong style="display:block;margin-bottom:4px">🚨 48-hour escalation window</strong>
                If Roads Supervisor has not updated the case by April 15 at 4:11 PM, an escalation alert fires automatically to the Township Administrator.
              </div>
            </div>
          </div>
        </div>

        <!-- CODE -->
        <div class="demo-panel" id="panel-code">
          <div class="demo-process">
            <div class="demo-stage done"><strong>✓ 1</strong>Form submitted</div>
            <div class="demo-stage done"><strong>✓ 2</strong>Auto-routed</div>
            <div class="demo-stage done"><strong>✓ 3</strong>Priority set</div>
            <div class="demo-stage done"><strong>✓ 4</strong>AI draft ready</div>
            <div class="demo-stage done"><strong>✓ 5</strong>Staff reviewed</div>
            <div class="demo-stage active-s"><strong>→ 6</strong>Response sent</div>
            <div class="demo-stage"><strong>7</strong>Follow-up</div>
          </div>
          <div class="demo-layout">
            <div class="demo-card">
              <div class="eyebrow mono">Case TWP-2026-0180 · April 14, 2026 · 9:15 AM</div>
              <h4>Code Complaint — Junk Vehicle Storage</h4>
              <div class="demo-meta">
                <span class="demo-badge b-amber">In Review</span>
                <span class="demo-badge b-amber">Medium Priority</span>
                <span class="demo-badge b-green">Code Enforcement</span>
              </div>
              <p class="demo-copy">Three unlicensed, apparently inoperable vehicles parked on front lawn at 812 Township Road 4 for over six months. Resident believes this violates township ordinances.</p>
              <div class="logic">RequestType = "Code Complaint"<br>→ WorkflowArea = "Code Enforcement"<br>→ AssignedTo = Code Enforcement Officer<br>→ Priority = "Soon → Medium"<br>→ FollowUpDue = +7 days</div>
            </div>
            <div class="demo-card">
              <div class="eyebrow mono" style="margin-bottom:12px">Measured outcome</div>
              <h4 style="color:var(--green)">32 minutes — submission to reply</h4>
              <div class="timeline">
                <div class="timeline-row"><div class="dot"></div><div><strong>9:15 AM</strong> — case created, routed to Code Officer</div></div>
                <div class="timeline-row"><div class="dot dot-green" style="background:var(--green)"></div><div><strong>9:16 AM</strong> — AI draft ready for review</div></div>
                <div class="timeline-row"><div class="dot dot-green" style="background:var(--green)"></div><div><strong>9:47 AM</strong> — officer reviews, approves, sends</div></div>
                <div class="timeline-row"><div class="dot"></div><div><strong>Apr 21</strong> — follow-up deadline set</div></div>
              </div>
              <div style="background:var(--green-bg);border-radius:14px;padding:14px;margin-top:14px;font-size:.85rem;color:var(--green)">
                <strong style="display:block;margin-bottom:4px">✓ Response sent in 32 minutes</strong>
                Staff reviewed the AI draft, confirmed it was accurate, approved — and sent. The workflow was already staged before anyone opened the case.
              </div>
            </div>
          </div>
        </div>

        <!-- GENERAL -->
        <div class="demo-panel" id="panel-general">
          <div class="demo-process">
            <div class="demo-stage done"><strong>✓ 1</strong>Form submitted</div>
            <div class="demo-stage done"><strong>✓ 2</strong>Auto-routed</div>
            <div class="demo-stage done"><strong>✓ 3</strong>Priority set</div>
            <div class="demo-stage active-s"><strong>→ 4</strong>AI draft ready</div>
            <div class="demo-stage"><strong>5</strong>Staff review</div>
            <div class="demo-stage"><strong>6</strong>Response sent</div>
            <div class="demo-stage"><strong>7</strong>Follow-up</div>
          </div>
          <div class="demo-layout">
            <div class="demo-card">
              <div class="eyebrow mono">Case TWP-2026-0181 · April 14, 2026 · 11:02 AM</div>
              <h4>General Concern — Drainage Ditch Overflow</h4>
              <div class="demo-meta">
                <span class="demo-badge b-blue">● New</span>
                <span class="demo-badge b-amber">Medium Priority</span>
                <span class="demo-badge b-green">Township Administrator</span>
              </div>
              <p class="demo-copy">Drainage ditch along north side of 78 Township Road 11 overflowing onto lawn after heavy rain — third time this spring. Resident unsure whether this is a township or property-owner responsibility.</p>
              <div class="logic">RequestType = "General Concern"<br>→ WorkflowArea = "General Admin"<br>→ AssignedTo = Township Administrator<br>→ FollowUpDue = +7 days</div>
              <div class="ai-note">
                <strong>✦ AI Draft — awaiting staff review</strong>
                Dear Mr. and Mrs. Meyers, thank you for reaching out. We have logged your drainage concern under case <strong>TWP-2026-0181</strong>. Our office will review and be in touch within 7 business days regarding responsibility and next steps.
              </div>
            </div>
            <div class="demo-card">
              <div class="eyebrow mono" style="margin-bottom:12px">Why this matters</div>
              <h4>General requests stop disappearing.</h4>
              <p class="demo-copy">This is often the biggest hidden gap. Requests that don't fit a narrow department category used to fall into a void. Now they have a case number, an owner, and a deadline.</p>
              <div class="timeline">
                <div class="timeline-row"><div class="dot"></div><div><strong>11:02 AM</strong> — case created</div></div>
                <div class="timeline-row"><div class="dot"></div><div><strong>11:02 AM</strong> — routed to Township Administrator</div></div>
                <div class="timeline-row"><div class="dot"></div><div><strong>11:02 AM</strong> — resident auto-reply with case ID sent</div></div>
                <div class="timeline-row"><div class="dot dot-green" style="background:var(--green)"></div><div><strong>11:03 AM</strong> — AI draft ready for review</div></div>
                <div class="timeline-row"><div class="dot b-amber" style="background:var(--amber)"></div><div><strong>Apr 21</strong> — follow-up deadline</div></div>
              </div>
            </div>
          </div>
        </div>

      </div>
    </div>
  </div>
</section>

<!-- HOW IT WORKS -->
<section class="section">
  <div class="wrap">
    <div class="eyebrow mono">How it works</div>
    <h2>What happens when a resident submits a request.</h2>
    <p style="max-width:560px">Simple enough for non-technical staff. Structured enough that nothing falls through the cracks regardless of who is in the office that day.</p>
    <div class="steps">
      <div class="step"><div class="step-num">01</div><h3>Resident submits</h3><p>Online form, phone-assisted entry, or walk-in — captured in a consistent format every time.</p></div>
      <div class="step"><div class="step-num">02</div><h3>Case is created</h3><p>The request receives a reference number instantly inside Microsoft 365. Resident gets an auto-reply.</p></div>
      <div class="step"><div class="step-num">03</div><h3>Auto-routing runs</h3><p>Zoning, roads, code, and admin cases go to the right person automatically based on request type.</p></div>
      <div class="step"><div class="step-num">04</div><h3>Priority is set</h3><p>Urgent requests follow a 48-hour path. Routine requests follow a standard 7-day timeline.</p></div>
      <div class="step"><div class="step-num">05</div><h3>AI drafts response</h3><p>A staff-ready draft is prepared. Nothing goes out until a human reviews and approves it.</p></div>
      <div class="step"><div class="step-num">06</div><h3>Follow-up is scheduled</h3><p>If no action by the deadline, an escalation reminder fires automatically. Nothing gets forgotten.</p></div>
    </div>
  </div>
</section>

<!-- RESULTS + RISK -->
<section class="section-tight">
  <div class="wrap">
    <div class="result-grid">
      <div class="card">
        <div class="eyebrow mono">What changes immediately</div>
        <h3>Outcomes your township can feel within the first week</h3>
        <div class="list">
          <div class="list-item good"><span>✓</span><span>100% of requests tracked — nothing accepted without a case number</span></div>
          <div class="list-item good"><span>✓</span><span>Same-day acknowledgment becomes the default, not the exception</span></div>
          <div class="list-item good"><span>✓</span><span>Clear ownership on every case — no more "who has that?"</span></div>
          <div class="list-item good"><span>✓</span><span>Response times drop — often to the same hour for routine requests</span></div>
          <div class="list-item good"><span>✓</span><span>Follow-ups happen automatically — staff memory is no longer the system</span></div>
          <div class="list-item good"><span>✓</span><span>The process survives staff changes — it lives in the system, not a person</span></div>
        </div>
      </div>
      <div class="card">
        <div class="eyebrow mono">Risk removal</div>
        <h3>This is not a risky change for your office.</h3>
        <div class="list">
          <div class="list-item good"><span>✓</span><span>No data leaves Microsoft 365 — ever</span></div>
          <div class="list-item good"><span>✓</span><span>No AI message goes out without staff review and approval</span></div>
          <div class="list-item good"><span>✓</span><span>No replacement of staff judgment — CivicFlow supports it</span></div>
          <div class="list-item good"><span>✓</span><span>No major disruption to go live — staff keep using familiar tools</span></div>
          <div class="list-item good"><span>✓</span><span>No new software platform to buy, train on, or maintain</span></div>
          <div class="list-item good"><span>✓</span><span>No long contract — cancel with 30 days notice</span></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CTA -->
<section class="section" id="cta">
  <div class="wrap">
    <div class="cta-block">
      <div class="eyebrow mono" style="color:#9fd0ff;margin-bottom:16px">Get started</div>
      <h2>See what this would look like in your township.</h2>
      <p>We will map your current intake process, show exactly where requests are slipping, and walk you through how CivicFlow would work in your Microsoft 365 environment.</p>
      <p class="cta-sub">No commitment required. Takes about 15–20 minutes. We assess fit before proposing anything.</p>
      <a class="btn btn-primary btn-lg" href="https://forms.cloud.microsoft/r/MGmkKFT8v0" target="_blank" rel="noopener noreferrer">Get Your Workflow Mapped →</a>
      <div class="cta-notes">
        <span>✓ No commitment</span>
        <span>✓ 15–20 minutes</span>
        <span>✓ We assess fit first</span>
        <span>✓ We respond within one business day</span>
      </div>
    </div>
  </div>
</section>

<footer>
  <div class="wrap">
    CivicFlow by Avalon Systems · Built for township administrators, clerks, trustees, and small local government teams · <a href="https://civicflow.us" style="color:var(--accent)">civicflow.us</a>
  </div>
</footer>

<div class="mobile-cta">
  <a class="btn btn-primary" href="https://forms.cloud.microsoft/r/MGmkKFT8v0" target="_blank">Get Your Workflow Mapped →</a>
</div>

<script>
  const tabs = document.querySelectorAll('.demo-tab');
  const panels = document.querySelectorAll('.demo-panel');
  tabs.forEach(tab => {
    tab.addEventListener('click', () => {
      tabs.forEach(t => t.classList.remove('active'));
      panels.forEach(p => p.classList.remove('active'));
      tab.classList.add('active');
      document.getElementById('panel-' + tab.dataset.panel).classList.add('active');
    });
  });
</script>
</body>
</html>
