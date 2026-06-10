# ASASFISIKAX2026
Bacalah Do'a dan Kerjakan dengan Jujur 
<!doctype html>
<html lang="id" class="h-full">
 <head><script src="/_sdk/telemetry_sdk.js"></script>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CBT Asas Fisika - Vektor</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="https://cdn.jsdelivr.net/npm/lucide@0.263.0/dist/umd/lucide.min.js"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800&amp;display=swap" rel="stylesheet">
  <style>
* { font-family: 'Plus Jakarta Sans', sans-serif; }
html, body { height: 100%; margin: 0; }
.app-wrapper { height: 100%; width: 100%; overflow-y: auto; }
.gradient-bg { background: linear-gradient(135deg, #0f172a 0%, #1e3a5f 50%, #0f172a 100%); }
.card-glass { background: rgba(255,255,255,0.05); backdrop-filter: blur(10px); border: 1px solid rgba(255,255,255,0.1); }
.btn-primary { background: linear-gradient(135deg, #2563eb, #1d4ed8); }
.btn-primary:hover { background: linear-gradient(135deg, #3b82f6, #2563eb); }
.question-card { background: rgba(255,255,255,0.95); }
.option-btn { transition: all 0.2s; border: 2px solid #e2e8f0; }
.option-btn:hover { border-color: #2563eb; background: #eff6ff; }
.option-btn.selected { border-color: #2563eb; background: #dbeafe; }
.toast { animation: slideIn 0.3s ease; }
@keyframes slideIn { from { transform: translateY(-20px); opacity:0; } to { transform: translateY(0); opacity:1; } }
.blocked-overlay { background: rgba(0,0,0,0.95); }
  </style>
  <style>body { box-sizing: border-box; }</style>
  <script src="/_sdk/data_sdk.js" type="text/javascript"></script>
 </head>
 <body class="h-full">
  <div class="app-wrapper gradient-bg" id="app">
   <!-- LOGIN PAGE -->
   <div id="loginPage" class="flex items-center justify-center min-h-full p-4">
    <div class="w-full max-w-md">
     <div class="card-glass rounded-2xl p-8 text-center">
      <img src="https://i.ibb.co.com/h1nmnd7C/unnamed.jpg" alt="Logo MAN IC" class="w-24 h-24 mx-auto rounded-full mb-4 object-cover" loading="lazy" onerror="this.style.background='#1e3a5f';this.alt='Logo';">
      <h1 class="text-2xl font-800 text-white mb-1" id="examTitle">Ujian CBT ASAS FISIKA</h1>
      <p class="text-blue-300 text-sm mb-1">KELAS X - VEKTOR</p>
      <p class="text-blue-400 text-xs mb-6">MAN INSAN CENDEKIA BENGKULU TENGAH</p>
      <div class="space-y-4 text-left">
       <div>
        <label class="text-blue-200 text-sm block mb-1">Nama Lengkap</label> <input id="inputName" type="text" class="w-full px-4 py-3 rounded-lg bg-white/10 border border-white/20 text-white placeholder-white/40 focus:outline-none focus:border-blue-400" placeholder="Masukkan nama lengkap">
       </div>
       <div>
        <label class="text-blue-200 text-sm block mb-1">NISN</label> <input id="inputNISN" type="text" class="w-full px-4 py-3 rounded-lg bg-white/10 border border-white/20 text-white placeholder-white/40 focus:outline-none focus:border-blue-400" placeholder="Masukkan NISN">
       </div>
       <div id="loginError" class="text-red-400 text-sm hidden"></div><button onclick="doLogin()" class="w-full btn-primary text-white font-600 py-3 rounded-lg mt-2">Masuk</button>
      </div>
      <div class="mt-6 pt-4 border-t border-white/10">
       <p class="text-blue-400/60 text-xs mb-3">👨‍💻 Dikembangkan oleh:</p>
       <div class="flex items-center gap-3 justify-center"><img src="https://i.ibb.co.com/ymSTBJVC/developer.jpg" alt="Yudi Maulana" class="w-10 h-10 rounded-full object-cover border border-blue-400" loading="lazy" onerror="this.style.background='#1e3a5f';">
        <div class="text-left">
         <p class="text-white text-xs font-600">Yudi Maulana</p>
         <p class="text-blue-300 text-xs">Developer</p>
        </div>
       </div>
      </div>
     </div><!-- Admin Link --> <button onclick="showAdminLogin()" class="mt-4 text-blue-500/40 text-xs hover:text-blue-300 transition">⚙️ Admin</button>
    </div>
   </div><!-- EXAM PAGE -->
   <div id="examPage" class="hidden min-h-full p-4">
    <div class="max-w-3xl mx-auto">
     <!-- Header -->
     <div class="card-glass rounded-xl p-4 mb-4 flex items-center justify-between">
      <div class="flex items-center gap-3">
       <img src="https://i.ibb.co.com/h1nmnd7C/unnamed.jpg" alt="Logo" class="w-10 h-10 rounded-full object-cover" loading="lazy" onerror="this.style.background='#1e3a5f';">
       <div>
        <p class="text-white font-700 text-sm" id="studentNameDisplay"></p>
        <p class="text-blue-300 text-xs" id="studentNISNDisplay"></p>
       </div>
      </div>
      <div class="text-right">
       <p class="text-white font-700 text-lg" id="timerDisplay">90:00</p>
       <p class="text-blue-300 text-xs">Sisa Waktu</p>
      </div>
     </div><!-- Warning Toast -->
     <div id="warningToast" class="hidden toast mb-4 rounded-xl p-4 text-center font-700"></div><!-- Question Area -->
     <div class="question-card rounded-xl p-6 mb-4" id="questionArea">
      <div class="flex items-center justify-between mb-4">
       <span class="bg-blue-600 text-white text-sm font-600 px-3 py-1 rounded-full" id="qNumber">Soal 1/30</span> <span class="text-gray-500 text-sm" id="qCategory"></span>
      </div>
      <div id="qImage" class="mb-4"></div>
      <p id="qText" class="text-gray-800 font-500 mb-6 text-lg"></p>
      <div id="qOptions" class="space-y-3"></div>
     </div><!-- Navigation -->
     <div class="flex items-center justify-between mb-4">
      <button onclick="prevQ()" class="bg-white/10 text-white px-5 py-2 rounded-lg font-500 hover:bg-white/20 transition" id="btnPrev">← Sebelumnya</button> <span class="text-white/60 text-sm" id="answeredCount">0/30 dijawab</span> <button onclick="nextQ()" class="btn-primary text-white px-5 py-2 rounded-lg font-500" id="btnNext">Selanjutnya →</button>
     </div><!-- Question Nav Grid -->
     <div class="card-glass rounded-xl p-4 mb-4">
      <p class="text-blue-200 text-sm mb-3 font-600">Navigasi Soal:</p>
      <div class="grid grid-cols-10 gap-2" id="qNavGrid"></div>
     </div><button onclick="confirmSubmit()" class="w-full bg-green-600 hover:bg-green-700 text-white font-700 py-3 rounded-lg transition">Kumpulkan Jawaban</button> <!-- Submit Confirmation -->
     <div id="submitConfirm" class="hidden card-glass rounded-xl p-6 mt-4 text-center">
      <p class="text-white font-700 text-lg mb-2">Yakin kumpulkan jawaban?</p>
      <p class="text-blue-300 text-sm mb-4" id="confirmInfo"></p>
      <div class="flex gap-3 justify-center">
       <button onclick="cancelSubmit()" class="bg-white/10 text-white px-6 py-2 rounded-lg">Batal</button> <button onclick="submitExam()" class="bg-green-600 text-white px-6 py-2 rounded-lg font-600">Ya, Kumpulkan</button>
      </div>
     </div>
    </div>
   </div><!-- RESULT PAGE -->
   <div id="resultPage" class="hidden min-h-full p-4">
    <div class="max-w-2xl mx-auto">
     <div class="card-glass rounded-2xl p-8 text-center mb-6">
      <div class="text-6xl mb-4">
       📊
      </div>
      <h2 class="text-2xl font-800 text-white mb-2">Hasil Ujian</h2>
      <p class="text-blue-300 mb-6" id="resultName"></p>
      <div class="bg-white/10 rounded-xl p-6 mb-6">
       <p class="text-5xl font-800 text-white" id="resultScore">0</p>
       <p class="text-blue-300">Skor</p>
      </div>
      <div class="grid grid-cols-3 gap-3 text-center">
       <div class="bg-green-500/20 rounded-lg p-3">
        <p class="text-green-300 font-700 text-xl" id="resultCorrect">0</p>
        <p class="text-green-400 text-xs">Benar</p>
       </div>
       <div class="bg-red-500/20 rounded-lg p-3">
        <p class="text-red-300 font-700 text-xl" id="resultWrong">0</p>
        <p class="text-red-400 text-xs">Salah</p>
       </div>
       <div class="bg-yellow-500/20 rounded-lg p-3">
        <p class="text-yellow-300 font-700 text-xl" id="resultEmpty">0</p>
        <p class="text-yellow-400 text-xs">Kosong</p>
       </div>
      </div>
     </div><!-- Leaderboard -->
     <div class="card-glass rounded-2xl p-6 mb-6">
      <h3 class="text-white font-800 text-lg mb-4">📋 Papan Peringkat</h3>
      <div id="leaderboardList" class="space-y-2"></div>
     </div><!-- Logout Button --> <button onclick="backToLogin()" class="w-full bg-gradient-to-r from-blue-600 to-blue-500 hover:from-blue-700 hover:to-blue-600 text-white font-700 py-4 rounded-xl transition">← Kembali ke Dashboard</button>
    </div>
   </div><!-- BLOCKED OVERLAY -->
   <div id="blockedOverlay" class="hidden blocked-overlay fixed inset-0 z-50 flex items-center justify-center p-4">
    <div class="bg-red-950 border-2 border-red-500 rounded-2xl p-8 text-center max-w-md w-full">
     <div class="text-6xl mb-4">
      🚫
     </div>
     <h2 class="text-2xl font-800 text-red-400 mb-2">AKUN DIBLOKIR</h2>
     <p class="text-red-200 mb-4">Anda telah melanggar aturan ujian sebanyak 3 kali. Akun Anda diblokir permanen.</p>
     <div class="bg-red-900/50 rounded-lg p-4 text-left">
      <p class="text-red-300 font-600 text-sm mb-2">Untuk membuka blokir:</p>
      <p class="text-red-200 text-sm">Hubungi Admin/Guru pengawas untuk membuka blokir akun Anda.</p>
     </div>
    </div>
   </div><!-- ADMIN LOGIN MODAL -->
   <div id="adminLoginModal" class="hidden fixed inset-0 z-50 flex items-center justify-center p-4 bg-black/80">
    <div class="bg-slate-800 rounded-2xl p-6 max-w-sm w-full">
     <h3 class="text-white font-700 text-lg mb-4">Admin Login</h3><input id="adminPass" type="password" class="w-full px-4 py-3 rounded-lg bg-white/10 border border-white/20 text-white mb-3" placeholder="Password Admin">
     <div id="adminError" class="text-red-400 text-sm hidden mb-3"></div>
     <div class="flex gap-3">
      <button onclick="hideAdminLogin()" class="flex-1 bg-white/10 text-white py-2 rounded-lg">Batal</button> <button onclick="doAdminLogin()" class="flex-1 bg-blue-600 text-white py-2 rounded-lg font-600">Masuk</button>
     </div>
    </div>
   </div><!-- ADMIN PANEL -->
   <div id="adminPage" class="hidden min-h-full p-4">
    <div class="max-w-4xl mx-auto">
     <div class="card-glass rounded-xl p-6 mb-4">
      <div class="flex items-center justify-between">
       <h2 class="text-white font-800 text-xl">🛡️ Admin Dashboard</h2><button onclick="logoutAdmin()" class="bg-red-600/20 text-red-300 px-4 py-2 rounded-lg text-sm hover:bg-red-600/40">Logout</button>
      </div>
     </div><!-- Statistics -->
     <div class="grid grid-cols-4 gap-3 mb-4">
      <div class="card-glass rounded-xl p-4 text-center">
       <p class="text-blue-300 text-sm">Total Siswa</p>
       <p class="text-white font-800 text-2xl">113</p>
      </div>
      <div class="card-glass rounded-xl p-4 text-center">
       <p class="text-green-300 text-sm">Selesai Ujian</p>
       <p class="text-white font-800 text-2xl" id="statCompleted">0</p>
      </div>
      <div class="card-glass rounded-xl p-4 text-center">
       <p class="text-yellow-300 text-sm">Rata-rata Skor</p>
       <p class="text-white font-800 text-2xl" id="statAverage">0</p>
      </div>
      <div class="card-glass rounded-xl p-4 text-center">
       <p class="text-red-300 text-sm">Terblokir</p>
       <p class="text-white font-800 text-2xl" id="statBlocked">0</p>
      </div>
     </div><!-- Tabs -->
     <div class="card-glass rounded-xl p-4 mb-4 flex gap-4 border-b border-white/10">
      <button onclick="switchAdminTab('results')" id="tabResults" class="pb-2 px-2 font-600 text-white border-b-2 border-blue-500 transition">📊 Hasil Ujian</button> <button onclick="switchAdminTab('blocked')" id="tabBlocked" class="pb-2 px-2 font-600 text-white/60 hover:text-white transition">🚫 Siswa Terblokir</button> <button onclick="switchAdminTab('evaluation')" id="tabEval" class="pb-2 px-2 font-600 text-white/60 hover:text-white transition">✅ Evaluasi</button> <button onclick="switchAdminTab('reset')" id="tabReset" class="pb-2 px-2 font-600 text-white/60 hover:text-white transition">🔄 Reset</button>
     </div><!-- Results Tab -->
     <div id="tabResultsContent" class="card-glass rounded-xl p-6 mb-4">
      <input id="searchResults" type="text" placeholder="Cari nama atau NISN..." class="w-full px-4 py-2 rounded-lg bg-white/10 border border-white/20 text-white placeholder-white/40 mb-4" onkeyup="filterResults()">
      <div id="resultsList" class="space-y-2"></div>
      <p id="noResults" class="text-blue-300/60 text-sm">Belum ada hasil ujian.</p>
     </div><!-- Blocked Tab -->
     <div id="tabBlockedContent" class="hidden card-glass rounded-xl p-6 mb-4">
      <div id="blockedList" class="space-y-2"></div>
      <p id="noBlocked" class="text-blue-300/60 text-sm">Tidak ada siswa yang terblokir.</p>
     </div><!-- Evaluation Tab -->
     <div id="tabEvalContent" class="hidden">
      <div class="grid grid-cols-3 gap-3 mb-4">
       <div class="card-glass rounded-xl p-4 text-center">
        <p class="text-green-300 text-sm">🟢 Sangat Baik</p>
        <p class="text-white font-800 text-2xl" id="evalExcellent">0</p>
       </div>
       <div class="card-glass rounded-xl p-4 text-center">
        <p class="text-yellow-300 text-sm">🟡 Baik</p>
        <p class="text-white font-800 text-2xl" id="evalGood">0</p>
       </div>
       <div class="card-glass rounded-xl p-4 text-center">
        <p class="text-red-300 text-sm">🔴 Perlu Perbaikan</p>
        <p class="text-white font-800 text-2xl" id="evalPoor">0</p>
       </div>
      </div>
      <div class="card-glass rounded-xl p-6">
       <div id="evalList" class="space-y-3"></div>
       <p id="noEval" class="text-blue-300/60 text-sm">Belum ada data evaluasi.</p>
      </div>
     </div><!-- Reset Tab -->
     <div id="tabResetContent" class="hidden card-glass rounded-xl p-6 mb-4">
      <h3 class="text-white font-800 text-lg mb-6">🔄 Reset Data Ujian</h3>
      <div class="space-y-3">
       <div class="bg-red-500/10 border border-red-500/20 rounded-lg p-4">
        <p class="text-red-300 font-600 mb-2">⚠️ PERINGATAN: Aksi ini tidak dapat dibatalkan!</p>
        <p class="text-red-200 text-sm mb-4">Reset akan menghapus semua data hasil ujian, siswa terblokir, dan mereset sistem ke kondisi awal.</p><button onclick="confirmReset()" class="w-full bg-red-600 hover:bg-red-700 text-white font-600 py-2 rounded-lg transition">🔴 Reset Semua Data</button>
       </div>
       <div class="bg-yellow-500/10 border border-yellow-500/20 rounded-lg p-4">
        <p class="text-yellow-300 font-600 mb-2">🟡 Reset Siswa Terblokir</p>
        <p class="text-yellow-200 text-sm mb-4">Hapus daftar siswa terblokir dan buka blokir semua akun siswa.</p><button onclick="confirmResetBlocked()" class="w-full bg-yellow-600 hover:bg-yellow-700 text-white font-600 py-2 rounded-lg transition">Reset Blokir</button>
       </div>
       <div class="bg-green-500/10 border border-green-500/20 rounded-lg p-4">
        <p class="text-green-300 font-600 mb-2">🟢 Reset Hasil Ujian</p>
        <p class="text-green-200 text-sm mb-4">Hapus semua hasil ujian siswa tetapi pertahankan daftar siswa terblokir.</p><button onclick="confirmResetResults()" class="w-full bg-green-600 hover:bg-green-700 text-white font-600 py-2 rounded-lg transition">Reset Hasil</button>
       </div>
      </div>
      <div id="resetConfirm" class="hidden mt-4 card-glass rounded-xl p-4 text-center border-2 border-red-500">
       <p class="text-white font-700 mb-3" id="resetConfirmText"></p>
       <div class="flex gap-3 justify-center"><button onclick="cancelReset()" class="bg-white/10 text-white px-6 py-2 rounded-lg font-600">Batal</button> <button onclick="doReset()" id="resetConfirmBtn" class="px-6 py-2 rounded-lg font-600 text-white">Konfirmasi</button>
       </div>
      </div>
     </div>
    </div>
   </div>
   <script>
// ===== DATA =====
const students = [
["AFIF ARINAL HAQ","0103988938"],["AL HUSNAINI THOIBAH","3098997480"],["FADHIL SYAIRAZI SUTOPO","0101072432"],["MUHAMMAD FATHAN FAUZIL AZIZ","0101986656"],["ZAKIA ALHANIYAH","0097330842"],["FARIZAL AZIZ","0103629309"],["FATTIYAH LEVIANO","0099791787"],["THALITA AZ ZAHRA","3109688097"],["SHOFYIA YASMINE HUMAYROH","3105770187"],["HIRAR MASYA","0102108565"],["ADINDA AIDILLA SYAFITRI","0094334742"],["ARDINE DANISWARA MURYADIN","0105859839"],["RAISSA ATHIFAH","0106759658"],["RASYA PUTRAWANSYAH","0106398097"],["M. ALEXA HERDIAN","0099808940"],["M. SAYYID HIDAYATULLAH","3109955221"],["MEISSY CALLYSTA PERMANA","0101081182"],["MILLA DINA NUR ZAHRA","3107208991"],["MUHAMMAD ADNAN HAFIZH S.","0099181056"],["NAUFAL HABIBUR RAHMAN","0107080526"],["THORIQ AL HAYYAN","0095212570"],["JUNITA PUTRI CANISKA","0108352080"],["BELLA PUTRI MAHARANI","0103166780"],["NATASYA MULYANINGSIH","0103085469"],["RIZKY AKHMAD","3098403676"],["DERRY FAKHLEVIE","0102044339"],["IKHSAN NURDIANTO","0119172247"],["MUHAMMAD HAFID HABIBI","3109105219"],["BONITA DWI ASYIFA","0106453243"],["ALIFA HEFRIANI","0108296139"],["INTAN AULIA PUTRI","3101627657"],["SIVA ALIFIANA ZAHRA","0103908096"],["OKTA WAHYU PRATIWI","0097627918"],["AHIRA MUTIA RAMADHANI","0109052498"],["AHMAD JAFIN FAHLEVI","0117576139"],["FADLI AROYAN","0105621421"],["ZATASYA NUR RAMADHANI","0108148858"],["RENNAYU DESMIN PUTRI","0101493679"],["AZRA LAILA MASYRIFAH","0109405505"],["FIKRIYA MUZAKKI","0106013573"],["M.DAFFA GALENDA HERYANTO","0108458437"],["MEUTYA SABRINA","0105449745"],["MUHAMMAD AHZA NUFAIL","0104816821"],["RATU BUNGA CITRA PERDANA","3100672932"],["SUBHAN ANUGRAH","0106608683"],["TSALISA AZZAHRA","0105293907"],["M. ALIF IFFATURROHMAN","0104117726"],["MUHAMMAD DARREL HERMANSYAH","0109381573"],["ROMY KURNIAWAN","0101655409"],["SALSABILA HENDRA PUTRI","0114658262"],["VIONA MAILENI RAHAYU","0108857831"],["ALFINZA PRATAMA","0096192329"],["RAFFI ALFAIRUS AGSA","3104869356"],["FILANDO NOTO ARNANDA","0107590882"],["AINUHA KAELA SURRAIYA","0101582101"],["AMIRAH ZAHIRAH PRAMONO","0108325125"],["CALLISTA ANDIRA FATHARANI","0093521006"],["DIO RENZA OKTOVIANDI","0117400006"],["FADLY YUANZA","0101557600"],["IQBAL HIDAYAT","0098031669"],["JECINDA HANANTRI ISKANDAR","0107256961"],["AFIF LUQMAN ISKANDAR","3109820563"],["FATIHATUN NISAK","3101028825"],["M.KAUTSAR RIZQY","0091446543"],["M. IBRAHIM","0105007175"],["MUTIA AMBAR ERYN AL HASANAH","0102681898"],["PUTI NAZHIFAH ATTHAYA","0103190265"],["SYAFA NABILLA YANTRI","0094658131"],["VIORAHMATIA ELIZA","0112937838"],["AISYAH MEIDINA PUTRI","0101979883"],["KAYSAN NAWFAL ALI","3105845314"],["MUHAMAD FAIZ NUR ALAM","0103965655"],["MUHAMMAD DHAFIN AZRILLAH","0108169516"],["SYAHVIRA NURSYIFA","0107417975"],["AIRA ANINDYA PERMATA","0108367592"],["RAFIQ NAUFAL PUTRA FELONI","0107211842"],["ALIN ADI SAPUTRA","0091906364"],["CHICI HERLINA","0093912368"],["SEPTI AZIZAH","0106654323"],["M. LUTHFI FAIRUZ","0097916251"],["ASYFA FADHILLA ANDRIADI","0102549300"],["DIOSATRIA RABBAHUL VILLA","3107338919"],["FAISHAL RAJABI ABIMANYU","0108407245"],["HAFIZ AFIF AMAMI","0116743084"],["WILLIAM ASSIDIK","0109119237"],["WAFIQI DIAHNISSA AULIA","0102497498"],["JESICHA ADELLARAFLESIA","0105066684"],["CHIA PRINCES FINO","0107209793"],["KANZA AMANDA","0108868801"],["KHANSA HUMAIRA ADILAH","0091715147"],["M. HARRY RAHMANTIO","0109316215"],["MUHAMMAD RAIHAN ALFARIZI","0104277804"],["MUTIARA RIZKIA SALSABIL ARIFIN","0109008437"],["QUEENSHA QEILA EFENDRI","0103346973"],["NAJWA AURIMA","0108406815"],["FARHAN MAULANA DIWANGGA","0097775847"],["KHALIF FADLAN RENDRAPATI","0098357873"],["SHERIN HAFIZA","0102158975"],["KHAIRA INTAN SYAHARA PULUNGAN","0102869836"],["MUHAMMAD RAMZY SETIAWAN","0102558895"],["RAISAH RADIFAH","0095899970"],["AKHRAENY RAHAYU","0096413070"],["ANDARU AZZA PRAWIRA","0103202537"],["AZIZAH NASYWA IRAWAN","0108105335"],["HANIF ARRIFQI","0107067717"],["ZAHRA TALITA","0108560944"],["CLARA APRILIA","0108589047"],["GHEA RAMADANI","3099581001"],["M. RADITYA FAIZ KHOMEINI","0101481751"],["SYIFA NUR SHABRINA","3104476772"],["RAID ABBIYYU DZAKWAN","0114114271"],["MUHAMMAD ZAKWAN HAFIZHI AHTARSI","0102872869"],["MUHAMMAD FARRAAS RAMADHAN","0102659413"],["MUHAMAD FIQRI FADILLAH","0101573867"],["ZASKIA ALIFAH HUMAIRA","0107578052"]
];

const ADMIN_PASS = "ASAS2026";

const questions = [
{img:"https://i.ibb.co.com/200ngbCg/s-10.png",text:"Tentukan resultan vektor pada gambar di atas!",options:["15 î + 10√3 ĵ","32,5 î + 12,5√3 ĵ","15 î + 20√3 ĵ","10 î + 15√3 ĵ","20 î + 10√3 ĵ"],answer:0,cat:"Penjumlahan Vektor"},
{img:"https://i.ibb.co.com/qYKRmcYP/s1.png",text:"Tentukan besar resultan vektor pada gambar!",options:["√67","2√67","3√67","4√67","6√67"],answer:1,cat:"Penjumlahan Vektor"},
{img:"https://i.ibb.co.com/FbzT1qFh/s2.png",text:"Tentukan resultan gaya pada gambar!",options:["15 N ke kiri","15 N ke kanan","9 N ke kiri","9 N ke kanan","6 N ke kiri"],answer:2,cat:"Penjumlahan Vektor"},
{img:"https://i.ibb.co.com/Vcj6yFj6/s3.png",text:"Tentukan resultan dan arah gaya pada gambar!",options:["5 N ke arah 45°","10 N ke arah 30°","20 N ke arah 45°","5 N ke arah 60°","10 N ke arah 60°"],answer:1,cat:"Penjumlahan Vektor"},
{img:"https://i.ibb.co.com/sdszCCgR/s5.png",text:"Tentukan besar resultan vektor!",options:["5√3","10√3","20√3","20√5","20√7"],answer:2,cat:"Penjumlahan Vektor"},
{img:"https://i.ibb.co.com/0Rd9bFGx/s9.png",text:"Tentukan besar resultan vektor pada gambar!",options:["0","6","6√3","12","12√3"],answer:1,cat:"Penjumlahan Vektor"},
{text:"Jika A = 3î + 4ĵ dan B = 2î − ĵ, tentukan A + B!",options:["5î + 3ĵ","î + 5ĵ","5î − 3ĵ","î + 3ĵ","6î + 3ĵ"],answer:0,cat:"Penjumlahan Vektor"},
{text:"Vektor P = 6î − 2ĵ dan Q = −3î + 5ĵ. Tentukan P + Q!",options:["3î + 3ĵ","9î − 7ĵ","3î − 3ĵ","−3î + 3ĵ","9î + 3ĵ"],answer:0,cat:"Penjumlahan Vektor"},
{text:"Jika A = 4î + 2ĵ, B = −î + 3ĵ, dan C = 2î − 4ĵ, tentukan A + B + C!",options:["5î + ĵ","7î − ĵ","5î − ĵ","3î + ĵ","6î + 2ĵ"],answer:0,cat:"Penjumlahan Vektor"},
{text:"Dua vektor masing-masing 5 N dan 12 N saling tegak lurus. Besar resultannya adalah...",options:["7 N","13 N","17 N","10 N","15 N"],answer:1,cat:"Penjumlahan Vektor"},
{text:"Vektor A = 8î dan B = 6ĵ. Besar resultan A + B adalah...",options:["14","10","2","√100","√14"],answer:1,cat:"Penjumlahan Vektor"},
{text:"Jika A = 5î + 2ĵ dan B = 3î + 7ĵ, tentukan A − B!",options:["2î − 5ĵ","8î + 9ĵ","−2î + 5ĵ","2î + 5ĵ","8î − 5ĵ"],answer:0,cat:"Pengurangan Vektor"},
{text:"Vektor P = 7î − 3ĵ dan Q = 4î + 2ĵ. Tentukan P − Q!",options:["3î − 5ĵ","11î − ĵ","−3î + 5ĵ","3î + 5ĵ","11î − 5ĵ"],answer:0,cat:"Pengurangan Vektor"},
{text:"Jika A = −2î + 6ĵ dan B = 4î − 3ĵ, tentukan A − B!",options:["−6î + 9ĵ","2î + 3ĵ","6î − 9ĵ","−6î − 9ĵ","2î − 9ĵ"],answer:0,cat:"Pengurangan Vektor"},
{text:"Vektor R = 10î + 4ĵ dan S = 10î + 4ĵ. Tentukan R − S!",options:["0","20î + 8ĵ","20î","8ĵ","−20î"],answer:0,cat:"Pengurangan Vektor"},
{text:"Jika A = î + ĵ dan B = 3î − 2ĵ, besar |A − B| adalah...",options:["√13","√5","5","13","√10"],answer:0,cat:"Pengurangan Vektor"},
{text:"Jika A = 3î + 4ĵ dan B = 2î − ĵ, tentukan A · B!",options:["2","10","−2","6","14"],answer:0,cat:"Perkalian Titik"},
{text:"Vektor P = 5î + 2ĵ dan Q = −1î + 3ĵ. Tentukan P · Q!",options:["1","−1","11","13","7"],answer:0,cat:"Perkalian Titik"},
{text:"Jika A = 4î − 3ĵ dan B = 2î + 6ĵ, tentukan A · B!",options:["−10","26","10","−26","0"],answer:0,cat:"Perkalian Titik"},
{text:"Dua vektor A dan B memiliki besar masing-masing 6 dan 8. Jika sudut antara keduanya 60°, tentukan A · B!",options:["24","48","24√3","48√3","12"],answer:0,cat:"Perkalian Titik"},
{text:"Jika A = î + 2ĵ + 3k̂ dan B = 2î − î + k̂, tentukan A · B!",options:["3","5","7","1","−1"],answer:0,cat:"Perkalian Titik"},
{text:"Vektor A = 6î dan B = 4ĵ. Tentukan A · B!",options:["0","24","10","−24","2"],answer:0,cat:"Perkalian Titik"},
{text:"Jika A = 2î + 3ĵ dan B = î − 2ĵ, tentukan A × B!",options:["−7k̂","7k̂","−î","5k̂","k̂"],answer:0,cat:"Perkalian Silang"},
{text:"Vektor P = î + 2ĵ + 3k̂ dan Q = 2î + 3ĵ + k̂. Komponen î dari P × Q adalah...",options:["−7","7","−5","5","1"],answer:0,cat:"Perkalian Silang"},
{text:"Jika A = 3î dan B = 4ĵ, tentukan A × B!",options:["12k̂","−12k̂","0","7k̂","12î"],answer:0,cat:"Perkalian Silang"},
{text:"Vektor A = î − ĵ + 2k̂ dan B = 2î + ĵ − k̂. Tentukan komponen ĵ dari A × B!",options:["5ĵ","−5ĵ","3ĵ","−3ĵ","ĵ"],answer:0,cat:"Perkalian Silang"},
{text:"Jika |A| = 5, |B| = 4, dan sudut antara A dan B adalah 30°, maka |A × B| = ...",options:["10","20","10√3","20√3","5"],answer:0,cat:"Perkalian Silang"},
{text:"Jika A = 3î + 4ĵ dan B = 4î + 3ĵ, tentukan cos θ antara A dan B!",options:["24/25","25/24","7/25","1","12/25"],answer:0,cat:"Sudut Antar Vektor"},
{text:"Vektor A = î + ĵ dan B = î − ĵ. Sudut antara A dan B adalah...",options:["90°","0°","45°","180°","60°"],answer:0,cat:"Sudut Antar Vektor"},
{text:"Jika A = 2î + 2ĵ dan B = −2î + 2ĵ, tentukan cos θ!",options:["0","1","−1","1/2","√2/2"],answer:0,cat:"Sudut Antar Vektor"},
];

// ===== STATE =====
let currentStudent = null;
let currentQ = 0;
let answers = new Array(30).fill(-1);
let timer = 90 * 60;
let timerInterval = null;
let warnings = 0;
let blockedStudents = JSON.parse(localStorage.getItem('cbt_blocked') || '{}');
let examResults = JSON.parse(localStorage.getItem('cbt_results') || '[]');

// Exam schedule: Thursday, June 11, 2026 at 07:15 - 09:45
const EXAM_DATE = new Date(2026, 5, 11, 7, 15, 0); // June 11, 2026 07:15
const EXAM_END = new Date(2026, 5, 11, 9, 45, 0); // June 11, 2026 09:45

// ===== LOGIN =====
function checkExamSchedule() {
  const now = new Date();
  const dayOfWeek = now.getDay(); // 0=Sunday, 4=Thursday
  
  if (dayOfWeek !== 4) {
    return { valid: false, message: "❌ Ujian hanya bisa dilaksanakan pada hari KAMIS" };
  }
  
  const examStart = new Date(EXAM_DATE);
  const examEnd = new Date(EXAM_END);
  
  if (now < examStart) {
    const timeLeft = Math.ceil((examStart - now) / (1000 * 60));
    return { valid: false, message: `⏰ Ujian belum dimulai. Jadwal: Kamis, 11 Juni 2026 pukul 07:15\nWaktu tersisa: ${timeLeft} menit` };
  }
  
  if (now > examEnd) {
    return { valid: false, message: "⛔ Ujian sudah berakhir (batas akhir: 09:45)" };
  }
  
  return { valid: true };
}

function doLogin() {
  const name = document.getElementById('inputName').value.trim().toUpperCase();
  const nisn = document.getElementById('inputNISN').value.trim();
  const err = document.getElementById('loginError');
  
  if (!name || !nisn) { err.textContent = "Nama dan NISN harus diisi!"; err.classList.remove('hidden'); return; }
  
  const schedule = checkExamSchedule();
  if (!schedule.valid) { err.textContent = schedule.message; err.classList.remove('hidden'); return; }
  
  const found = students.find(s => s[0] === name && s[1] === nisn);
  if (!found) { err.textContent = "Nama atau NISN tidak ditemukan!"; err.classList.remove('hidden'); return; }
  
  if (blockedStudents[nisn]) { showBlocked(); return; }
  
  currentStudent = { name: found[0], nisn: found[1] };
  document.getElementById('studentNameDisplay').textContent = currentStudent.name;
  document.getElementById('studentNISNDisplay').textContent = "NISN: " + currentStudent.nisn;
  
  document.getElementById('loginPage').classList.add('hidden');
  document.getElementById('examPage').classList.remove('hidden');
  
  buildNavGrid();
  showQuestion(0);
  startTimer();
  setupAntiCheat();
}

// ===== TIMER =====
function startTimer() {
  timerInterval = setInterval(() => {
    timer--;
    if (timer <= 0) { clearInterval(timerInterval); submitExam(); return; }
    const m = Math.floor(timer / 60);
    const s = timer % 60;
    document.getElementById('timerDisplay').textContent = `${m}:${s.toString().padStart(2,'0')}`;
  }, 1000);
}

// ===== QUESTIONS =====
function showQuestion(idx) {
  currentQ = idx;
  const q = questions[idx];
  document.getElementById('qNumber').textContent = `Soal ${idx+1}/30`;
  document.getElementById('qCategory').textContent = q.cat;
  
  const imgDiv = document.getElementById('qImage');
  if (q.img) {
    imgDiv.innerHTML = `<img src="${q.img}" alt="Soal ${idx+1}" class="max-w-full rounded-lg border" loading="lazy" onerror="this.style.background='#e5e7eb';this.alt='Gambar tidak tersedia';">`;
  } else { imgDiv.innerHTML = ''; }
  
  document.getElementById('qText').textContent = q.text;
  
  const optDiv = document.getElementById('qOptions');
  const labels = ['A','B','C','D','E'];
  optDiv.innerHTML = q.options.map((o, i) => `
    <button onclick="selectAnswer(${i})" class="option-btn w-full text-left px-4 py-3 rounded-lg flex items-center gap-3 ${answers[idx]===i?'selected':''}">
      <span class="w-8 h-8 rounded-full flex items-center justify-center text-sm font-700 ${answers[idx]===i?'bg-blue-600 text-white':'bg-gray-100 text-gray-600'}">${labels[i]}</span>
      <span class="text-gray-700">${o}</span>
    </button>
  `).join('');
  
  updateNavGrid();
}

function selectAnswer(idx) {
  answers[currentQ] = idx;
  showQuestion(currentQ);
  updateAnsweredCount();
}

function prevQ() { if (currentQ > 0) showQuestion(currentQ - 1); }
function nextQ() { if (currentQ < 29) showQuestion(currentQ + 1); }

function buildNavGrid() {
  const grid = document.getElementById('qNavGrid');
  grid.innerHTML = '';
  for (let i = 0; i < 30; i++) {
    const btn = document.createElement('button');
    btn.className = 'w-8 h-8 rounded text-xs font-600 transition';
    btn.textContent = i + 1;
    btn.onclick = () => showQuestion(i);
    grid.appendChild(btn);
  }
  updateNavGrid();
}

function updateNavGrid() {
  const btns = document.getElementById('qNavGrid').children;
  for (let i = 0; i < 30; i++) {
    if (i === currentQ) btns[i].className = 'w-8 h-8 rounded text-xs font-600 bg-blue-600 text-white';
    else if (answers[i] >= 0) btns[i].className = 'w-8 h-8 rounded text-xs font-600 bg-green-600 text-white';
    else btns[i].className = 'w-8 h-8 rounded text-xs font-600 bg-white/20 text-white hover:bg-white/30';
  }
}

function updateAnsweredCount() {
  const count = answers.filter(a => a >= 0).length;
  document.getElementById('answeredCount').textContent = `${count}/30 dijawab`;
}

// ===== SUBMIT =====
function confirmSubmit() {
  const answered = answers.filter(a => a >= 0).length;
  document.getElementById('confirmInfo').textContent = `${answered}/30 soal telah dijawab. ${30-answered} soal belum dijawab.`;
  document.getElementById('submitConfirm').classList.remove('hidden');
}
function cancelSubmit() { document.getElementById('submitConfirm').classList.add('hidden'); }

function submitExam() {
  clearInterval(timerInterval);
  let correct = 0;
  for (let i = 0; i < 30; i++) { if (answers[i] === questions[i].answer) correct++; }
  const wrong = answers.filter((a,i) => a >= 0 && a !== questions[i].answer).length;
  const empty = answers.filter(a => a < 0).length;
  const score = Math.round((correct / 30) * 100);
  
  document.getElementById('resultName').textContent = currentStudent.name;
  document.getElementById('resultScore').textContent = score;
  document.getElementById('resultCorrect').textContent = correct;
  document.getElementById('resultWrong').textContent = wrong;
  document.getElementById('resultEmpty').textContent = empty;
  
  examResults.push({ name: currentStudent.name, nisn: currentStudent.nisn, score, correct, wrong, empty, time: new Date().toLocaleString() });
  localStorage.setItem('cbt_results', JSON.stringify(examResults));
  
  document.getElementById('examPage').classList.add('hidden');
  document.getElementById('resultPage').classList.remove('hidden');
  
  renderLeaderboard();
}

// ===== ANTI-CHEAT =====
function setupAntiCheat() {
  document.addEventListener('visibilitychange', () => {
    if (document.hidden && currentStudent) triggerWarning();
  });
  window.addEventListener('blur', () => { if (currentStudent) triggerWarning(); });
}

function triggerWarning() {
  warnings++;
  const toast = document.getElementById('warningToast');
  
  if (warnings === 1) {
    toast.className = 'toast mb-4 rounded-xl p-4 text-center font-700 bg-red-600 text-white';
    toast.textContent = '⚠️ PERINGATAN 1: Anda terdeteksi meninggalkan halaman ujian! Tetap fokus pada ujian!';
    toast.classList.remove('hidden');
    setTimeout(() => toast.classList.add('hidden'), 5000);
  } else if (warnings === 2) {
    toast.className = 'toast mb-4 rounded-xl p-4 text-center font-700 bg-yellow-500 text-black';
    toast.textContent = '🚨 PERINGATAN 2: INI PERINGATAN TERAKHIR! JIKA ANDA MENINGGALKAN HALAMAN SEKALI LAGI, AKUN ANDA AKAN DIBLOKIR PERMANEN!';
    toast.classList.remove('hidden');
    setTimeout(() => toast.classList.add('hidden'), 8000);
  } else if (warnings >= 3) {
    blockStudent();
  }
}

function blockStudent() {
  clearInterval(timerInterval);
  blockedStudents[currentStudent.nisn] = { name: currentStudent.name, time: new Date().toLocaleString() };
  localStorage.setItem('cbt_blocked', JSON.stringify(blockedStudents));
  showBlocked();
}

function showBlocked() {
  document.getElementById('blockedOverlay').classList.remove('hidden');
  document.getElementById('examPage').classList.add('hidden');
  document.getElementById('loginPage').classList.add('hidden');
  document.getElementById('resultPage').classList.add('hidden');
}

// ===== ADMIN =====
function showAdminLogin() { document.getElementById('adminLoginModal').classList.remove('hidden'); }
function hideAdminLogin() { document.getElementById('adminLoginModal').classList.add('hidden'); document.getElementById('adminError').classList.add('hidden'); }

function doAdminLogin() {
  const pass = document.getElementById('adminPass').value;
  if (pass === ADMIN_PASS) {
    hideAdminLogin();
    document.getElementById('loginPage').classList.add('hidden');
    document.getElementById('adminPage').classList.remove('hidden');
    renderAdmin();
  } else {
    document.getElementById('adminError').textContent = "Password salah!";
    document.getElementById('adminError').classList.remove('hidden');
  }
}

function logoutAdmin() {
  document.getElementById('adminPage').classList.add('hidden');
  document.getElementById('loginPage').classList.remove('hidden');
  document.getElementById('adminPass').value = '';
}

function renderAdmin() {
  const completed = examResults.length;
  const blocked = Object.keys(blockedStudents).length;
  const avgScore = completed > 0 ? Math.round(examResults.reduce((sum, r) => sum + r.score, 0) / completed) : 0;
  
  document.getElementById('statCompleted').textContent = completed;
  document.getElementById('statBlocked').textContent = blocked;
  document.getElementById('statAverage').textContent = avgScore;
  
  // Blocked list
  const bl = document.getElementById('blockedList');
  const keys = Object.keys(blockedStudents);
  if (keys.length === 0) { bl.innerHTML = ''; document.getElementById('noBlocked').classList.remove('hidden'); }
  else {
    document.getElementById('noBlocked').classList.add('hidden');
    bl.innerHTML = keys.map(nisn => `
      <div class="flex items-center justify-between bg-red-500/10 rounded-lg p-3 border border-red-500/20">
        <div><p class="text-white font-600 text-sm">${blockedStudents[nisn].name}</p><p class="text-red-300 text-xs">NISN: ${nisn} | ${blockedStudents[nisn].time}</p></div>
        <button onclick="unblock('${nisn}')" class="bg-green-600 text-white text-xs px-3 py-1 rounded font-600 hover:bg-green-700 transition">✅ Buka</button>
      </div>
    `).join('');
  }
  
  // Results
  const rl = document.getElementById('resultsList');
  if (examResults.length === 0) { rl.innerHTML = ''; document.getElementById('noResults').classList.remove('hidden'); }
  else {
    document.getElementById('noResults').classList.add('hidden');
    const sorted = [...examResults].sort((a,b) => b.score - a.score);
    rl.innerHTML = sorted.map((r, idx) => {
      const status = r.score >= 80 ? '🟢' : r.score >= 60 ? '🟡' : '🔴';
      return `
        <div class="flex items-center justify-between bg-white/5 hover:bg-white/10 rounded-lg p-3 border border-white/10 transition">
          <div><p class="text-white font-600 text-sm">${idx+1}. ${r.name}</p><p class="text-blue-300 text-xs">NISN: ${r.nisn} | ${r.time}</p></div>
          <div class="text-right">
            <p class="text-white font-700 text-lg">${status} ${r.score}</p>
            <p class="text-green-300 text-xs">${r.correct}✓ ${r.wrong}✗ ${r.empty}⭕</p>
          </div>
        </div>
      `;
    }).join('');
  }
  
  // Evaluation
  const excellent = examResults.filter(r => r.score >= 80).length;
  const good = examResults.filter(r => r.score >= 60 && r.score < 80).length;
  const poor = examResults.filter(r => r.score < 60).length;
  
  document.getElementById('evalExcellent').textContent = excellent;
  document.getElementById('evalGood').textContent = good;
  document.getElementById('evalPoor').textContent = poor;
  
  const el = document.getElementById('evalList');
  if (examResults.length === 0) { el.innerHTML = ''; document.getElementById('noEval').classList.remove('hidden'); }
  else {
    document.getElementById('noEval').classList.add('hidden');
    const sorted = [...examResults].sort((a,b) => b.score - a.score);
    el.innerHTML = sorted.map(r => {
      let category = '🔴 Perlu Perbaikan'; let bgColor = 'bg-red-500/10 border-red-500/20';
      if (r.score >= 80) { category = '🟢 Sangat Baik'; bgColor = 'bg-green-500/10 border-green-500/20'; }
      else if (r.score >= 60) { category = '🟡 Baik'; bgColor = 'bg-yellow-500/10 border-yellow-500/20'; }
      return `
        <div class="${bgColor} rounded-lg p-3 border">
          <div class="flex items-center justify-between">
            <div><p class="text-white font-600 text-sm">${r.name}</p><p class="text-blue-300 text-xs">${category}</p></div>
            <p class="text-white font-800 text-lg">${r.score}</p>
          </div>
          <div class="mt-2 text-xs text-blue-200">
            <p>Benar: ${r.correct}/30 | Persentase: ${Math.round((r.correct/30)*100)}%</p>
            <p>Rekomendasi: ${r.score >= 80 ? 'Pertahankan prestasi!' : r.score >= 60 ? 'Tingkatkan pemahaman konsep vektor' : 'Butuh bimbingan intensif'}</p>
          </div>
        </div>
      `;
    }).join('');
  }
}

function switchAdminTab(tab) {
  // Update tab buttons
  ['results', 'blocked', 'evaluation', 'reset'].forEach(t => {
    const btn = document.getElementById('tab' + (t === 'results' ? 'Results' : t === 'blocked' ? 'Blocked' : t === 'evaluation' ? 'Eval' : 'Reset'));
    if (t === tab) {
      btn.classList.remove('text-white/60');
      btn.classList.add('text-white', 'border-b-2', 'border-blue-500');
    } else {
      btn.classList.add('text-white/60');
      btn.classList.remove('text-white', 'border-b-2', 'border-blue-500');
    }
  });
  
  // Update content visibility
  document.getElementById('tabResultsContent').classList.toggle('hidden', tab !== 'results');
  document.getElementById('tabBlockedContent').classList.toggle('hidden', tab !== 'blocked');
  document.getElementById('tabEvalContent').classList.toggle('hidden', tab !== 'evaluation');
  document.getElementById('tabResetContent').classList.toggle('hidden', tab !== 'reset');
}

function filterResults() {
  const search = document.getElementById('searchResults').value.toUpperCase();
  const items = document.getElementById('resultsList').children;
  for (let item of items) {
    const text = item.textContent.toUpperCase();
    item.style.display = text.includes(search) ? '' : 'none';
  }
}

function unblock(nisn) {
  delete blockedStudents[nisn];
  localStorage.setItem('cbt_blocked', JSON.stringify(blockedStudents));
  renderAdmin();
}

// ===== RESET FUNCTIONS =====
let resetType = null;

function confirmReset(type) {
  resetType = type;
  const confirmDiv = document.getElementById('resetConfirm');
  const btn = document.getElementById('resetConfirmBtn');
  
  if (type === 'all') {
    document.getElementById('resetConfirmText').textContent = '⚠️ Yakin ingin reset SEMUA data? Ini tidak bisa dibatalkan!';
    btn.className = 'px-6 py-2 rounded-lg font-600 text-white bg-red-600 hover:bg-red-700 transition';
  } else if (type === 'blocked') {
    document.getElementById('resetConfirmText').textContent = '🟡 Yakin ingin reset siswa terblokir?';
    btn.className = 'px-6 py-2 rounded-lg font-600 text-white bg-yellow-600 hover:bg-yellow-700 transition';
  } else if (type === 'results') {
    document.getElementById('resetConfirmText').textContent = '🟢 Yakin ingin reset hasil ujian?';
    btn.className = 'px-6 py-2 rounded-lg font-600 text-white bg-green-600 hover:bg-green-700 transition';
  }
  
  confirmDiv.classList.remove('hidden');
}

function confirmResetBlocked() {
  confirmReset('blocked');
}

function confirmResetResults() {
  confirmReset('results');
}

function cancelReset() {
  document.getElementById('resetConfirm').classList.add('hidden');
  resetType = null;
}

function doReset() {
  if (resetType === 'all') {
    blockedStudents = {};
    examResults = [];
  } else if (resetType === 'blocked') {
    blockedStudents = {};
  } else if (resetType === 'results') {
    examResults = [];
  }
  
  localStorage.setItem('cbt_blocked', JSON.stringify(blockedStudents));
  localStorage.setItem('cbt_results', JSON.stringify(examResults));
  
  cancelReset();
  renderAdmin();
}

// ===== LEADERBOARD =====
function renderLeaderboard() {
  const sorted = [...examResults].sort((a,b) => b.score - a.score);
  const lb = document.getElementById('leaderboardList');
  lb.innerHTML = sorted.map((r, idx) => {
    const medal = idx === 0 ? '🥇' : idx === 1 ? '🥈' : idx === 2 ? '🥉' : `${idx+1}`;
    const status = r.score >= 80 ? '🟢' : r.score >= 60 ? '🟡' : '🔴';
    return `
      <div class="flex items-center justify-between bg-white/5 hover:bg-white/10 rounded-lg p-4 border border-white/10 transition">
        <div class="flex items-center gap-3">
          <span class="text-2xl">${medal}</span>
          <div>
            <p class="text-white font-600">${r.name}</p>
            <p class="text-blue-300 text-xs">NISN: ${r.nisn}</p>
          </div>
        </div>
        <div class="text-right">
          <p class="text-white font-800 text-xl">${status} ${r.score}</p>
          <p class="text-green-300 text-xs">${r.correct}✓ ${r.wrong}✗ ${r.empty}⭕</p>
        </div>
      </div>
    `;
  }).join('');
}

function backToLogin() {
  document.getElementById('resultPage').classList.add('hidden');
  document.getElementById('loginPage').classList.remove('hidden');
  document.getElementById('blockedOverlay').classList.add('hidden');
  document.getElementById('inputName').value = '';
  document.getElementById('inputNISN').value = '';
  document.getElementById('loginError').classList.add('hidden');
  currentStudent = null;
  answers = new Array(30).fill(-1);
  timer = 90 * 60;
  warnings = 0;
}

// ===== ELEMENT SDK =====
const defaultConfig = {
  exam_title: "Ujian CBT ASAS FISIKA",
  background_color: "#0f172a",
  surface_color: "#1e3a5f",
  text_color: "#ffffff",
  primary_action_color: "#2563eb",
  secondary_action_color: "#16a34a",
  font_family: "Plus Jakarta Sans",
  font_size: 16
};

window.elementSdk.init({
  defaultConfig,
  onConfigChange: async (config) => {
    const title = config.exam_title || defaultConfig.exam_title;
    document.getElementById('examTitle').textContent = title;
    
    const font = config.font_family || defaultConfig.font_family;
    document.body.style.fontFamily = `${font}, sans-serif`;
    
    const size = config.font_size || defaultConfig.font_size;
    document.body.style.fontSize = size + 'px';
  },
  mapToCapabilities: (config) => ({
    recolorables: [
      { get: () => config.background_color || defaultConfig.background_color, set: (v) => { config.background_color = v; window.elementSdk.setConfig({ background_color: v }); }},
      { get: () => config.surface_color || defaultConfig.surface_color, set: (v) => { config.surface_color = v; window.elementSdk.setConfig({ surface_color: v }); }},
      { get: () => config.text_color || defaultConfig.text_color, set: (v) => { config.text_color = v; window.elementSdk.setConfig({ text_color: v }); }},
      { get: () => config.primary_action_color || defaultConfig.primary_action_color, set: (v) => { config.primary_action_color = v; window.elementSdk.setConfig({ primary_action_color: v }); }},
      { get: () => config.secondary_action_color || defaultConfig.secondary_action_color, set: (v) => { config.secondary_action_color = v; window.elementSdk.setConfig({ secondary_action_color: v }); }},
    ],
    borderables: [],
    fontEditable: { get: () => config.font_family || defaultConfig.font_family, set: (v) => { config.font_family = v; window.elementSdk.setConfig({ font_family: v }); }},
    fontSizeable: { get: () => config.font_size || defaultConfig.font_size, set: (v) => { config.font_size = v; window.elementSdk.setConfig({ font_size: v }); }}
  }),
  mapToEditPanelValues: (config) => new Map([
    ["exam_title", config.exam_title || defaultConfig.exam_title]
  ])
});

lucide.createIcons();
   </script>
  </div>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'a09be1f9dc74fdfe',t:'MTc4MTEzMTI3OA=='};var a=document.createElement('script');a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
