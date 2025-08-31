<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>RetroTube 2009</title>
  <style>
    /* ===== 2009-esque Skin ===== */
    :root{
      --bg:#eaeaea;
      --card:#ffffff;
      --text:#111;
      --sub:#666;
      --accent:#cc181e; /* classic red */
      --nav-top:#f8f8f8;
      --nav-border:#cfcfcf;
      --link:#0033cc;
      --yellow:#ffcc00; /* subscribe */
      --tab:#f2f2f2;
      --tab-border:#d9d9d9;
    }
    html,body{margin:0;padding:0;background:var(--bg);color:var(--text);font:13px/1.45 Arial, Helvetica, sans-serif}
    a{color:var(--link);text-decoration:none}
    a:hover{text-decoration:underline}

    /* Header */
    .topbar{position:sticky;top:0;z-index:60;background:linear-gradient(#ffffff,#f2f2f2);border-bottom:1px solid var(--nav-border)}
    .bar{max-width:1200px;margin:0 auto;display:flex;align-items:center;gap:12px;padding:8px 12px}
    .logo{display:flex;align-items:center;gap:6px;font-weight:700;letter-spacing:0.2px}
    .logo .tube{display:inline-block;padding:2px 6px;border-radius:3px;background:var(--accent);color:white}
    .logo a{color:#000}
    .search{flex:1;display:flex;gap:0}
    .search input{flex:1;padding:7px;border:1px solid #bfbfbf;border-right:0;border-radius:2px 0 0 2px}
    .search button{padding:7px 12px;border:1px solid #bfbfbf;background:#efefef;border-radius:0 2px 2px 0;cursor:pointer}

    .right{margin-left:auto;display:flex;align-items:center;gap:10px}
    .signin{padding:5px 10px;border:1px solid #bfbfbf;background:#fff;border-radius:2px;cursor:pointer}

    /* Tabs */
    .tabs{background:var(--tab);border-bottom:1px solid var(--tab-border)}
    .tabs .inner{max-width:1200px;margin:0 auto;display:flex;gap:12px;padding:6px 12px}
    .tabs a{padding:5px 10px;border:1px solid transparent;border-bottom:0;border-radius:3px 3px 0 0;color:#333}
    .tabs a.active,.tabs a:hover{background:#fff;border-color:var(--tab-border)}

    /* Page */
    .page{max-width:1200px;margin:12px auto;display:grid;grid-template-columns:240px 1fr;gap:16px}
    .sidebar{background:#fff;border:1px solid #ddd;padding:10px}
    .sidegroup{margin-bottom:14px}
    .sidegroup h4{margin:8px 0 6px 0;font-size:12px;color:#444}
    .sidegroup a{display:block;padding:6px;border-radius:3px;color:#333}
    .sidegroup a.active,.sidegroup a:hover{background:#f6f6f6}

    .content{min-height:60vh}

    /* Home grid/list */
    .video-grid{display:grid;grid-template-columns:repeat(auto-fill, minmax(260px, 1fr));gap:14px}
    .card{background:var(--card);border:1px solid #ddd}
    .thumb{position:relative;aspect-ratio:16/9;background:#ddd;display:block}
    .thumb img{width:100%;height:100%;object-fit:cover;display:block}
    .duration{position:absolute;right:6px;bottom:6px;background:rgba(0,0,0,.85);color:#fff;font-size:11px;padding:1px 4px;border-radius:2px}
    .meta{padding:8px 10px}
    .title{font-weight:700;color:#000;display:block;margin-bottom:4px}
    .byline{color:var(--sub);font-size:11px}

    /* Watch page */
    .watch{display:grid;grid-template-columns:1fr 320px;gap:16px}
    .player{background:#000}
    .player iframe,.player video{width:100%;height:58vh}
    .watch .panel{background:#fff;border:1px solid #ddd;padding:10px}
    .watch h1{font-size:18px;margin:10px 0}
    .metarow{display:flex;flex-wrap:wrap;gap:10px;align-items:center;color:#444;font-size:12px}
    .subscribe{background:var(--yellow);border:1px solid #ccaa00;border-radius:3px;padding:4px 10px;font-weight:700;cursor:pointer}
    .subscribe.on{background:#ffd84d}
    .actions{display:flex;flex-wrap:wrap;gap:8px;margin:8px 0}
    .btn{padding:6px 10px;border:1px solid #ccc;background:#f5f5f5;border-radius:3px;cursor:pointer}

    /* Star ratings */
    .stars{display:inline-flex;direction:rtl}
    .stars input{display:none}
    .star{font-size:17px;color:#cfcfcf;cursor:pointer;padding:0 1px}
    .stars input:checked ~ label,.star.hover{color:#ffb400}

    /* Comments */
    .comment-box textarea{width:100%;min-height:70px;padding:8px;border:1px solid #ccc}
    .comment{border-top:1px solid #eee;padding:8px 0}
    .comment .who{font-weight:700}
    .comment .when{color:#888;font-size:11px}

    /* Forms */
    .form label{display:block;font-weight:700;margin:10px 0 4px}
    .form input,.form textarea,.form select{width:100%;padding:8px;border:1px solid #cfcfcf;border-radius:3px}

    /* Popover / modal */
    .popover{position:fixed;inset:0;display:none;align-items:center;justify-content:center;background:rgba(0,0,0,.35)}
    .popover.open{display:flex}
    .pop{background:#fff;border:1px solid #ccc;border-radius:4px;min-width:320px;max-width:92vw}
    .pop .hd{padding:10px;border-bottom:1px solid #eee;font-weight:700}
    .pop .bd{padding:10px}
    .pop .ft{padding:10px;border-top:1px solid #eee;display:flex;gap:8px;justify-content:flex-end}

    /* Footer */
    footer{margin:24px 0;color:#777;text-align:center}

    @media (max-width: 900px){
      .page{grid-template-columns:1fr}
      .watch{grid-template-columns:1fr}
      .player iframe,.player video{height:52vw}
      .tabs .inner{flex-wrap:wrap}
    }
  </style>
</head>
<body>
  <header class="topbar">
    <div class="bar">
      <div class="logo" aria-label="RetroTube home">
        <a href="#" title="RetroTube"><span>Retro</span><span class="tube">Tube</span></a>
      </div>
      <form class="search" id="searchForm" role="search" aria-label="Search videos">
        <input id="searchInput" type="search" placeholder="Search videos" aria-label="Search" />
        <button type="submit" title="Search">Search</button>
      </form>
      <div class="right">
        <a class="signin" href="#/account" id="acctBtn">Sign In</a>
      </div>
    </div>
    <nav class="tabs">
      <div class="inner" aria-label="Primary">
        <a href="#" id="navHome">Home</a>
        <a href="#/subscriptions" id="navSubs">Subscriptions</a>
        <a href="#/playlists" id="navPlaylists">Playlists</a>
        <a href="#/history" id="navHistory">History</a>
        <a href="#/watch-later" id="navWL">Watch Later</a>
        <a href="#/upload" id="navUpload">Upload</a>
      </div>
    </nav>
  </header>

  <main class="page">
    <aside class="sidebar" aria-label="Categories">
      <div class="sidegroup">
        <h4>Browse</h4>
        <a href="#" data-cat="All" class="cat-link active">All</a>
        <a href="#/c/Music" data-cat="Music" class="cat-link">Music</a>
        <a href="#/c/Gaming" data-cat="Gaming" class="cat-link">Gaming</a>
        <a href="#/c/Comedy" data-cat="Comedy" class="cat-link">Comedy</a>
        <a href="#/c/Education" data-cat="Education" class="cat-link">Education</a>
        <a href="#/c/News" data-cat="News" class="cat-link">News</a>
      </div>
      <div class="sidegroup">
        <h4>Quick Links</h4>
        <a href="#/trending">Trending</a>
        <a href="#/recent">Recently Uploaded</a>
        <a href="#/top-rated">Top Rated</a>
      </div>
    </aside>

    <section class="content" id="app" aria-live="polite"></section>
  </main>

  <footer>
    <small>RetroTube is a nostalgic, local-first video viewer. Add your own videos or link YouTube URLs. Optional backend sync supported. Not affiliated with YouTube.</small>
  </footer>

  <!-- Add-to-Playlist Popover -->
  <div class="popover" id="plPop">
    <div class="pop" role="dialog" aria-modal="true" aria-labelledby="plh">
      <div class="hd" id="plh">Add to playlist</div>
      <div class="bd">
        <div id="plList"></div>
        <div style="margin-top:8px">
          <input id="newPlName" placeholder="New playlist name" />
        </div>
      </div>
      <div class="ft">
        <button class="btn" id="plCancel">Cancel</button>
        <button class="btn" id="plSave">Save</button>
      </div>
    </div>
  </div>

  <script>
  // ===== Config (Backend optional) =====
  const CONFIG = {
    backendBaseURL: '', // e.g., https://your-api.example.com — leave empty for local-only
    apiKey: '' // optional
  };

  // ===== Storage Keys =====
  const STORAGE_KEY = 'retrotube_db_v2';
  const USER_KEY = 'retrotube_user';
  const THEME_KEY = 'retrotube_theme_2009';

  // ===== Utilities =====
  const $ = (sel, root=document) => root.querySelector(sel);
  const $$ = (sel, root=document) => Array.from(root.querySelectorAll(sel));
  const fmtViews = n => (n>=1e9? (n/1e9).toFixed(1)+'B': n>=1e6? (n/1e6).toFixed(1)+'M': n>=1e3? (n/1e3).toFixed(1)+'K': String(n));
  function timeAgo(dateStr){
    const d = new Date(dateStr);
    if(isNaN(d)) return '';
    const diff = (Date.now()-d.getTime())/1000;
    const map = [[31536000,'year'],[2592000,'month'],[604800,'week'],[86400,'day'],[3600,'hour'],[60,'minute']];
    for(const [s, label] of map){ if(diff >= s){ const v = Math.floor(diff/s); return v+ ' '+label + (v>1?'s':'') + ' ago'; } }
    return 'just now';
  }
  function idFromYouTubeURL(url){
    try{ const u = new URL(url); if(u.hostname.includes('youtu.be')) return u.pathname.replace('/',''); return u.searchParams.get('v') || ''; }catch(e){return ''}
  }
  function ytThumb(id){ return 'https://img.youtube.com/vi/'+id+'/hqdefault.jpg'; }

  // ===== Demo videos =====
  const demoVideos = [
    { id:'yt_dQw4w9WgXcQ', type:'youtube', videoId:'dQw4w9WgXcQ', title:'Never Gonna Give You Up', channel:'Rick Astley', views:1540000000, date:'2009-10-24', duration:'3:33', categories:['Music'], description:'Official music video — retro vibes!', tags:['music','80s'] },
    { id:'yt_9bZkp7q19f0', type:'youtube', videoId:'9bZkp7q19f0', title:'PSY - GANGNAM STYLE', channel:'officialpsy', views:4800000000, date:'2012-07-15', duration:'4:12', categories:['Music'], description:'Oppa Gangnam style.', tags:['kpop','dance'] },
    { id:'yt_kfVsfOSbJY0', type:'youtube', videoId:'kfVsfOSbJY0', title:'Friday - Rebecca Black', channel:'rebecca', views:170000000, date:'2011-03-14', duration:'3:48', categories:['Music','Comedy'], description:'It’s Friday, Friday…', tags:['viral'] },
    { id:'yt_J---aiyznGQ', type:'youtube', videoId:'J---aiyznGQ', title:'Charlie bit my finger!', channel:'HDCYT', views:900000000, date:'2007-05-22', duration:'0:56', categories:['Comedy'], description:'Classic internet time capsule.', tags:['classic'] },
    { id:'yt_oHg5SJYRHA0', type:'youtube', videoId:'oHg5SJYRHA0', title:'Never Gonna Give You Up (HD)', channel:'RickRoll', views:350000000, date:'2010-05-15', duration:'3:33', categories:['Music'], description:'You know the one.', tags:['meme'] },
    { id:'yt_fJ9rUzIMcZQ', type:'youtube', videoId:'fJ9rUzIMcZQ', title:'Queen – Bohemian Rhapsody', channel:'Queen Official', views:1800000000, date:'2008-08-01', duration:'6:00', categories:['Music'], description:'Is this the real life…', tags:['rock'] },
  ];

  // ===== DB shape =====
  let db = JSON.parse(localStorage.getItem(STORAGE_KEY) || 'null');
  if(!db){
    db = {
      videos: demoVideos,
      comments: {},        // videoId -> [ {who, txt, ts} ]
      ratings: {},         // videoId -> {sum, count, mine}
      subscriptions: {},   // channel -> bool
      watchLater: [],      // [videoId]
      views: {},           // videoId -> viewcount
      playlists: [],       // [ {id,name,createdAt,videoIds:[] } ]
      history: []          // [ {id, ts} ]
    };
    localStorage.setItem(STORAGE_KEY, JSON.stringify(db));
  }
  let currentUser = localStorage.getItem(USER_KEY) || 'Guest';

  function save(){ localStorage.setItem(STORAGE_KEY, JSON.stringify(db)); }

  // ===== Backend helpers (optional) =====
  function backendOn(){ return !!CONFIG.backendBaseURL; }
  async function api(path, opts={}){
    const base = CONFIG.backendBaseURL.endsWith('/') ? CONFIG.backendBaseURL.slice(0,-1) : CONFIG.backendBaseURL;
    const url = base + path;
    const headers = Object.assign({ 'Content-Type':'application/json' }, CONFIG.apiKey? { 'Authorization':'Bearer '+CONFIG.apiKey } : {});
    const res = await fetch(url, Object.assign({ headers }, opts));
    if(!res.ok) throw new Error('API '+res.status);
    return res.status===204? null : res.json();
  }
  // Contract (example):
  // GET /init -> { videos, comments, ratings, subscriptions, playlists, history }
  // POST /videos {video} -> {ok}
  // POST /videos/:id/comments {who,txt,ts}
  // POST /videos/:id/ratings {value}
  // POST /users/:user/subscriptions {channel, on}
  // POST /users/:user/playlists {id?, name, videoId?}
  // POST /users/:user/history {id, ts}
  async function backendInit(){
    if(!backendOn()) return;
    try{
      const data = await api('/init');
      ['videos','comments','ratings','subscriptions','playlists','history'].forEach(k=>{ if(data[k]) db[k] = data[k]; });
      save();
    }catch(e){ console.warn('Backend init failed, staying local', e); }
  }

  // ===== Routing =====
  window.addEventListener('hashchange', router);
  document.addEventListener('DOMContentLoaded', async ()=>{ await backendInit(); applyTheme(); router(); });

  function router(){
    const hash = location.hash.slice(1);
    highlightNav();
    if(hash.startsWith('/watch')){ const id = new URLSearchParams(hash.split('?')[1]||'').get('v'); return renderWatch(id); }
    if(hash.startsWith('/upload')) return renderUpload();
    if(hash.startsWith('/subscriptions')) return renderSubscriptions();
    if(hash.startsWith('/playlists')) return renderPlaylists();
    if(hash.startsWith('/history')) return renderHistory();
    if(hash.startsWith('/trending')) return renderHome('Trending');
    if(hash.startsWith('/recent')) return renderHome('Recent');
    if(hash.startsWith('/top-rated')) return renderHome('TopRated');
    if(hash.startsWith('/channel/')){ const ch = decodeURIComponent(hash.replace('/channel/','')); return renderChannel(ch); }
    if(hash.startsWith('/c/')){ const cat = decodeURIComponent(hash.replace('/c/','')); return renderHome('Category', cat); }
    if(hash.startsWith('/search')){ const q = new URLSearchParams(hash.split('?')[1]||'').get('q')||''; return renderHome('Search', null, q); }
    if(hash.startsWith('/account')) return renderAccount();
    return renderHome('All');
  }

  function highlightNav(){
    $$('#navHome, #navSubs, #navPlaylists, #navHistory, #navWL, #navUpload').forEach(a=>a.classList.remove('active'));
    if(location.hash.startsWith('#/subscriptions')) $('#navSubs').classList.add('active');
    else if(location.hash.startsWith('#/playlists')) $('#navPlaylists').classList.add('active');
    else if(location.hash.startsWith('#/history')) $('#navHistory').classList.add('active');
    else if(location.hash.startsWith('#/upload')) $('#navUpload').classList.add('active');
    else if(location.hash.startsWith('#/watch-later')) $('#navWL').classList.add('active');
    else $('#navHome').classList.add('active');
    $$('.cat-link').forEach(a=>a.classList.remove('active'));
    const cat = decodeURIComponent(location.hash.replace('#/c/',''));
    $$('.cat-link').forEach(a=>{ if(a.dataset.cat===cat) a.classList.add('active'); })
  }

  // Header search
  $('#searchForm').addEventListener('submit', e=>{ e.preventDefault(); const q = $('#searchInput').value.trim(); location.hash = '#/search?q='+encodeURIComponent(q); });
  document.addEventListener('keydown', e=>{ if(e.key==='/' && !['INPUT','TEXTAREA','SELECT'].includes(document.activeElement.tagName)){ e.preventDefault(); $('#searchInput').focus(); } });

  // ===== Renderers =====
  function renderHome(mode='All', category=null, query=''){
    const app = $('#app');
    let vids = [...db.videos];
    if(mode==='Trending') vids.sort((a,b)=> (b.views||0) - (a.views||0));
    if(mode==='Recent') vids.sort((a,b)=> new Date(b.date)-new Date(a.date));
    if(mode==='TopRated') vids.sort((a,b)=> (avgRating(b.id)) - (avgRating(a.id)) );
    if(category && category!=='All') vids = vids.filter(v=> (v.categories||[]).includes(category));
    if(mode==='Search' && query){
      const q = query.toLowerCase();
      vids = vids.filter(v=> v.title.toLowerCase().includes(q) || (v.channel||'').toLowerCase().includes(q) || (v.tags||[]).some(t=>t.toLowerCase().includes(q)) );
    }
    const heading = mode==='Search' ? 'Search results for \''+escapeHtml(query)+'\'' : (category && category!=='All' ? category : (mode==='All'?'Recommended':'Trending'));
    app.innerHTML = `
      <div class="card" style="padding:12px">
        <div style="display:flex;justify-content:space-between;align-items:center;gap:10px;flex-wrap:wrap">
          <h2 style="margin:6px 0">${heading}</h2>
          <div>
            <label style="margin-right:6px">Sort by</label>
            <select id="sortSel">
              <option value="relevance">Relevance</option>
              <option value="views">Views</option>
              <option value="date">Upload date</option>
              <option value="rating">Rating</option>
            </select>
          </div>
        </div>
        <div class="video-grid" id="grid"></div>
      </div>`;
    const grid = $('#grid'); vids.forEach(v=> grid.appendChild(videoCard(v)) );
    $('#sortSel').addEventListener('change', e=>{
      const val = e.target.value;
      if(val==='views') vids.sort((a,b)=>(b.views||0)-(a.views||0));
      else if(val==='date') vids.sort((a,b)=>new Date(b.date)-new Date(a.date));
      else if(val==='rating') vids.sort((a,b)=>avgRating(b.id)-avgRating(a.id));
      else vids.sort(()=>0);
      grid.innerHTML=''; vids.forEach(v=> grid.appendChild(videoCard(v)));
    });
    $$('.cat-link').forEach(a=> a.addEventListener('click', evt=>{ $$('.cat-link').forEach(x=>x.classList.remove('active')); evt.currentTarget.classList.add('active'); }));
  }

  function videoCard(v){
    const el = document.createElement('a');
    el.className = 'card';
    el.href = '#/watch?v='+encodeURIComponent(v.id);
    el.setAttribute('aria-label', v.title);
    const thumb = v.type==='youtube' ? ytThumb(v.videoId) : '';
    el.innerHTML = `
      <div class="thumb">${thumb?`<img alt="" src="${thumb}">`:'<div style="display:flex;align-items:center;justify-content:center;height:100%;color:#555">MP4</div>'}
        <span class="duration">${v.duration||''}</span>
      </div>
      <div class="meta">
        <span class="title">${escapeHtml(v.title)}</span>
        <div class="byline">${escapeHtml(v.channel||'')} • ${fmtViews(v.views||0)} views • ${timeAgo(v.date)}</div>
        <div class="byline">★ ${avgRating(v.id).toFixed(1)} / 5</div>
      </div>`;
    return el;
  }

  function renderWatch(id){
    const app = $('#app');
    const v = db.videos.find(x=>x.id===id);
    if(!v){ app.innerHTML = '<div class="card" style="padding:16px">Video not found.</div>'; return; }
    db.views[id] = (db.views[id]||v.views||0) + 1; v.views = db.views[id];
    recordHistory(id);
    save();
    const subbed = !!db.subscriptions[v.channel];
    const inWL = db.watchLater.includes(id);
    app.innerHTML = `
      <div class="watch">
        <div>
          <div class="player card">
            ${v.type==='youtube' ? `<iframe src="https://www.youtube.com/embed/${v.videoId}" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>`
            : `<video controls src="${v.src}"></video>`}
          </div>
          <div class="panel">
            <h1>${escapeHtml(v.title)}</h1>
            <div class="metarow">
              <span><strong>${fmtViews(v.views||0)}</strong> views</span>
              <span>• Uploaded ${timeAgo(v.date)}</span>
            </div>
            <div class="actions">
              <button class="btn" id="wlBtn">${inWL? '✓ In Watch Later' : '+ Watch Later'}</button>
              <button class="btn" id="addBtn">Add to Playlist</button>
              <button class="btn" id="shareBtn">Share</button>
            </div>
            <div style="margin:8px 0">
              <span style="margin-right:8px">Rate this video:</span>
              ${starWidgetHTML(id)}
              <span style="margin-left:8px;color:#555">Avg: <strong id="avg_${id}">${avgRating(id).toFixed(2)}</strong></span>
            </div>
            <div style="display:flex;align-items:center;gap:8px;margin:8px 0">
              <a class="title" href="#/channel/${encodeURIComponent(v.channel)}">${escapeHtml(v.channel)}</a>
              <button class="subscribe ${subbed?'on':''}" id="subBtn">${subbed?'Subscribed':'Subscribe'}</button>
            </div>
            <div style="white-space:pre-wrap;color:#333">${escapeHtml(v.description||'')}</div>
            <div style="margin-top:6px;color:#777">Tags: ${(v.tags||[]).map(t=>`<a href="#/search?q=${encodeURIComponent(t)}">#${escapeHtml(t)}</a>`).join(' ')}</div>
          </div>
          <div class="panel">
            <h3 style="margin:6px 0">Comments</h3>
            <div class="comment-box" style="margin:8px 0">
              <label for="cmt">Comment as <strong>${escapeHtml(currentUser)}</strong></label>
              <textarea id="cmt" placeholder="Say something nice..."></textarea>
              <div style="display:flex;gap:8px;margin-top:6px;align-items:center;flex-wrap:wrap">
                <input id="nameInput" placeholder="Name (optional)" style="flex:0 0 220px;padding:6px;border:1px solid #ccc" />
                <button class="btn" id="postBtn">Post</button>
              </div>
            </div>
            <div id="comments"></div>
          </div>
        </div>
        <div>
          <div class="panel">
            <h3 style="margin:6px 0">Up next</h3>
            <div id="upnext"></div>
          </div>
        </div>
      </div>`;
    $('#subBtn').addEventListener('click', async ()=>{
      db.subscriptions[v.channel] = !db.subscriptions[v.channel]; save();
      try{ if(backendOn()) await api('/users/'+encodeURIComponent(currentUser)+'/subscriptions', {method:'POST', body: JSON.stringify({ channel: v.channel, on: !!db.subscriptions[v.channel] })}); }catch(e){}
      router();
    });
    $('#wlBtn').addEventListener('click', ()=>{ const idx = db.watchLater.indexOf(id); if(idx>-1) db.watchLater.splice(idx,1); else db.watchLater.push(id); save(); router(); });
    $('#shareBtn').addEventListener('click', async ()=>{ const url = location.href; try{ await navigator.clipboard.writeText(url); alert('Link copied to clipboard!'); }catch(e){ prompt('Copy this link:', url); } });
    $('#addBtn').addEventListener('click', ()=> openPlaylistPopover(id));
    const list = db.comments[id] || [];
    renderComments(list);
    $('#postBtn').addEventListener('click', async ()=>{
      const txt = $('#cmt').value.trim(); const nm = $('#nameInput').value.trim(); if(!txt) return;
      const who = nm || currentUser || 'Guest'; const item = { who, txt, ts: Date.now() };
      db.comments[id] = [item, ...(db.comments[id]||[])]; save();
      try{ if(backendOn()) await api('/videos/'+encodeURIComponent(id)+'/comments', {method:'POST', body: JSON.stringify(item)}); }catch(e){}
      $('#cmt').value=''; $('#nameInput').value=''; renderComments(db.comments[id]);
    });
    function renderComments(items){
      const wrap = $('#comments');
      wrap.innerHTML = items.map(c=>{
        return '<div class="comment">'+
          '<div><span class="who">'+escapeHtml(c.who)+'</span> <span class="when">• '+timeAgo(c.ts)+'</span></div>'+
          '<div>'+linkify(escapeHtml(c.txt))+'</div>'+
        '</div>';
      }).join('');
    }
    const up = db.videos.filter(x=>x.id!==id && (x.categories||[]).some(c=> (v.categories||[]).includes(c))).slice(0,8);
    const cont = $('#upnext'); (up.length? up : db.videos.filter(x=>x.id!==id).slice(0,8)).forEach(x=> cont.appendChild(smallRow(x)));
    bindStarWidget(id);
  }

  function smallRow(v){
    const el = document.createElement('a');
    el.href = '#/watch?v='+encodeURIComponent(v.id);
    el.style.display='grid'; el.style.gridTemplateColumns='120px 1fr'; el.style.gap='8px'; el.style.margin='8px 0';
    const thumb = v.type==='youtube' ? ytThumb(v.videoId) : '';
    el.innerHTML = `
      <div class="thumb" style="aspect-ratio:16/9">${thumb?`<img alt="" src="${thumb}">`:'<div style="display:flex;align-items:center;justify-content:center;height:100%;color:#555">MP4</div>'}
        <span class="duration">${v.duration||''}</span>
      </div>
      <div>
        <div style="font-weight:700;color:#000">${escapeHtml(v.title)}</div>
        <div class="byline">${escapeHtml(v.channel||'')} • ${fmtViews(v.views||0)} views</div>
      </div>`;
    return el;
  }

  function starWidgetHTML(id){
    const val = userRating(id);
    return `
      <span class="stars" data-id="${id}">
        <input type="radio" name="rate-${id}" id="r5-${id}" value="5" ${val===5?'checked':''} /><label for="r5-${id}" class="star" title="5">★</label>
        <input type="radio" name="rate-${id}" id="r4-${id}" value="4" ${val===4?'checked':''} /><label for="r4-${id}" class="star" title="4">★</label>
        <input type="radio" name="rate-${id}" id="r3-${id}" value="3" ${val===3?'checked':''} /><label for="r3-${id}" class="star" title="3">★</label>
        <input type="radio" name="rate-${id}" id="r2-${id}" value="2" ${val===2?'checked':''} /><label for="r2-${id}" class="star" title="2">★</label>
        <input type="radio" name="rate-${id}" id="r1-${id}" value="1" ${val===1?'checked':''} /><label for="r1-${id}" class="star" title="1">★</label>
      </span>`;
  }
  function bindStarWidget(id){
    const wrap = document.querySelector(`.stars[data-id='${CSS.escape(id)}']`);
    if(!wrap) return;
    wrap.addEventListener('change', async e=>{
      if(e.target && e.target.value){ setUserRating(id, Number(e.target.value)); $('#avg_'+id).textContent = avgRating(id).toFixed(2); save(); try{ if(backendOn()) await api('/videos/'+encodeURIComponent(id)+'/ratings', {method:'POST', body: JSON.stringify({ value:Number(e.target.value) })}); }catch(err){} }
    });
    $$('.star', wrap).forEach(lbl=>{ lbl.addEventListener('mouseenter', ()=> lbl.classList.add('hover')); lbl.addEventListener('mouseleave', ()=> lbl.classList.remove('hover')); });
  }
  function userRating(id){ const r = db.ratings[id] || { sum:0, count:0, mine:0 }; return r.mine || 0; }
  function setUserRating(id, val){ const r = db.ratings[id] || { sum:0, count:0, mine:0 }; if(r.mine){ r.sum -= r.mine; } else { r.count += 1; } r.mine = val; r.sum += val; db.ratings[id] = r; }
  function avgRating(id){ const r = db.ratings[id]; return r? (r.sum / Math.max(r.count,1)) : 4.2; }

  // ===== Upload =====
  function renderUpload(){
    const app = $('#app');
    app.innerHTML = `
      <div class="card" style="padding:14px">
        <h2 style="margin:6px 0">Upload / Add Video</h2>
        <p style="color:#555">Add a YouTube link (we'll embed it) or an MP4 URL you host. Fill in details below.</p>
        <div class="form">
          <label>Title</label>
          <input id="u_title" placeholder="Video title" />
          <label>Channel / Uploader</label>
          <input id="u_channel" value="${escapeHtml(currentUser)}" />
          <label>Type</label>
          <select id="u_type">
            <option value="youtube">YouTube Link</option>
            <option value="mp4">Direct MP4 URL</option>
          </select>
          <label>YouTube or MP4 URL</label>
          <input id="u_url" placeholder="https://www.youtube.com/watch?v=... or https://.../video.mp4" />
          <label>Categories (comma-separated)</label>
          <input id="u_cats" placeholder="e.g., Music, Education" />
          <label>Tags (comma-separated)</label>
          <input id="u_tags" placeholder="e.g., tutorial, retro" />
          <label>Description</label>
          <textarea id="u_desc" rows="5" placeholder="Describe your video"></textarea>
          <div style="margin-top:10px;display:flex;gap:10px;align-items:center;flex-wrap:wrap">
            <button class="btn" id="u_save">Add Video</button>
            <small id="u_msg" style="color:#777"></small>
          </div>
        </div>
      </div>`;
    $('#u_save').addEventListener('click', async ()=>{
      const title = $('#u_title').value.trim(); const channel = $('#u_channel').value.trim() || 'Unknown';
      const type = $('#u_type').value; const url = $('#u_url').value.trim();
      const cats = $('#u_cats').value.split(',').map(s=>s.trim()).filter(Boolean);
      const tags = $('#u_tags').value.split(',').map(s=>s.trim()).filter(Boolean);
      const desc = $('#u_desc').value.trim();
      if(!title || !url){ $('#u_msg').textContent = 'Please provide a title and URL.'; return; }
      const now = new Date().toISOString();
      let rec = { id:'', type, title, channel, categories:cats, tags, description:desc, views:0, date: now, duration:'', src:'', videoId:'' };
      if(type==='youtube'){
        const vid = idFromYouTubeURL(url); if(!vid){ $('#u_msg').textContent = 'Could not parse YouTube link.'; return; }
        rec.id = 'yt_'+vid; rec.videoId = vid;
      } else { rec.id = 'mp4_'+Math.random().toString(36).slice(2,9); rec.src = url; }
      db.videos.unshift(rec); save();
      try{ if(backendOn()) await api('/videos', {method:'POST', body: JSON.stringify(rec)}); }catch(e){}
      $('#u_msg').textContent = 'Added! Redirecting…';
      setTimeout(()=> location.hash = '#/watch?v='+encodeURIComponent(rec.id), 300);
    });
  }

  // ===== Subscriptions =====
  function renderSubscriptions(){
    const app = $('#app'); const channels = Object.keys(db.subscriptions).filter(k=>db.subscriptions[k]);
    app.innerHTML = '<div class="card" style="padding:12px"><h2 style="margin:6px 0">Subscriptions</h2><div id="subs"></div></div>';
    const wrap = $('#subs'); if(channels.length===0){ wrap.innerHTML = '<p style="color:#555">You are not subscribed to any channels yet. Visit a video to subscribe.</p>'; return; }
    channels.forEach(ch=>{
      const list = db.videos.filter(v=>v.channel===ch).slice(0,12);
      const block = document.createElement('div'); block.style.margin='12px 0';
      block.innerHTML = '<h3 style="margin:8px 0"><a href="#/channel/'+encodeURIComponent(ch)+'">'+escapeHtml(ch)+'</a></h3><div class="video-grid"></div>';
      const grid = block.querySelector('.video-grid'); list.forEach(v=> grid.appendChild(videoCard(v)) ); wrap.appendChild(block);
    });
  }

  // ===== Watch Later =====
  function renderWatchLater(){
    const app = $('#app'); const vids = db.watchLater.map(id=> db.videos.find(v=>v.id===id)).filter(Boolean);
    app.innerHTML = '<div class="card" style="padding:12px"><h2 style="margin:6px 0">Watch Later</h2><div class="video-grid" id="grid"></div></div>';
    const grid = $('#grid'); if(vids.length===0){ grid.innerHTML = '<p style="color:#555">Your Watch Later list is empty.</p>'; return; }
    vids.forEach(v=> grid.appendChild(videoCard(v)) );
  }

  // ===== Channel =====
  function renderChannel(name){
    const app = $('#app'); const vids = db.videos.filter(v=>v.channel===name);
    const subbed = !!db.subscriptions[name]; const totalViews = vids.reduce((a,b)=>a+(b.views||0),0);
    app.innerHTML = `
      <div class="card" style="padding:14px">
        <div style="display:flex;gap:16px;align-items:center;flex-wrap:wrap">
          <div style="width:64px;height:64px;border-radius:4px;background:#ddd;display:flex;align-items:center;justify-content:center;font-weight:700">${escapeHtml(name[0]||'?')}</div>
          <div>
            <h2 style="margin:4px 0">${escapeHtml(name)}</h2>
            <div class="byline">${vids.length} videos • ${fmtViews(totalViews)} total views</div>
          </div>
          <div style="flex:1"></div>
          <button class="subscribe ${subbed?'on':''}" id="subBtn">${subbed?'Subscribed':'Subscribe'}</button>
        </div>
        <div class="video-grid" id="grid" style="margin-top:12px"></div>
      </div>`;
    $('#subBtn').addEventListener('click', async ()=>{
      db.subscriptions[name] = !db.subscriptions[name]; save();
      try{ if(backendOn()) await api('/users/'+encodeURIComponent(currentUser)+'/subscriptions', {method:'POST', body: JSON.stringify({ channel: name, on: !!db.subscriptions[name] })}); }catch(e){}
      router();
    });
    const grid = $('#grid'); vids.forEach(v=> grid.appendChild(videoCard(v)) );
  }

  // ===== Playlists =====
  function ensureDefaultPlaylists(){ if(!Array.isArray(db.playlists)) db.playlists = []; if(!db.playlists.some(p=>p.name==='Favorites')) db.playlists.push({ id: 'pl_fav', name: 'Favorites', createdAt: Date.now(), videoIds: [] }); }
  function openPlaylistPopover(videoId){
    ensureDefaultPlaylists(); const pop = $('#plPop'); const list = $('#plList');
    list.innerHTML = db.playlists.map(p=> '<label style="display:flex;align-items:center;gap:6px;margin:6px 0">\
        <input type="checkbox" value="'+p.id+'" '+(p.videoIds.includes(videoId)?'checked':'')+'>\
        <span>'+escapeHtml(p.name)+'</span>\
      </label>').join('');
    pop.classList.add('open');
    $('#plCancel').onclick = ()=> pop.classList.remove('open');
    $('#plSave').onclick = async ()=>{
      const chosen = Array.from(document.querySelectorAll('#plList input[type="checkbox"]')).filter(x=>x.checked).map(x=>x.value);
      db.playlists.forEach(p=>{ const i = p.videoIds.indexOf(videoId); if(chosen.includes(p.id)){ if(i===-1) p.videoIds.push(videoId); } else { if(i>-1) p.videoIds.splice(i,1); } });
      const nm = $('#newPlName').value.trim(); if(nm){ const id = 'pl_'+Math.random().toString(36).slice(2,9); db.playlists.push({ id, name:nm, createdAt: Date.now(), videoIds:[videoId] }); }
      save(); try{ if(backendOn()) await api('/users/'+encodeURIComponent(currentUser)+'/playlists', {method:'POST', body: JSON.stringify({ playlists: db.playlists })}); }catch(e){}
      pop.classList.remove('open');
    };
  }
  function renderPlaylists(){
    ensureDefaultPlaylists(); const app = $('#app');
    app.innerHTML = '<div class="card" style="padding:12px"><h2 style="margin:6px 0">Playlists</h2><div id="pls"></div></div>';
    const wrap = $('#pls'); if(db.playlists.length===0){ wrap.innerHTML = '<p style="color:#555">No playlists yet.</p>'; return; }
    db.playlists.forEach(pl=>{
      const vids = pl.videoIds.map(id=> db.videos.find(v=>v.id===id)).filter(Boolean);
      const block = document.createElement('div'); block.style.margin='12px 0';
      block.innerHTML = '<h3 style="margin:8px 0">'+escapeHtml(pl.name)+' <small class="byline">('+(vids.length)+')</small></h3><div class="video-grid"></div>';
      const grid = block.querySelector('.video-grid'); vids.forEach(v=> grid.appendChild(videoCard(v))); wrap.appendChild(block);
    });
  }

  // ===== History =====
  function recordHistory(id){ db.history = [{ id, ts: Date.now() }, ...db.history.filter(h=>h.id!==id)].slice(0,500); if(backendOn()) api('/users/'+encodeURIComponent(currentUser)+'/history', {method:'POST', body: JSON.stringify({ id, ts: Date.now() })}).catch(()=>{}); }
  function renderHistory(){
    const app = $('#app'); const items = db.history.slice(0,200);
    app.innerHTML = '<div class="card" style="padding:12px"><h2 style="margin:6px 0">History</h2><div class="video-grid" id="grid"></div></div>';
    const grid = $('#grid'); if(items.length===0){ grid.innerHTML = '<p style="color:#555">No history yet. Watch something!</p>'; return; }
    items.forEach(h=>{ const v = db.videos.find(x=>x.id===h.id); if(v) grid.appendChild(videoCard(v)); });
  }

  // ===== Account & Theme =====
  function renderAccount(){
    const app = $('#app'); const is2009 = localStorage.getItem(THEME_KEY) !== 'off';
    app.innerHTML = `
      <div class="card" style="padding:14px;max-width:720px">
        <h2 style="margin:6px 0">Account</h2>
        <div class="form">
          <label>Display name</label>
          <input id="acct_name" value="${escapeHtml(currentUser)}" />
          <div style="margin-top:10px;display:flex;gap:10px;align-items:center;flex-wrap:wrap">
            <button class="btn" id="acct_save">Save</button>
          </div>
          <hr style="margin:14px 0;border:none;border-top:1px solid #eee" />
          <label>Theme</label>
          <div>
            <label style="display:flex;gap:8px;align-items:center"><input type="checkbox" id="theme2009" ${is2009?'checked':''}/> Use 2009 skin</label>
          </div>
          <p class="byline" style="margin-top:8px">Backend: ${backendOn()? 'Connected' : 'Local-only'} (set <code>CONFIG.backendBaseURL</code> in the source to enable sync)</p>
        </div>
      </div>`;
    $('#acct_save').addEventListener('click', ()=>{ const name = $('#acct_name').value.trim() || 'Guest'; localStorage.setItem(USER_KEY, name); currentUser = name; alert('Saved!'); });
    $('#theme2009').addEventListener('change', e=>{ localStorage.setItem(THEME_KEY, e.target.checked? 'on':'off'); applyTheme(); });
  }
  function applyTheme(){ const on = localStorage.getItem(THEME_KEY) !== 'off'; document.body.classList.toggle('skin-2009', on); }

  // ===== Helpers =====
  function escapeHtml(str){ return (str||'').replace(/[&<>"]/g, s=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[s])); }
  function linkify(text){
    // simple: linkify words starting with http(s)://
    return text.split(' ').map(w=>{
      if(w.startsWith('http://') || w.startsWith('https://')) return '<a href="'+w+'" target="_blank" rel="noopener">'+w+'</a>';
      return w;
    }).join(' ');
  }

  // ===== Keyboard shortcuts =====
  document.addEventListener('keydown', e=>{
    if(e.target.closest('input, textarea, select')) return;
    if(e.key==='g'){ window.__gPressed = Date.now(); }
    if(e.key==='h' && window.__gPressed && Date.now()-window.__gPressed<800){ location.hash='#'; }
    if(e.key==='s' && window.__gPressed && Date.now()-window.__gPressed<800){ location.hash='#/subscriptions'; }
    if(e.key==='p' && window.__gPressed && Date.now()-window.__gPressed<800){ location.hash='#/playlists'; }
    if(e.key==='w' && window.__gPressed && Date.now()-window.__gPressed<800){ location.hash='#/watch-later'; }
  });

  // ===== Init =====
  if(!localStorage.getItem(USER_KEY)){ const uname = 'User'+Math.random().toString(36).slice(2,6); localStorage.setItem(USER_KEY, uname); currentUser = uname; } else { currentUser = localStorage.getItem(USER_KEY); }

  </script>
</body>
</html>

