<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>X-TOVA</title>
  <!--  <link href="https://fonts.googleapis.com/css2?family=Noto+Serif+Bengali&display=swap" rel="stylesheet">-->
  <!-- CSS স্টাইল শুরু -->
  <style>
    /* সাধারণ রিসেট */
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body, html {
      /*font-family: 'Noto Serif Bengali', serif;*/
      background-color: #000;
      color: #fff;
    }

    /* টপবার স্টাইল */
    .topbar {
      display: flex;
      align-items: center;
      padding: 18px;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      z-index: 1100;
      background: #000;
    }

    /* হ্যামবার্গার মেনু */
    .hamburger {
      cursor: pointer;
      width: 30px;
      height: 22px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      margin-right: 15px;
    }

    .hamburger span {
      display: block;
      height: 4px;
      background: #fff;
      border-radius: 2px;
      transition: 0.4s;
    }

  

    /* লোগো */
    .logo img { height: 40px;}

    /* সাইডবার */
    .sidebar {
      position: fixed;
      top: 0;
      left: -250px;
      width: 220px;
      height: 100%;
      background-color: #000;
      padding-top: 80px;
      transition: left 0.4s ease;
      z-index: 1000;
    }

    .sidebar.open { left: 0; }

    /* সাইডবারের লিংক */
    .sidebar a {
      display: block;
      padding: 15px 20px;
      color: #ccc;
      text-decoration: none;
    }

    .sidebar a:hover {
      background: #333;
      color: #fff;
    }

    /* হ্যামবার্গার মেনু ওপেন অবস্থায় */
    .hamburger.open span:nth-child(1) { transform: rotate(45deg) translateY(9px); }
    .hamburger.open span:nth-child(2) { opacity: 0; }
    .hamburger.open span:nth-child(3) { transform: rotate(-45deg) translateY(-9px); }
  
  /* মূল কন্টেন্ট */
    .content { padding-top: 0px; }

    /* প্রতিটি পেজ */
    .page { display: none; }
    .page.active { display: block; }

    /* হিরো হেডার */
    .hero-header {
      position: relative;
      width: 100%;
     aspect-ratio: 1 / 1;
      overflow: hidden;
      display: flex;
      align-items: center;
      justify-content: center;
      text-align: left;
      color: #fff;
    }

    .bg-image {
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      width: 100%;
      object-fit: cover;
      z-index: 1;
    }

    .overlay {
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      width: 100%;
      background: rgba(0, 0, 0, 0);
     /* background: linear-gradient(to top, rgba(0, 0, 0, 1), rgba(0, 0, 0, 0));
     */
      z-index: 2;
    }

    .header-content {
      position: relative;
      z-index: 3;
      max-width: 600px;
      padding: 20px;
    }

    /* হেডার টাইটেল ও সাবটাইটেল */
    .header-content h1 { font-size: 2.5rem; margin-bottom: 1rem; }
    .header-content p { font-size: 1rem; line-height: 1.6; }

    /* ক্লাইমেট পোস্ট */
    .climate-post {
      position: relative;
      width: 90%;
      aspect-ratio: 1.4 / 1;
      overflow: hidden;
      margin: 40px 20px;
      border-radius: 0px;
    }

    .climate-link {
      display: block;
      height: 100%;
      color: white;
      text-decoration: none;
      position: relative;
    }

    .climate-bg {
      width: 100%;
      height: 100%;
      object-fit: cover;
      position: absolute;
      top: 0;
      left: 0;
      z-index: 1;
    }

    .climate-overlay {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(to top, rgba(0, 0, 0, 1), rgba(0, 0, 0, 0));
      z-index: 2;
    }

    .climate-text {
      position: relative;
      z-index: 4;
      padding: 40% 20px;
      max-width: 500px;
    }

    .climate-text h2 { font-size: 2rem; margin-bottom: 10px; }
    .climate-text p { font-size: 1rem; line-height: 1.3;}

    /* ফুটার */
    footer {
      background-color: #111111;
      color: #fff;
      padding: 40px 20px;
      text-align: center;
    }

    footer a { color: #ccc; text-decoration: none; }
    footer a:hover { text-decoration: 0; }

    .footer-links {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 50px;
      margin-top: 30px;
    }

    .social-icons {
      display: flex;
      justify-content: center;
      margin-top: 30px;
    }

    .social-icons a img {
      height: 30px;
      margin: 0 10px;
      filter: invert(1);
    }

    /* ব্যাকড্রপ ওভারলে */
    #overlay {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      height: 100%;
      width: 100%;
      background: rgba(0, 0, 0, 0.5);
      z-index: 900;
    }
  
  .page * {
  animation: slideUp 0.7s ease-out forwards;
}

