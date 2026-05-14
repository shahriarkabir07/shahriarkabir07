<!DOCTYPE html>
<html>
<head>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;400;500;600;700&family=Space+Grotesk:wght@300;400;500;600;700&display=swap');

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: #0a0a0f;
    color: #e2e8f0;
    font-family: 'Space Grotesk', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  .bg-grid {
    position: fixed;
    inset: 0;
    background-image: 
      linear-gradient(rgba(0,247,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,247,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 40px 24px;
    position: relative;
    z-index: 1;
  }

  .hero {
    text-align: center;
    padding: 60px 0 40px;
    position: relative;
  }

  .hero-badge {
    display: inline-block;
    background: rgba(0,247,255,0.08);
    border: 1px solid rgba(0,247,255,0.2);
    color: #00f7ff;
    font-family: 'Fira Code', monospace;
    font-size: 12px;
    padding: 6px 16px;
    border-radius: 20px;
    margin-bottom: 24px;
    letter-spacing: 2px;
  }

  .hero-name-glow {
    font-family: 'Fira Code', monospace;
    font-size: clamp(36px, 6vw, 64px);
    font-weight: 700;
    color: #0a1628;
    line-height: 1.1;
    margin-bottom: 8px;
    text-shadow: 
      0 0 30px rgba(0,80,255,0.5),
      0 0 60px rgba(0,40,200,0.3),
      0 2px 4px rgba(0,0,0,0.8);
    -webkit-text-stroke: 0.5px rgba(0,100,255,0.3);
  }

  .hero-title {
    font-size: 15px;
    color: #64748b;
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 16px;
    font-family: 'Fira Code', monospace;
  }

  .hero-desc {
    font-size: 16px;
    color: #94a3b8;
    max-width: 500px;
    margin: 0 auto 32px;
    line-height: 1.7;
  }

  .hero-desc span { color: #00f7ff; font-weight: 500; }

  .cursor-blink {
    display: inline-block;
    width: 3px;
    height: 1.1em;
    background: #00f7ff;
    margin-left: 4px;
    vertical-align: middle;
    animation: blink 1s step-end infinite;
    border-radius: 1px;
  }

  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0} }

  .socials {
    display: flex;
    gap: 12px;
    justify-content: center;
    flex-wrap: wrap;
    margin-bottom: 48px;
  }

  .social-btn {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 10px 20px;
    border-radius: 8px;
    text-decoration: none;
    font-size: 13px;
    font-weight: 500;
    transition: all 0.2s;
    border: 1px solid;
  }

  .social-btn.instagram { background: rgba(228,64,95,0.08); border-color: rgba(228,64,95,0.3); color: #f06292; }
  .social-btn.linkedin  { background: rgba(0,119,181,0.08); border-color: rgba(0,119,181,0.3); color: #5dade2; }
  .social-btn.email     { background: rgba(209,72,54,0.08);  border-color: rgba(209,72,54,0.3);  color: #ef9a9a; }
  .social-btn:hover { transform: translateY(-2px); filter: brightness(1.2); }

  .section-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 24px;
  }

  .section-title {
    font-family: 'Fira Code', monospace;
    font-size: 20px;
    font-weight: 600;
    color: #e2e8f0;
  }

  .section-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, rgba(0,247,255,0.3), transparent);
  }

  .snake-section {
    background: rgba(0,247,255,0.02);
    border: 1px solid rgba(0,247,255,0.1);
    border-radius: 12px;
    padding: 24px;
    margin-bottom: 40px;
    text-align: center;
  }

  .tech-section { margin-bottom: 40px; }
  .tech-category { margin-bottom: 28px; }

  .tech-cat-label {
    font-family: 'Fira Code', monospace;
    font-size: 11px;
    color: #00f7ff;
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 14px;
    opacity: 0.7;
  }

  .tech-grid { display: flex; flex-wrap: wrap; gap: 10px; }

  .tech-badge {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 8px 14px;
    background: rgba(255,255,255,0.03);
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: 8px;
    font-size: 12px;
    font-weight: 500;
    color: #94a3b8;
    transition: all 0.2s;
    cursor: default;
  }

  .tech-badge:hover {
    border-color: rgba(0,247,255,0.3);
    color: #e2e8f0;
    background: rgba(0,247,255,0.05);
    transform: translateY(-2px);
  }

  .tech-badge img { width: 18px; height: 18px; object-fit: contain; }

  .stats-section { margin-bottom: 40px; }

  .stats-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 16px;
    margin-bottom: 16px;
  }

  .stat-card {
    background: rgba(255,255,255,0.02);
    border: 1px solid rgba(255,255,255,0.07);
    border-radius: 12px;
    overflow: hidden;
    transition: border-color 0.2s;
  }

  .stat-card:hover { border-color: rgba(0,247,255,0.2); }
  .stat-card img { width: 100%; display: block; }
  .stat-card-wide { grid-column: 1 / -1; }

  .trophy-section, .repos-section, .quote-section { margin-bottom: 40px; }

  .trophy-card, .repos-card {
    background: rgba(255,255,255,0.02);
    border: 1px solid rgba(255,255,255,0.07);
    border-radius: 12px;
    overflow: hidden;
  }

  .trophy-card img, .repos-card img { width: 100%; display: block; }

  .quote-card {
    background: rgba(255,255,255,0.02);
    border: 1px solid rgba(255,255,255,0.07);
    border-radius: 12px;
    overflow: hidden;
    text-align: center;
    padding: 4px;
  }

  .quote-card img { max-width: 100%; display: block; margin: 0 auto; border-radius: 8px; }

  .footer {
    text-align: center;
    padding: 32px 0 16px;
    border-top: 1px solid rgba(255,255,255,0.05);
  }

  .visitor-badge img { margin: 0 auto 16px; display: block; }

  .footer-text {
    font-family: 'Fira Code', monospace;
    font-size: 11px;
    color: #334155;
    letter-spacing: 1px;
  }

  .code-rain {
    font-family: 'Fira Code', monospace;
    font-size: 11px;
    color: rgba(0,247,255,0.15);
    text-align: left;
    padding: 0 0 20px;
    line-height: 1.8;
    overflow: hidden;
    max-height: 60px;
  }

  .divider {
    margin: 40px 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(0,247,255,0.2), transparent);
  }

  .about-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 12px;
    margin-bottom: 40px;
  }

  .about-card {
    background: rgba(255,255,255,0.02);
    border: 1px solid rgba(255,255,255,0.07);
    border-radius: 10px;
    padding: 16px;
    display: flex;
    align-items: flex-start;
    gap: 12px;
  }

  .about-icon { font-size: 20px; flex-shrink: 0; }
  .about-card-title { font-size: 11px; color: #475569; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 4px; font-family: 'Fira Code', monospace; }
  .about-card-val { font-size: 13px; color: #94a3b8; font-weight: 500; }
  .about-card-val a { color: #00f7ff; text-decoration: none; }

  .avatar-ring {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    margin: 0 auto 24px;
    background: linear-gradient(135deg, #00f7ff, #0080ff, #8000ff);
    padding: 3px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .avatar-inner {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background: #0d1117;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Fira Code', monospace;
    font-size: 28px;
    font-weight: 700;
    color: #00f7ff;
    letter-spacing: -1px;
  }
</style>
</head>
<body>
<div class="bg-grid"></div>
<div class="container">

  <!-- HERO -->
  <div class="hero">
    <div class="code-rain">
      &gt;&gt;&gt; import shahriar_kabir as dev // Loading profile... [██████████] 100%
    </div>

    <div class="avatar-ring">
      <div class="avatar-inner">SK</div>
    </div>

    <div class="hero-badge">✦ AVAILABLE FOR PROJECTS ✦</div>

    <h1 class="hero-name-glow">Hi 👋, I'm Shahriar Kabir</h1>
    <p class="hero-title">Software Engineer · App Developer · Bangladesh</p>
    <p class="hero-desc">
      A passionate builder creating <span>innovative solutions</span> with modern tech.
      Always learning, always shipping. 🚀
      <span class="cursor-blink"></span>
    </p>

    <div class="socials">
      <a class="social-btn instagram" href="https://www.instagram.com/shahriar_rony06" target="_blank">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
        Instagram
      </a>
      <a class="social-btn linkedin" href="https://www.linkedin.com/in/shahriar-kabir-74160b3ab" target="_blank">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        LinkedIn
      </a>
      <a class="social-btn email" href="mailto:shahriar.kabir.swe@gmail.com">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor"><path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/></svg>
        Email Me
      </a>
    </div>
  </div>

  <!-- ABOUT CARDS -->
  <div class="about-grid">
    <div class="about-card">
      <div class="about-icon">📍</div>
      <div><div class="about-card-title">Location</div><div class="about-card-val">Bangladesh 🇧🇩</div></div>
    </div>
    <div class="about-card">
      <div class="about-icon">💻</div>
      <div><div class="about-card-title">Focus</div><div class="about-card-val">Software & App Dev</div></div>
    </div>
    <div class="about-card">
      <div class="about-icon">📧</div>
      <div><div class="about-card-title">Contact</div><div class="about-card-val"><a href="mailto:shahriar.kabir.swe@gmail.com">shahriar.kabir.swe@gmail.com</a></div></div>
    </div>
    <div class="about-card">
      <div class="about-icon">🚀</div>
      <div><div class="about-card-title">Status</div><div class="about-card-val" style="color:#4ade80">Open to Projects</div></div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- SNAKE -->
  <div class="section-header">
    <span class="section-title">🐍 Contribution Activity</span>
    <div class="section-line"></div>
  </div>
  <div class="snake-section">
    <img src="https://raw.githubusercontent.com/platane/snk/output/github-contribution-grid-snake-dark.svg" alt="Snake animation" style="max-width:100%; height:auto;" />
  </div>

  <!-- TECH STACK -->
  <div class="tech-section">
    <div class="section-header">
      <span class="section-title">🖥️ Tech Stack</span>
      <div class="section-line"></div>
    </div>

    <div class="tech-category">
      <div class="tech-cat-label">// Languages</div>
      <div class="tech-grid">
        <div class="tech-badge"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg"> HTML5</div>
        <div class="tech-badge"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg"> CSS3</div>
        <div class="tech-badge"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg"> JavaScript</div>
        <div class="tech-badge"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/c/c-original.svg"> C</div>
        <div class="tech-badge"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/cplusplus/cplusplus-original.svg"> C++</div>
        <div class="tech-badge"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg"> Java</div>
      </div>
    </div>

    <div class="tech-category">
      <div class="tech-cat-label">// Cloud & Backend</div>
      <div class="tech-grid">
        <div class="tech-badge"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" style="filter:invert(1)"> AWS</div>
        <div class="tech-badge"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/apache/apache-original.svg"> Apache</div>
        <div class="tech-badge"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg"> MySQL</div>
      </div>
    </div>

    <div class="tech-category">
      <div class="tech-cat-label">// Tools & Platforms</div>
      <div class="tech-grid">
        <div class="tech-badge"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" style="filter:invert(1)"> GitHub</div>
        <div class="tech-badge"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg"> Figma</div>
        <div class="tech-badge"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/jest/jest-plain.svg"> Jest</div>
      </div>
    </div>

    <div class="tech-category">
      <div class="tech-cat-label">// Design Suite</div>
      <div class="tech-grid">
        <div class="tech-badge">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="#FF0000"><path d="M13.966 22.624l-1.69-4.281H7.122l3.867-7.713 2.977 7.994zM.5 1.376h5.348l6.03 16.73L17.905 1.376h5.348L14.842 23.624h-6.14z"/></svg>
          Adobe
        </div>
        <div class="tech-badge">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="#9999FF"><path d="M.047 4.382v15.236L7.33 24V0zm16.625.312L9.35 9.514l4.786 8.199 6.516-13.02zM9.35 9.514L.047 4.382l4.477 7.679zm14.603-5.132l-4.562 9.126-2.077-3.561z"/></svg>
          After Effects
        </div>
        <div class="tech-badge">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="#EC1C24"><path d="M16.3 3.3H7.7C5.3 3.3 3.3 5.3 3.3 7.7v8.7c0 2.3 2 4.3 4.4 4.3h8.7c2.3 0 4.3-2 4.3-4.4V7.7c0-2.4-2-4.4-4.4-4.4zm-7 9.5c0 .4-.4.8-.8.8H7.2c-.4 0-.8-.4-.8-.8v-1.3c0-.4.4-.8.8-.8h1.3c.4 0 .8.4.8.8v1.3zm1.6-5.6c0 .4-.4.8-.8.8H8.8c-.4 0-.8-.4-.8-.8v-.6c0-.4.4-.8.8-.8h1.3c.4 0 .8.4.8.8v.6zm5 5.6c0 .4-.4.8-.8.8h-3.8c-.4 0-.8-.4-.8-.8v-1.3c0-.4.4-.8.8-.8h3.8c.4 0 .8.4.8.8v1.3zm0-5.6c0 .4-.4.8-.8.8h-1.3c-.4 0-.8-.4-.8-.8v-.6c0-.4.4-.8.8-.8H15c.4 0 .8.4.8.8v.6z"/></svg>
          Acrobat
        </div>
        <div class="tech-badge">
          <svg width="18" height="18" viewBox="0 0 24 24" fill="#00C4CC"><path d="M11.03 0C8.3 0 6.09 2.21 6.09 4.94c0 2.72 2.21 4.93 4.94 4.93.88 0 1.7-.23 2.41-.64v.5c0 1.34-1.09 2.43-2.43 2.43H8.37v2.43h2.64c2.73 0 4.94-2.21 4.94-4.94V4.94C15.95 2.21 13.75 0 11.03 0zm0 7.44c-1.38 0-2.5-1.12-2.5-2.5s1.12-2.5 2.5-2.5 2.5 1.12 2.5 2.5-1.12 2.5-2.5 2.5zm1.93 9.44H8.37v2.43h4.59v3.69h2.43v-3.69h-.43zm-4.59 0v2.43H5.73v-2.43z"/></svg>
          Canva
        </div>
      </div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- GITHUB STATS -->
  <div class="stats-section">
    <div class="section-header">
      <span class="section-title">📊 GitHub Stats</span>
      <div class="section-line"></div>
    </div>
    <div class="stats-grid">
      <div class="stat-card">
        <img src="https://github-readme-stats.vercel.app/api?username=shahriarkabir07&theme=dark&hide_border=true&include_all_commits=true&count_private=false&bg_color=0d1117&title_color=00f7ff&text_color=94a3b8&icon_color=00f7ff" alt="GitHub Stats" />
      </div>
      <div class="stat-card">
        <img src="https://nirzak-streak-stats.vercel.app/?user=shahriarkabir07&theme=dark&hide_border=true&background=0d1117&ring=00f7ff&fire=ff6b6b&currStreakLabel=00f7ff" alt="Streak Stats" />
      </div>
      <div class="stat-card stat-card-wide">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=shahriarkabir07&theme=dark&hide_border=true&include_all_commits=true&count_private=false&layout=compact&bg_color=0d1117&title_color=00f7ff&text_color=94a3b8" alt="Top Languages" />
      </div>
    </div>
  </div>

  <!-- TROPHIES -->
  <div class="trophy-section">
    <div class="section-header">
      <span class="section-title">🏆 GitHub Trophies</span>
      <div class="section-line"></div>
    </div>
    <div class="trophy-card">
      <img src="https://github-profile-trophy.vercel.app/?username=shahriarkabir07&theme=darkhub&no-frame=true&no-bg=true&margin-w=4&column=6" alt="Trophies" style="width:100%; background:#0d1117; padding:12px; box-sizing:border-box;" />
    </div>
  </div>

  <!-- TOP CONTRIBUTED REPOS -->
  <div class="repos-section">
    <div class="section-header">
      <span class="section-title">🔝 Top Contributed Repos</span>
      <div class="section-line"></div>
    </div>
    <div class="repos-card">
      <img src="https://github-contributor-stats.vercel.app/api?username=shahriarkabir07&limit=5&theme=dark&combine_all_yearly_contributions=true&bg_color=0d1117&hide_border=true" alt="Top Contributed Repos" />
    </div>
  </div>

  <!-- QUOTE -->
  <div class="quote-section">
    <div class="section-header">
      <span class="section-title">✍️ Random Dev Quote</span>
      <div class="section-line"></div>
    </div>
    <div class="quote-card">
      <img src="https://quotes-github-readme.vercel.app/api?type=horizontal&theme=radical" alt="Dev Quote" />
    </div>
  </div>

  <div class="divider"></div>

  <!-- FOOTER -->
  <div class="footer">
    <div class="visitor-badge">
      <img src="https://visitcount.itsvg.in/api?id=shahriarkabir07&icon=2&color=6&label=Profile+Views" alt="Visitor Count" />
    </div>
    <p class="footer-text">⚡ Proudly crafted with GPRM · Made with ❤️ from Bangladesh</p>
    <p style="font-family:'Fira Code',monospace; font-size:10px; color:#1e293b; margin-top:8px;">
      console.log("Thanks for visiting! 🙏");
    </p>
  </div>

</div>
</body>
</html>
