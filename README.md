<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Saqib Weddings — 3D Modern</title>
  <style>
    :root{
      --bg:#ffffff;
      --text:#000000;
      --muted:#444;
      --accent:#000;
      --card-shadow: 0 12px 30px rgba(0,0,0,0.12);
      --perspective: 1000px;
      --gap:18px;
      --radius:14px;
    }
    /* Reset */
    *{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%}
    body{
      background:var(--bg);
      color:var(--text);
      font-family: Inter, ui-sans-serif, system-ui, -apple-system, "Helvetica Neue", Arial;
      -webkit-font-smoothing:antialiased;
      line-height:1.35;
      padding:24px;
    }
    a { color:var(--text); text-decoration:none; }
    header{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:16px;
      margin-bottom:28px;
    }
    /* Logo */
    .logo{
      display:flex;
      align-items:center;
      gap:12px;
    }
    .logo .mark{
      width:62px;height:62px;border-radius:12px;
      background:linear-gradient(135deg,#000 0%, #111 100%);
      display:flex;align-items:center;justify-content:center;
      color:white;font-weight:700;font-size:14px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.15), inset 0 -6px 10px rgba(255,255,255,0.03);
      transform: translateZ(20px);
    }
    .logo h1{font-size:18px;letter-spacing:0.4px}
    nav{display:flex;gap:14px;align-items:center}
    nav a.button{
      padding:10px 14px;border-radius:10px;border:1px solid var(--muted);
      font-weight:600;font-size:14px;
      box-shadow: var(--card-shadow);
      background:linear-gradient(180deg,#fff,#fbfbfb);
    }
    /* Hero */
    .hero{
      display:grid;
      grid-template-columns: 1fr 460px;
      gap:28px;
      align-items:center;
      margin-bottom:36px;
    }
    .hero-left h2{
      font-size:38px;margin-bottom:8px;
    }
    .hero-left p{color:var(--muted);margin-bottom:18px}
    /* 3D CTA button (touch-bubble style) */
    .cta-wrap{perspective:var(--perspective)}
    .cta{
      display:inline-block;
      padding:16px 26px;border-radius:18px;
      background:#000;color:#fff;font-weight:700;
      transform-style:preserve-3d;
      transition: transform .18s ease, box-shadow .18s ease;
      box-shadow: 0 18px 40px rgba(0,0,0,0.18);
      border: 2px solid rgba(0,0,0,0.08);
      cursor:pointer;
    }
    .cta:active{ transform: translateY(3px) scale(.997) rotateX(2deg) }
    .cta .sub{display:block;font-weight:600;font-size:12px;color:#ddd;margin-top:6px}
    /* 3D card preview */
    .preview{
      width:100%;
      height:320px;
      border-radius:var(--radius);
      background: linear-gradient(180deg,#fff,#fafafa);
      box-shadow: var(--card-shadow);
      display:flex;align-items:center;justify-content:center;
      transform-style:preserve-3d;
      transition: transform .25s ease, box-shadow .25s ease;
      perspective: var(--perspective);
    }
    .interactive-card{
      width:92%;height:85%;border-radius:12px;
      background:linear-gradient(135deg,#fff,#f6f6f6);
      display:flex;flex-direction:column;justify-content:center;align-items:center;
      border:1px solid #eee;
      transform: translateZ(24px);
    }
    .preview:hover{ transform: translateY(-8px) rotateX(4deg) rotateY(-6deg); box-shadow: 0 30px 60px rgba(0,0,0,0.18);}
    .preview img{max-width:72%; opacity:.95}
    /* Gallery sections */
    section.gallery{
      margin-bottom:36px;
    }
    .grid{
      display:grid;
      gap:var(--gap);
    }
    /* pictures side-by-side multiple */
    .images-grid{
      grid-template-columns: repeat(auto-fit, minmax(200px,1fr));
    }
    .images-grid .img-card{
      border-radius:12px;overflow:hidden;border:1px solid #eee;
      box-shadow: 0 8px 28px rgba(0,0,0,0.06);
      transition: transform .18s ease;
      background:#fff;
    }
    .img-card img{width:100%;height:100%;object-fit:cover;display:block;filter:contrast(.96)}
    .img-card:hover{ transform: translateY(-6px) }
    /* videos side-by-side multiple */
    .videos-grid{
      grid-template-columns: repeat(auto-fit, minmax(260px,1fr));
    }
    .video-card{
      border-radius:12px;overflow:hidden;border:1px solid #eee;
      background:#000;color:#fff;position:relative;
      box-shadow: 0 10px 30px rgba(0,0,0,0.12);
    }
    .video-card video{width:100%;height:220px;display:block;background:#000}
    .video-meta{ padding:12px; color:var(--muted); font-size:14px }
    /* Responsive adjustments */
    @media (max-width:980px){
      .hero{grid-template-columns:1fr; text-align:center}
      .preview{height:260px}
      .hero-left h2{font-size:32px}
    }
    /* Contact footer */
    footer.contact{
      margin-top:32px;padding:22px;border-top:1px solid #eee;border-radius:12px;background:#fff;
      display:flex;flex-direction:row;gap:18px;align-items:center;justify-content:space-between;
      box-shadow: 0 10px 30px rgba(0,0,0,0.04)
    }
    .contact-left{display:flex;flex-direction:column;gap:6px}
    .contact-left .big{font-weight:700;font-size:18px}
    .socials{display:flex;gap:12px;align-items:center}
    .socials a{font-weight:600;padding:8px 12px;border-radius:10px;border:1px solid #eee}
    .note{font-size:13px;color:var(--muted)}
    /* Lightbox overlay */
    .lightbox{
      position:fixed;inset:0;display:none;align-items:center;justify-content:center;
      background:rgba(0,0,0,0.8);z-index:9999;padding:18px;
    }
    .lightbox.open{display:flex}
    .lightbox .inner{max-width:1100px;width:100%;max-height:90vh}
    .lightbox img, .lightbox video{width:100%;height:auto;display:block;border-radius:10px}
    .lb-close{
      position:fixed;right:20px;top:20px;background:#fff;border-radius:999px;padding:10px 12px;font-weight:700;cursor:pointer;color:#000;
      box-shadow:0 6px 20px rgba(0,0,0,0.3);
    }
  </style>
</head>
<body>

  <header>
    <div class="logo">
      <!-- Replace the mark with your real logo image if you have one -->
      <div class="mark">SW</div>
      <div>
        <h1>Saqib Weddings</h1>
      </div>
    </div>

    <nav>
      <a class="button" href="#gallery">Gallery</a>
      <a class="button" href="#videos">Videos</a>
      <a class="button" href="#contact">Contact</a>
    </nav>
  </header>

  <!-- HERO -->
  <section class="hero">
    <div class="hero-left">
      <h2>Agency-level wedding films & photos — Saqib Weddings</h2>
      <p>We craft cinematic wedding stories with a modern 3D touch. Send your videos or book a shoot — quick contact below.</p>

      <div style="display:flex;gap:12px;align-items:center;flex-wrap:wrap;margin-top:8px">
        <div class="cta-wrap">
          <a class="cta" href="#contact">
            Contact / Book
            <span class="sub">Call: 0316-2772095</span>
          </a>
        </div>

        <div class="cta-wrap">
          <button class="cta" id="submitVideoBtn" onclick="promptSendVideo()">
            Send Video
            <span class="sub">Share footage via email</span>
          </button>
        </div>
      </div>
    </div>

    <!-- 3D style preview -->
    <div class="preview" id="previewCard" aria-hidden="true">
      <div class="interactive-card">
        <!-- change to your logo image -->
        <img src="c:\Users\Lenovo\Downloads\picturs\SAQIB WEDDINGS.jpg" alt="Saqib Weddings Logo">
        <div style="margin-top:14px;font-weight:700;color:var(--muted)">Saqib Weddings</div>
      </div>
    </div>
  </section>

  <!-- PICTURES GRID -->
  <section class="gallery" id="gallery">
    <h3 style="margin-bottom:12px">Wedding Photos — Side by side</h3>
    <div class="grid images-grid">
      <!-- Replace placeholders with real image URLs -->
      <div class="img-card"><img src="d:\file\3uToolsV3\saqib weddings\page post\IMG_8173.JPG" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\1\01.jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\1\4 (1).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\1\4 (2).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\1\4 (4).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\1\4 (6).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\2\1 (2).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\2\1 (4).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\2\1 (1).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\2\1 (7).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\2\1 (3).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\2\1 (6).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\2\1 (5).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\3\5 (5).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\3\5 (1).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\3\5 (2).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\3\5 (3).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\3\5 (4).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\8 (6).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\8 (5).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\8 (1).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\8 (7).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\8 (2).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\8 (3).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\8 (4).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\9 (5).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\9 (4).jpg" alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\9 (12).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\9 (13).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\9 (3).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\9 (9).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\9 (10).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\9 (6).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\9 (7).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\9 (8).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\9 (11).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\12 (1).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\12 (3).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\4\12 (2).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\9 (2).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\9 (1).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\11 (7).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\11 (9).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\11 (3).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\11 (1).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\11 (8).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\11 (4).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\11 (6).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\11 (2).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\3 (1).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\3 (4).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\3 (3).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\3 (6).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\3 (2).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\3 (5).jpg"alt=""></div>
      <div class="img-card"><img src="c:\Users\Lenovo\Downloads\picturs\5\7 (1).jpg"alt=""></div>
    </div>
  </section>

  <!-- VIDEOS GRID -->
  <section class="gallery" id="videos">
    <h3 style="margin-bottom:12px">Videos — Multiple side-by-side</h3>
    <div class="grid videos-grid">
      <!-- Example local video tags: replace src with your MP4 / WebM hosted files or use YouTube embeds if you prefer -->
      <div class="video-card">
        <video controls  playsinline preload="metadata" poster="">
          <source src="c:\Users\Lenovo\Downloads\picturs\Sumaira & Ahsan 👩_❤️_👨Nikah day 🌸.mp4" type="video/mp4">
          Your browser does not support the video tag.
        </video>
        <div class="video-meta">Cinematic Highlights — 2:12</div>
      </div>

      <div class="video-card">
        <video controls playsinline preload="metadata" poster="">
          <source src="c:\Users\Lenovo\Downloads\picturs\@saqibweddings Khurram & Arbish👩_❤️_👨.mp4" type="video/mp4">
          Your browser does not support the video tag.
        </video>
        <div class="video-meta">Reception Reel — 1:48</div>
      </div>

      <div class="video-card">
        <video controls playsinline preload="metadata" poster="">
          <source src="c:\Users\Lenovo\Downloads\picturs\@saqibweddings Khurram & Arbish.mp4" type="video/mp4">
          Your browser does not support the video tag.
        </video>
        <div class="video-meta">Trailer — 0:45</div>
    </div>
  </section>
  


</body>
</html><!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>saqibweddings — Invoice (A4)</title>
  <style>
    /* A4 layout */
    @page { size: A4; margin: 20mm }
    body { font-family: Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial; margin: 0; padding: 0; color: #222 }
    .page { width: 310mm; min-height: 297mm; padding: 02mm; box-sizing: border-box }
    .card { background: #fff; border-radius: 8px; padding: 20px; box-shadow: 0 2px 8px rgba(0,0,0,0.06) }

    header { display:flex; justify-content:space-between; align-items:center; margin-bottom:18px }
    .brand { font-weight:700; font-size:22px; letter-spacing:0.6px }
    .brand small { display:block; font-size:12px; font-weight:600 }

    table { width:100%; border-collapse:collapse; margin-top:12px }
    th, td { padding:10px 8px; text-align:left; border-bottom:1px solid #e9e9e9; font-size:14px }
    th { background:#fafafa; font-weight:700 }

    .right { text-align:right }
    input[type='number'], input[type='text'], select { padding:6px 8px; font-size:14px; border:1px solid #dcdcdc; border-radius:4px }
    input[readonly] { background:#f7f7f7; color:#333 }
    .muted { color:#666; font-size:13px }

    .highlight { background:linear-gradient(90deg,#fff7d6,#fff1e0); padding:8px 12px; border-radius:6px }
    .subtotal { font-weight:800; font-size:18px }
    .note { font-size:13px; color:#555 }

    .totals { margin-top:14px; width:320px; float:right }
    .totals table { border:0 }
    .totals td { border:0; padding:6px 8px }

    .actions { margin-top:22px; display:flex; gap:10px }
    button { padding:8px 12px; border-radius:6px; border:0; cursor:pointer; font-weight:700 }
    .btn-print { background:#0b5cff; color:#fff }
    .btn-reset { background:#eee; color:#222 }

    footer { margin-top:40px; font-size:12px; color:#666 }

    /* small-screen friendly */
    @media (max-width:800px){ .page{padding:12px} .totals{float:none;width:100%} }
  </style>
</head>
<body>
  <div class="page">
    <div class="card" role="main">
      <header>
        <div>
          <div class="brand">saqibweddings<br/><small>Customized Packages — Automatic 10% PKR discount</small></div>
          <div class="muted">Invoice size: A4 — Unit prices are fixed (not editable)</div>
        </div>
        <div style="text-align:right">
          <div><strong>Invoice</strong></div>
          <div class="muted">Date: <span id="invDate"></span></div>
          <div class="muted">Invoice #: <input id="invoiceNo" type="text" value="SW-" style="width:110px"/></div>
        </div>
      </header>

      <section aria-label="controls" style="display:flex; gap:12px; align-items:center; margin-bottom:8px">
        <label class="muted">Currency:
          <select id="currency">
            <option value="PKR">PKR</option>
          </select>
        </label>
        <label class="muted">Client name:
          <input id="clientName" type="text" placeholder="Client name" style="width:180px" />
        </label>
        <label class="muted">Exact Venue(s):
          <input id="Exact Venue(s)" type="text" placeholder="CExact Venue(s)" style="width:180px" />
        </label>
      </section>
       <label class="muted">Date(s):
          <input id="Date(s)" type="text" placeholder="Date(s)" style="width:180px" />
        </label>
      </section>
       <label class="muted">Names of the Couple:
          <input id="Names of the Couple" type="text" placeholder="Names of the Couple" style="width:180px" />
        </label>
        <label class="muted">Wedding days:
          <input id="weddingDays" type="number" min="1" value="1" style="width:68px" />
        </label>
      </section>

      <table aria-label="invoice-items">
        <thead>
          <tr>
            <th style="width:40%">Description</th>
            <th style="width:12%">Unit Price</th>
            <th style="width:12%">Qty</th>
            <th style="width:12%">Days</th>
            <th class="right" style="width:05%">Line Total</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>
              1 DAY PHOTOGRAPHY
              <div class="muted" style="font-size:13px">Fixed unit price — day-based</div>
            </td>
            <td><input id="price_photo" type="text" readonly value="15000" /></td>
            <td><input id="qty_photo" type="number" min="0" value="1" /></td>
            <td><input class="daybased" data-item="photo" type="number" min="1" value="1" readonly /></td>
            <td class="right"><strong id="line_photo">15000</strong></td>
          </tr>

          <tr>
            <td>
              1 DAY VIDEOGRAPHY
              <div class="muted" style="font-size:13px">Fixed unit price — day-based</div>
            </td>
            <td><input id="price_video" type="text" readonly value="20000" /></td>
            <td><input id="qty_video" type="number" min="0" value="1" /></td>
            <td><input class="daybased" data-item="video" type="number" min="1" value="1" readonly /></td>
            <td class="right"><strong id="line_video">20000</strong></td>
          </tr>

          <tr>
            <td>
              1 ALBUM PAYMENT
              <div class="muted" style="font-size:13px">Unit price fixed — album custom notes below</div>
            </td>
            <td><input id="price_album" type="text" readonly value="23000" /></td>
            <td><input id="qty_album" type="number" min="0" value="1" /></td>
            <td class="muted">—</td>
            <td class="right"><strong id="line_album">23000</strong></td>
          </tr>

          <tr>
            <td>
              1 DAY DRONE
              <div class="muted" style="font-size:13px">Fixed unit price — day-based</div>
            </td>
            <td><input id="price_drone" type="text" readonly value="12000" /></td>
            <td><input id="qty_drone" type="number" min="0" value="1" /></td>
            <td><input class="daybased" data-item="drone" type="number" min="1" value="1" readonly /></td>
            <td class="right"><strong id="line_drone">12000</strong></td>
          </tr>
        </tbody>
      </table>

      <div style="margin-top:8px">
        <label class="muted">1 Album 10 sheets size 12/36 / notes:</label>
        <label class="muted">

  Payment Terms
- 50% advance at booking (non-refundable).
- Remaining balance to be cleared before final delivery.

- Payments via Bank Transfer / Cash / 
Bank Details:
Bank: HBL
Account Title: Saqib Weddings
Account No: 11310981042292015


Notes
✔ Delivery timeline: video 1 month & Album 7 Days after the wedding. 
✔ Thank you for choosing Saqib Weddings!
 / notes:</label>

      </div>

      <div class="totals">
        <table>
          <tr>
            <td class="muted">Subtotal</td>
            <td class="right highlight subtotal" id="subtotal">0</td>
          </tr>
          <tr>
            <td class="muted">Discount (<span id="discountPct">0%</span>)</td>
            <td class="right" id="discountAmt">0</td>
          </tr>
          <tr>
            <td class="muted">Tax (if any)</td>
            <td class="right" id="taxAmt">0</td>
          </tr>
          <tr style="border-top:2px solid #efefef">
            <td style="font-weight:800">Total</td>
            <td class="right" style="font-weight:800; font-size:18px" id="totalAmt">0</td>
          </tr>
        </table>
      </div>

      <div style="clear:both"></div>

      <div class="actions">
        <button class="btn-print" onclick="window.print()">Print / Save PDF</button>
        <button class="btn-reset" onclick="resetForm()">Reset</button>
      </div>

      <footer>
        <div class="note">Note: Unit prices are fixed and cannot be changed in this invoice (as requested). Change quantities, wedding days or album customization above. Discount of 5% applies automatically when currency is PKR.</div>
      </footer>
    </div>
  </div>

  <script>
    // Init
    document.getElementById('invDate').textContent = new Date().toLocaleDateString();

    const currencyEl = document.getElementById('currency');
    const weddingDaysEl = document.getElementById('weddingDays');

    // Map day-based inputs to reflect wedding days (readonly to prevent confusion)
    function syncDays(){
      const days = Math.max(1, parseInt(weddingDaysEl.value) || 1);
      document.querySelectorAll('.daybased').forEach(el=> el.value = days);
    }

    // Calculation logic
    function toNumber(v){ return parseFloat(String(v).replace(/[^0-9.-]+/g,'')) || 0 }

    function recalc(){
      syncDays();
      const days = Math.max(1, parseInt(weddingDaysEl.value) || 1);
      const cur = currencyEl.value;

      // Items
      const photoUnit = toNumber(document.getElementById('price_photo').value);
      const videoUnit = toNumber(document.getElementById('price_video').value);
      const albumUnit = toNumber(document.getElementById('price_album').value);
      const droneUnit = toNumber(document.getElementById('price_drone').value);

      const qtyPhoto = Math.max(0, parseInt(document.getElementById('qty_photo').value) || 0);
      const qtyVideo = Math.max(0, parseInt(document.getElementById('qty_video').value) || 0);
      const qtyAlbum = Math.max(0, parseInt(document.getElementById('qty_album').value) || 0);
      const qtyDrone = Math.max(0, parseInt(document.getElementById('qty_drone').value) || 0);

      const linePhoto = photoUnit * days * qtyPhoto;
      const lineVideo = videoUnit * days * qtyVideo;
      const lineAlbum = albumUnit * qtyAlbum;
      const lineDrone = droneUnit * days * qtyDrone;

      document.getElementById('line_photo').textContent = formatCurrency(linePhoto, cur);
      document.getElementById('line_video').textContent = formatCurrency(lineVideo, cur);
      document.getElementById('line_album').textContent = formatCurrency(lineAlbum, cur);
      document.getElementById('line_drone').textContent = formatCurrency(lineDrone, cur);

      let subtotal = linePhoto + lineVideo + lineAlbum + lineDrone;
      document.getElementById('subtotal').textContent = formatCurrency(subtotal, cur);

      // Discount: automatic 10% if PKR, otherwise 0
      let discountPct = 0;
      if (cur === 'PKR') discountPct = 10;
      const discountAmt = round(subtotal * (discountPct/100));
      document.getElementById('discountPct').textContent = discountPct + '%';
      document.getElementById('discountAmt').textContent = formatCurrency(discountAmt, cur);

      // Tax placeholder (0)
      const taxAmt = 0;
      document.getElementById('taxAmt').textContent = formatCurrency(taxAmt, cur);

      const total = subtotal - discountAmt + taxAmt;
      document.getElementById('totalAmt').textContent = formatCurrency(total, cur);
    }

    function formatCurrency(amount, cur){
      const num = Number(amount) || 0;
      if (cur === 'PKR') return 'PKR ' + num.toLocaleString('en-US');
      if (cur === 'USD') return 'USD ' + num.toLocaleString('en-US', {minimumFractionDigits:2, maximumFractionDigits:2});
      return cur + ' ' + num.toLocaleString('en-US');
    }

    function round(v){ return Math.round((v + Number.EPSILON) * 100) / 100 }

    // Attach events
    ['qty_photo','qty_video','qty_album','qty_drone','weddingDays','currency'].forEach(id=>{
      const el = document.getElementById(id);
      el.addEventListener('input', recalc);
      el.addEventListener('change', recalc);
    });

    // Ensure day-based inputs follow weddingDays value but are readonly
    weddingDaysEl.addEventListener('input', recalc);

    // Reset helper
    function resetForm(){
      document.getElementById('qty_photo').value = 1;
      document.getElementById('qty_video').value = 1;
      document.getElementById('qty_album').value = 1;
      document.getElementById('qty_drone').value = 1;
      document.getElementById('weddingDays').value = 1;
      document.getElementById('currency').value = 'PKR';
      document.getElementById('albumNotes').value = '';
      recalc();
    }

    // initial calc
    recalc();
  </script>
</body>
</html>
  <!-- Footer / Contact -->
  <footer class="contact" id="contact">
    <div class="contact-left">
      <div class="big">Contact — Saqib Weddings</div>
      <div class="note">Phone: <strong>0316-2772095</strong> · Email: <a href="mailto:saqibweddings@gmail.com">saqibweddings@gmail.com</a></div>
      <div class="note">Instagram: <a href="https://www.instagram.com/saqibweddings" target="_blank">@saqibweddings</a> · TikTok: <a href="https://www.tiktok.com/@saqibweddings" target="_blank">@saqibweddings</a></div>
      <div style="margin-top:10px;color:var(--muted)">To submit a video for review, click “Send Video” above or email your file link (WeTransfer/Drive) to the address above.</div>
    </div>

    <div style="display:flex;flex-direction:column;align-items:flex-end;gap:10px">
      <div class="socials">
        <a href="https://www.instagram.com/saqibweddings" target="_blank">Instagram</a>
        <a href="https://www.tiktok.com/@saqibweddings" target="_blank">TikTok</a>
        <a href="mailto:saqibweddings@gmail.com">Email</a>
      </div>
      <div style="font-size:13px;color:var(--muted)">© <span id=""></span> 2016 Saqib Weddings</div>
    </div>
  </footer>

  <!-- Lightbox overlay for images/videos -->
  <div id="lightbox" class="lightbox" role="dialog" aria-hidden="true">
    <button class="lb-close" id="lbClose">✕</button>
    <div class="inner" id="lbInner"></div>
  </div>

  <script>
    // set year
    document.getElementById('curYear').innerText = new Date().getFullYear();

    // lightbox: click to open images/videos
    const lb = document.getElementById('lightbox');
    const lbInner = document.getElementById('lbInner');
    const lbClose = document.getElementById('lbClose');

    // open image in lightbox
    document.querySelectorAll('.img-card img').forEach(img => {
      img.style.cursor = 'zoom-in';
      img.addEventListener('click', () => {
        lbInner.innerHTML = '<img src="'+img.src+'" alt="">';
        lb.classList.add('open');
        lb.setAttribute('aria-hidden','false');
      });
    });

    // open video in lightbox when clicking poster area
    document.querySelectorAll('.video-card video').forEach((v,i) => {
      v.addEventListener('dblclick', () => { // double-click to open fullscreen in lightbox
        const src = v.querySelector('source') ? v.querySelector('source').src : v.src;
        lbInner.innerHTML = '<video controls autoplay src="'+src+'"></video>';
        lb.classList.add('open');
        lb.setAttribute('aria-hidden','false');
      });
    });

    lbClose.addEventListener('click', closeLB);
    lb.addEventListener('click', (e) => { if(e.target === lb) closeLB(); });

    function closeLB(){
      lb.classList.remove('open');
      lb.setAttribute('aria-hidden','true');
      lbInner.innerHTML = '';
    }

    // small prompt function for sending videos
    function promptSendVideo(){
      const mail = 'saqibweddings@gmail.com';
      const subject = encodeURIComponent('Video submission for Saqib Weddings');
      const body = encodeURIComponent('Hi Saqib,%0D%0A%0D%0AI would like to share a video for review. Here is a link to my file (WeTransfer/Drive/Dropbox):%0D%0A%0D%0A[Paste link here]%0D%0A%0D%0AThanks,%0D%0A[Your name]');
      window.location.href = `mailto:${mail}?subject=${subject}&body=${body}`;
    }

    // Optional: subtle parallax tilt for preview card on mouse move
    const preview = document.getElementById('previewCard');
    preview.addEventListener('mousemove', (e) => {
      const r = preview.getBoundingClientRect();
      const px = (e.clientX - r.left)/r.width - 0.5;
      const py = (e.clientY - r.top)/r.height - 0.5;
      preview.style.transform = `translateY(-8px) rotateX(${py * 6}deg) rotateY(${ -px * 8}deg)`;
    });
    preview.addEventListener('mouseleave', ()=> preview.style.transform = '');
  </script>