/* এনিমেশন ডিফাইন করা */
@keyframes slideUp {
  0% {
    opacity: 1;
    transform: translateY(60px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}
  
  </style>
  <!-- CSS স্টাইল শেষ -->
</head>

<body>

  <!-- টপবার -->
  <div class="topbar">
    <!-- হ্যামবার্গার বাটন -->
    <div class="hamburger" id="hamburger">
      <span></span><span></span><span></span>
    </div>
    <!-- লোগো -->
    <div class="logo">
      <img  src="https://i.postimg.cc/28KZMNyW/20250424-223807.png" alt="X-TOVA Logo" >
    </div>
  </div>

  <!-- সাইডবার -->
  <div class="sidebar" id="sidebar">
    <!-- সাইডবারের লিংকসমূহ -->
    <a href="https://zunova.github.io/bd/">Home</a>
    <a href="https://zunova.github.io/bd/" onclick="showPage('news')">News & Events</a>
    <a href="https://zunova.github.io/bd/">Missions</a>
    <a href="https://zunova.github.io/bd/" onclick="showPage('solar-system')">Solar System</a>
    <a href="https://zunova.github.io/bd/">Earth</a>
     <a href="https://zunova.github.io/bd/">The Universe</a>
    <a href="https://zunova.github.io/bd/">Technology</a>
    <a href="https://zunova.github.io/bd/">About X-TOVA</a>
    </div>

  <!-- ওভারলে ব্যাকড্রপ -->
  <div id="overlay"></div>

  <!-- মূল কন্টেন্ট এরিয়া -->
  <div class="content" id="mainContent">

    
    
    <!-- হোম পেজ -->
    <div id="home" class="page active">
      <!-- হিরো ব্যানার -->
      <header class="hero-header" style="aspect-ratio: auto; height: 100vh;">
        <img src="https://media-hosting.imagekit.io/7a2e66f9938d438d/1000009881.jpg?Expires=1840348330&Key-Pair-Id=K2ZIVPTIP2VGHC&Signature=kMQX9TyNxcFviLRN1rs2N5-I91xg84CRR-Qlw4~LpEG1fVbRk390soriNq3pryLyZG5WsODtXQdtysRQI7ya0N697J2ccYfcwerWAyxMP3epf9ua94oX8R0vEbryU56C~GHw6w3TJKShmdiOu3AynbDf8ambW-yvrY2orQMrD0A6piIZcsp7GEdmW3XwvUG1qrRa3~yG-rI7CxSvsWbd93xS1~Qg-YKZj2AFmrgA9T5pMrSoyGyhhk1oI2OozmDE8z~TH2t4C5NUIR8dPv1gkaUkyB5TJl5sa71LrAVypSXtaAqhgxJHiA52v2zyVbnU6Vww1lICpzU~pOfadiSIyA__" class="bg-image">
        <div class="overlay"></div>
        <div class="header-content">
          <h1>X-TOVA</h1>
          <p></>X-TOVA explores the unknown in air and space, innovates for the benefit of humanity, and inspires the world through discovery.</p>
       </div>
      </header>

      <!-- নিউজ অংশ -->
      <h1>News & Events</h1>
      <p>Stay updated with X-TOVA's latest news and events.</p>

      <!--<p>&nbsp;</p><div class="separator" style="clear: both; text-align: center;"><iframe allowfullscreen="" height="274" src="https://www.youtube.com/embed/zT3l1lT-_Wk" width="351" youtube-src-id="zT3l1lT-_Wk"></iframe></div><br /><p></p>-->
      
      <!-- পোস্ট ১ 
      <section class="climate-post">
        <a href="#" class="climate-link" onclick="showPage('climate')">
          <img src="https://i.postimg.cc/vTzfK4jL/IMG-20250425-145649.jpg" class="climate-bg">
          <div class="climate-overlay"></div>
          <div class="climate-text">
            <h2>Climate Change</h2>
            <p>NASA is a global leader in studying Earth’s changing climate.</p>
          </div>
        </a>
      </section>

      <!-- পোস্ট ২ 
      <section class="climate-post">
        <a href="#" class="climate-link" onclick="showPage('pop')">
          <img src="https://i.ibb.co/DPz5sVDS/73f436678910.jpg" class="climate-bg">
          <div class="climate-overlay"></div>
          <div class="climate-text">
            <h2>Earth Climate is changing!</h2>
            <p>NASA is a global leader in studying Earth’s changing climate.</p>
          </div>
        </a>
      </section>-->
      
    </div>
    

<!-- ফুটার -->
    <footer>
      <div><img src="https://i.postimg.cc/28KZMNyW/20250424-223807.png" alt="ZUNOVA Logo" style="height: 50px;"></div>
      <h1>ZUNOVA</h1>
      <p>ZUNOVA explores the unknown in air and space, innovates for the benefit of humanity, and inspires the world through discovery.</p>
    
      <br><br><p> <br>All Pages</p>
      <div class="footer-links">
        <div>
          <h2><a href="https://zunova.github.io/bd/" onclick="showPage('home')">Home</a></h2>
          <h2><a

href="https://zunova.github.io/news/events/" onclick="showPage('news')">News & Events</a></h2>
          <h2><a href="https://zunova.github.io/missions/" onclick="showPage('missions')">Missions</a></h2>
 <h2><a href="https://zunova.github.io/solarsystem/" onclick="showPage('missions')">Missions</a></h2>
        </div>
        <div>
 <h2><a href="https://zunova.github.io/earth/" onclick="showPage('missions')">Earth</a></h2>
          <h2><a href="https://zunova.github.io/universe/" onclick="showPage('universe')">The Universe</a></h2>
          <h2><a href="https://zunova.github.io/technology/" onclick="showPage('technology')">Technology</a></h2>
          <h2><a href="https://zunova.github.io/about/" onclick="showPage('about')">About</a></h2>
        </div>
      </div>

    <br><br><br>
    <p>Join Us <span style="color: red;">➔</span></p>
      <!-- সোশ্যাল আইকন -->
    <div class="social-icons">
  <a href="https://facebook.com/@ZUNOVAofficial" target="_blank"><img src="https://i.ibb.co/0Rn3cY0N/8fedea3b4ab9.png" alt="Facebook"></a>
  <a href="https://instagram.com/ZUNOVAofficial" target="_blank"><img src="https://i.ibb.co/fzDwQZ0F/54a6d7f094cb.png" alt="Instagram"></a>
  <a href="https://x.com/ZUNOVAofficial" target="_blank"><img src="https://i.ibb.co/1fG6k8Ww/93ada2da4eee.png" alt="X"></a>
  <a href="https://youtube.com/@ZUNOVAofficial" target="_blank"><img src="https://i.ibb.co/mCrxw2YM/b21e91fe0afb.png" alt="YouTube"></a>
</div>
<br><br><br>
<a>© ZUNOVA</a>
</footer>
</div>
  <!-- জাভাস্ক্রিপ্ট শুরু -->
  <script>
    // হ্যামবার্গার ক্লিক করলে সাইডবার খুলবে/বন্ধ হবে
    const hamburger = document.getElementById('hamburger');
    const sidebar = document.getElementById('sidebar');
    const overlay = document.getElementById('overlay');

    hamburger.addEventListener('click', () => {
      sidebar.classList.toggle('open');
      hamburger.classList.toggle('open');
      overlay.style.display = sidebar.classList.contains('open') ? 'block' : 'none';
    });

    overlay.addEventListener('click', () => {
      sidebar.classList.remove('open');
      hamburger.classList.remove('open');
      overlay.style.display = 'none';
    });

    // পেজ দেখানোর ফাংশন
    function showPage(pageId) {
      document.querySelectorAll('.page').forEach(page => page.classList.remove('active'));
      document.getElementById(pageId).classList.add('active');
      sidebar.classList.remove('open');
      hamburger.classList.remove('open');
      overlay.style.display = 'none';
    }
  </script>
  <!-- জাভাস্ক্রিপ্ট শেষ -->
</body>