<!DOCTYPE html>
<html lang="id">

<head>
  <meta charset="UTF-8" />
  <meta name="description" content="Aplikasi Device Hmsi">
  <meta name="keywords" content="sdedyatm,atm,hmsi,hino">
  <meta name="author" content="sdedyatm">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <link href="https://fonts.googleapis.com/css2?family=Fira+Code&display=swap" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
  <title>Form Pengeluaran Driver</title>
  <style>
    body,
    html {
      margin: 0;
      padding: 1%;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: #e0f7fa;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .container {
      background: #ffffff;
      padding: 30px 40px;
      width: 100%;
      max-width: 480px;
      border-radius: 15px;
      box-shadow: 0 15px 40px rgba(0, 0, 0, 0.15);
      text-align: center;
      height: 150%;
    }

    h2 {
      color: #00796b;
      margin-bottom: 24px;
      font-weight: 700;
    }

    label {
      display: block;
      text-align: left;
      font-weight: 600;
      margin: 12px 0 6px 0;
      color: #004d40;
    }

    input[type=text],
    select,
    textarea {
      width: 100%;
      padding: 12px 14px;
      border: 1.8px solid #b2dfdb;
      border-radius: 8px;
      font-size: 16px;
      font-family: inherit;
      transition: border-color 0.3s ease;
    }

    input[type=text]:focus,
    select:focus,
    textarea:focus {
      border-color: #00796b;
      outline: none;
      box-shadow: 0 0 10px rgba(0, 121, 107, 0.3);
    }

    textarea {
      min-height: 90px;
      resize: vertical;
    }

    input[readonly] {
      background-color: #f0f4f4;
      cursor: not-allowed;
    }

    #sisaOutput {
      margin-top: 14px;
      font-weight: 700;
      color: #2e7d32;
      text-align: left;
    }

    button[type=submit] {
      margin-top: 28px;
      background-color: #00796b;
      border: none;
      padding: 14px;
      border-radius: 10px;
      width: 100%;
      color: white;
      font-weight: 700;
      font-size: 17px;
      cursor: pointer;
      user-select: none;
      transition: background-color 0.3s ease;
    }

    button[type=submit]:hover {
      background-color: #004d40;
    }

    #ringkasanContainer {
      white-space: pre-wrap;
      background-color: transparent;
      /* transparan untuk hasil PNG */
      color: #222;
      padding: 24px;
      border: none;
      /* agar clean di PNG */
      border-radius: 12px;
      max-width: 600px;
      font-family: 'Fira Code', monospace;
      font-size: 16px;
      text-align: left;
      line-height: 1.5;
    }

    #downloadBtn {
      background-color: #00796b;
      color: white;
      border: none;
      padding: 10px 18px;
      border-radius: 8px;
      cursor: pointer;
      font-weight: 700;
      transition: background-color 0.3s ease;
      user-select: none;
    }

    #downloadBtn:hover {
      background-color: #004d40;
    }

    @media (max-width: 520px) {
      .container {
        padding: 25px 20px;
      }

      #outputWrapper {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        min-height: 100vh;
        /* agar selalu di tengah halaman */
        text-align: center;
        padding: 40px;
      }
    }
  </style>
</head>

<body>
  <main class="container" role="main" aria-label="Form Pengeluaran Driver">
    <center>
      <img src="https://lh3.googleusercontent.com/pw/ABLVV86l4why0k2zAcWgQtpuAPbx1mQtyWLpFAG8LMyYBxIgDdM1T7WWH-Ewwyh55l-KUl1_5kjWXt9oGPw4tcArZ-dIHZJhLOaTrHG2HtOiq6y0zgqVeJU_2bLJAn8TuW4WwbHmgEYv2jm3fpGwemFe7FPxDQ=w607-h607-s-no-gm?authuser=0" width="190">
    </center>
    <h2>Rincian UJ Chasis</h2>
    <form id="formPengeluaran" autocomplete="off" novalidate>
      <label for="namaDriver">Nama Driver</label>
      <input type="text" id="namaDriver" name="namaDriver" placeholder="Ketik Nama Driver" required />

      <label for="typeUnit">Type Unit</label>
      <select id="typeUnit" name="typeUnit" required>
        <option value="" disabled selected>-- Pilih Type Unit --</option>
        <option value="DUTRO 4 RODA">DUTRO 4 RODA</option>
        <option value="DUTRO 6 RODA">DUTRO 6 RODA</option>
        <option value="FG JP/JL/JK">FG JP/JL/JK</option>
        <option value="FG / SG TH">FG / SG TH</option>
        <option value="FL JW">FL JW</option>
        <option value="FM JD">FM JD</option>
        <option value="FL JT / JN">FL JT / JN</option>
        <option value="FM JW">FM JW</option>
        <option value="FM 340 TH">FM 340 TH</option>
        <option value="DUTRO ENGINE">DUTRO ENGINE</option>
        <option value="RM / RK">RM / RK</option>
      </select>

      <label for="tujuan">Tujuan</label>
      <select id="tujuan" name="tujuan" required>
        <option value="" disabled selected>-- Pilih Tujuan --</option>
        <option value="Lampung">Lampung</option>
        <option value="Palembang">Palembang</option>
        <option value="Bengkulu">Bengkulu</option>
        <option value="Jambi">Jambi</option>
        <option value="Pekanbaru">Pekanbaru</option>
        <option value="Padang">Padang</option>
        <option value="Sidempuan">Sidempuan</option>
        <option value="Labuhan Batu">Labuhan Batu</option>
        <option value="Siantar">Siantar</option>
        <option value="Medan">Medan</option>
        <option value="Lhokseumawe">Lhokseumawe</option>
        <option value="Aceh">Aceh</option>
        <option value="Meulaboh">Meulaboh</option>
        <option value="Surabaya">Surabaya</option>
        <option value="Semarang">Semarang</option>
        <option value="Magelang">Magelang</option>
        <option value="Yogyakarta">Yogyakarta</option>
        <option value="Solo">Solo</option>
        <option value="Gresik">Gresik</option>
        <option value="Madiun">Madiun</option>
        <option value="Kediri">Kediri</option>
        <option value="Mojokerto">Mojokerto</option>
        <option value="Malang">Malang</option>
        <option value="Pasuruan">Pasuruan</option>
        <option value="Jember">Jember</option>
        <option value="Banyuwangi">Banyuwangi</option>
      </select>

      <label for="uangJalanDisplay">Uang Jalan (Rp)</label>
      <input type="text" id="uangJalanDisplay" readonly aria-readonly="true" value="Rp 0" />

      <label for="pengeluaranDisplay">Pengeluaran (Rp)</label>
      <input type="text" id="pengeluaranDisplay" placeholder="Masukkan pengeluaran" required />

      <div id="sisaOutput" aria-live="polite">Sisa Uang Jalan: Rp 0</div>

      <label for="rincian">Rincian Pengeluaran</label>
      <textarea id="rincian" name="rincian" placeholder="Pengeluaran unit :&#10;E-Tol :&#10;Pulsa / Kuota :&#10;Transfer :&#10;UJ Sementara :" required></textarea>

      <button type="submit">Cetak Rincian uj</button>
    </form>

    <section id="ringkasanSection" tabindex="0" aria-label="Ringkasan Pengeluaran"></section>

    <div id="outputWrapper">
      <div id="popupAlert" style="display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.5); z-index:9999; justify-content:center; align-items:center;">
        <div style="background:white; padding:20px; border-radius:10px; max-width:90%; text-align:center;">
          <p style="font-size:18px; font-weight:bold; color:red;">SILAHKAN UBAH TYPE UNIT / TUJUAN</p>
          <p style="font-size:14px;">Tidak ada pengiriman ke Sumatera untuk type ENGINE..!!</p>
          <button onclick="closePopup()" style="margin-top:10px; padding:8px 16px; background:#d33; color:#fff; border:none; border-radius:8px; cursor:pointer;">Tutup</button>
        </div>
      </div>

      <pre id="ringkasanContainer"></pre> <!-- Ini yang diisi teks ringkasan -->
      <button id="downloadBtn">Download & Kirim</button>
      <button id="downloadImgBtn" style="display: none;">Download PNG</button>
    </div>

  </main>

  <script>
    // Tarif uang jalan sesuai type unit dan tujuan
    const tarifUangJalan = {
      "DUTRO 4 RODA": {
        "Lampung": 1640000,
        "Palembang": 2440000,
        "Bengkulu": 2660000,
        "Jambi": 2610000,
        "Pekanbaru": 3110000,
        "Padang": 3160000,
        "Sidempuan": 4340000,
        "Labuhan Batu": 409000,
        "Siantar": 4240000,
        "Medan": 4390000,
        "Lhokseumawe": 5290000,
        "Aceh": 5740000,
        "Meulaboh": 6040000,
        "Surabaya": 1500000,
        "Semarang": 950000,
        "Magelang": 1050000,
        "Yogyakarta": 1150000,
        "Solo": 1200000,
        "Gresik": 1450000,
        "Madiun": 1350000,
        "Kediri": 1500000,
        "Mojokerto": 1450000,
        "Malang": 1650000,
        "Pasuruan": 1650000,
        "Jember": 1950000,
        "Banyuwangi": 2150000
      },
      "DUTRO 6 RODA": {
        "Lampung": 1740000,
        "Palembang": 2540000,
        "Bengkulu": 2840000,
        "Jambi": 2760000,
        "Pekanbaru": 3260000,
        "Padang": 3310000,
        "Sidempuan": 4540000,
        "Labuhan Batu": 4240000,
        "Siantar": 4390000,
        "Medan": 4540000,
        "Lhokseumawe": 5490000,
        "Aceh": 5940000,
        "Meulaboh": 6240000,
        "Surabaya": 1600000,
        "Semarang": 1000000,
        "Magelang": 1100000,
        "Yogyakarta": 1200000,
        "Solo": 1250000,
        "Gresik": 1550000,
        "Madiun": 1450000,
        "Kediri": 1500000,
        "Mojokerto": 1550000,
        "Malang": 1750000,
        "Pasuruan": 1750000,
        "Jember": 2050000,
        "Banyuwangi": 2250000
      },
      "FG JP/JL/JK": {
        "Lampung": 2515000,
        "Palembang": 3365000,
        "Bengkulu": 3585000,
        "Jambi": 3485000,
        "Pekanbaru": 4385000,
        "Padang": 4585000,
        "Sidempuan": 5885000,
        "Labuhan Batu": 5385000,
        "Siantar": 5635000,
        "Medan": 5885000,
        "Lhokseumawe": 6735000,
        "Aceh": 7335000,
        "Meulaboh": 7635000,
        "Surabaya": 2100000,
        "Semarang": 950000,
        "Magelang": 1350000,
        "Yogyakarta": 1450000,
        "Gresik": 2100000,
        "Madiun": 1900000,
        "Kediri": 2000000,
        "Mojokerto": 2100000,
        "Malang": 2300000,
        "Pasuruan": 2300000,
        "Jember": 2550000,
        "Banyuwangi": 2700000
      },
      "FG / SG TH": {
        "Lampung": 2515000,
        "Palembang": 3365000,
        "Bengkulu": 3585000,
        "Jambi": 3485000,
        "Pekanbaru": 4385000,
        "Padang": 4585000,
        "Sidempuan": 5885000,
        "Labuhan Batu": 5385000,
        "Siantar": 5635000,
        "Medan": 5885000,
        "Lhokseumawe": 6735000,
        "Aceh": 7335000,
        "Meulaboh": 7635000,
        "Surabaya": 2100000,
        "Semarang": 950000,
        "Magelang": 1350000,
        "Yogyakarta": 1450000,
        "Solo": 1500000,
        "Gresik": 2100000,
        "Madiun": 1900000,
        "Kediri": 2000000,
        "Mojokerto": 2100000,
        "Malang": 2300000,
        "Pasuruan": 2300000,
        "Jember": 2550000,
        "Banyuwangi": 2700000
      },
      "FL JW": {
        "Lampung": 3330000,
        "Palembang": 3930000,
        "Bengkulu": 4100000,
        "Jambi": 5200000,
        "Pekanbaru": 5500000,
        "Padang": 5500000,
        "Sidempuan": 7500000,
        "Labuhan Batu": 6700000,
        "Siantar": 7300000,
        "Medan": 7500000,
        "Lhokseumawe": 8500000,
        "Aceh": 9100000,
        "Meulaboh": 9400000,
        "Surabaya": 2300000,
        "Semarang": 1500000,
        "Magelang": 1550000,
        "Yogyakarta": 1650000,
        "Solo": 1700000,
        "Gresik": 2300000,
        "Madiun": 2100000,
        "Kediri": 2200000,
        "Mojokerto": 2300000,
        "Malang": 2500000,
        "Pasuruan": 2500000,
        "Jember": 2750000,
        "Banyuwangi": 2900000
      },
      "FM JD": {
        "Lampung": 3165000,
        "Palembang": 3715000,
        "Bengkulu": 4035000,
        "Jambi": 4185000,
        "Pekanbaru": 5185000,
        "Padang": 5285000,
        "Sidempuan": 7185000,
        "Labuhan Batu": 6635000,
        "Siantar": 7035000,
        "Medan": 7235000,
        "Lhokseumawe": 8585000,
        "Aceh": 9135000,
        "Meulaboh": 9435000,
        "Surabaya": 2300000,
        "Semarang": 1500000,
        "Magelang": 1550000,
        "Yogyakarta": 1650000,
        "Solo": 1700000,
        "Gresik": 2300000,
        "Madiun": 2100000,
        "Kediri": 2200000,
        "Mojokerto": 2300000,
        "Malang": 2500000,
        "Pasuruan": 2500000,
        "Jember": 2750000,
        "Banyuwangi": 2900000
      },
      "FL JT / JN": {
        "Lampung": 3115000,
        "Palembang": 3665000,
        "Bengkulu": 3935000,
        "Jambi": 4035000,
        "Pekanbaru": 5035000,
        "Padang": 5135000,
        "Sidempuan": 6935000,
        "Labuhan Batu": 6335000,
        "Siantar": 6735000,
        "Medan": 6935000,
        "Lhokseumawe": 8235000,
        "Aceh": 8835000,
        "Meulaboh": 9135000,
        "Surabaya": 2300000,
        "Semarang": 1500000,
        "Magelang": 1550000,
        "Yogyakarta": 1650000,
        "Solo": 1700000,
        "Gresik": 2300000,
        "Madiun": 2100000,
        "Kediri": 2200000,
        "Mojokerto": 2300000,
        "Malang": 2500000,
        "Pasuruan": 2500000,
        "Jember": 2750000,
        "Banyuwangi": 2900000
      },
      "FM JW": {
        "Lampung": 3480000,
        "Palembang": 4030000,
        "Bengkulu": 4300000,
        "Jambi": 5450000,
        "Pekanbaru": 5450000,
        "Padang": 5550000,
        "Sidempuan": 7950000,
        "Labuhan Batu": 7100000,
        "Siantar": 7800000,
        "Medan": 8000000,
        "Lhokseumawe": 9050000,
        "Aceh": 9600000,
        "Meulaboh": 9900000,
        "Surabaya": 2300000,
        "Semarang": 1500000,
        "Magelang": 1550000,
        "Yogyakarta": 1650000,
        "Solo": 1700000,
        "Gresik": 2300000,
        "Madiun": 2100000,
        "Kediri": 2200000,
        "Mojokerto": 2300000,
        "Malang": 2500000,
        "Pasuruan": 2500000,
        "Jember": 2750000,
        "Banyuwangi": 2900000
      },
      "FM 340 TH": {
        "Lampung": 3465000,
        "Palembang": 4015000,
        "Bengkulu": 4105000,
        "Jambi": 4565000,
        "Pekanbaru": 5435000,
        "Padang": 5535000,
        "Sidempuan": 7635000,
        "Labuhan Batu": 7085000,
        "Siantar": 7485000,
        "Medan": 7685000,
        "Lhokseumawe": 9035000,
        "Aceh": 9585000,
        "Meulaboh": 9885000,
        "Surabaya": 2300000,
        "Semarang": 1500000,
        "Magelang": 1550000,
        "Yogyakarta": 1650000,
        "Solo": 1700000,
        "Gresik": 2300000,
        "Madiun": 2100000,
        "Kediri": 2200000,
        "Mojokerto": 2300000,
        "Malang": 2500000,
        "Pasuruan": 2500000,
        "Jember": 2750000,
        "Banyuwangi": 2900000
      },
      "DUTRO ENGINE": {
        "Semarang": 1100000,
        "Magelang": 1150000,
        "Yogyakarta": 1250000,
        "Solo": 1300000,
        "Surabaya": 1900000,
        "Gresik": 1900000,
        "Madiun": 1700000,
        "Kediri": 1800000,
        "Mojokerto": 1900000,
        "Malang": 2100000,
        "Pasuruan": 2100000,
        "Jember": 2350000,
        "Banyuwangi": 2500000,
        "Lampung": 0,
        "Palembang": 0,
        "Bengkulu": 0,
        "Jambi": 0,
        "Pekanbaru": 0,
        "Padang": 0,
        "Sidempuan": 0,
        "Labuhan Batu": 0,
        "Siantar": 0,
        "Medan": 0,
        "Lhokseumawe": 0,
        "Aceh": 0,
        "Meulaboh": 0
      },
      "RM / RK": {
        "Semarang": 1700000,
        "Magelang": 1750000,
        "Yogyakarta": 1850000,
        "Solo": 1900000,
        "Surabaya": 2600000,
        "Gresik": 2600000,
        "Madiun": 2400000,
        "Kediri": 2500000,
        "Mojokerto": 2600000,
        "Malang": 2800000,
        "Pasuruan": 2800000,
        "Jember": 3050000,
        "Banyuwangi": 3200000,
        "Lampung": 0,
        "Palembang": 0,
        "Bengkulu": 0,
        "Jambi": 0,
        "Pekanbaru": 0,
        "Padang": 0,
        "Sidempuan": 0,
        "Labuhan Batu": 0,
        "Siantar": 0,
        "Medan": 0,
        "Lhokseumawe": 0,
        "Aceh": 0,
        "Meulaboh": 0
      }
    };
    // Format rupiah (Rp 12.345.678)
    function formatRupiah(angka) {
      if (!angka) return 'Rp 0';
      let number_string = angka.toString().replace(/[^,\d]/g, '');
      let split = number_string.split(',');
      let sisa = split[0].length % 3;
      let rupiah = split[0].substr(0, sisa);
      let ribuan = split[0].substr(sisa).match(/\d{3}/gi);
      if (ribuan) {
        let separator = sisa ? '.' : '';
        rupiah += separator + ribuan.join('.');
      }
      rupiah = split[1] !== undefined ? rupiah + ',' + split[1] : rupiah;
      return 'Rp ' + rupiah;
    }
    // Parsing dari string rupiah ke number
    function parseRupiah(str) {
      if (!str) return 0;
      return parseInt(str.replace(/[^0-9]/g, '')) || 0;
    }
    // Update uang jalan otomatis sesuai type unit dan tujuan
    function updateUangJalan() {
      const typeUnit = document.getElementById('typeUnit').value;
      const tujuan = document.getElementById('tujuan').value;
      const uangJalanDisplay = document.getElementById('uangJalanDisplay');
      if (typeUnit && tujuan && tarifUangJalan[typeUnit] && tarifUangJalan[typeUnit][tujuan] !== undefined) {
        uangJalanDisplay.value = formatRupiah(tarifUangJalan[typeUnit][tujuan]);
      } else {
        uangJalanDisplay.value = 'Rp 0';
      }
      updateSisa();
    }
    // Update sisa uang jalan realtime
    function updateSisa() {
      const uangJalan = parseRupiah(document.getElementById('uangJalanDisplay').value);
      const pengeluaran = parseRupiah(document.getElementById('pengeluaranDisplay').value);
      const sisaOutput = document.getElementById('sisaOutput');
      let sisa = uangJalan - pengeluaran;
      if (sisa < 0) {
        sisaOutput.style.color = '#c62828'; // merah kalau minus
        sisaOutput.textContent = `Sisa Uang Jalan: -${formatRupiah(Math.abs(sisa))} (Chek Kembali..!!)`;
      } else {
        sisaOutput.style.color = '#2e7d32'; // hijau kalau positif
        sisaOutput.textContent = `Sisa Uang Jalan: ${formatRupiah(sisa)}`;
      }
    }
    // Format input pengeluaran jadi rupiah saat mengetik
    function onPengeluaranInput(e) {
      let cursorPosition = e.target.selectionStart;
      let originalLength = e.target.value.length;
      let angka = parseRupiah(e.target.value);
      e.target.value = formatRupiah(angka);
      let newLength = e.target.value.length;
      cursorPosition = cursorPosition + (newLength - originalLength);
      e.target.setSelectionRange(cursorPosition, cursorPosition);
      updateSisa();
    }
    // Generate ringkasan teks pengeluaran
    function generateRingkasan(data) {
      return `=== RINCIAN UANG JALAN ===
Tanggal    : ${data.tanggal}
Nama Driver: ${data.namaDriver}
Type Unit  : ${data.typeUnit}
Tujuan     : ${data.tujuan}
Uang Jalan : ${formatRupiah(data.uangJalan)}
Pengeluaran: ${formatRupiah(data.pengeluaran)}
Sisa Uang  : ${formatRupiah(data.sisa)}
Rincian    : 
${data.rincian}
─═✧✧═─ 𝕓𝕪: 𝕤𝕕𝕖𝕕𝕪𝕒𝕥𝕞 ─═✧✧═─
Hati-hati di jalan anak istri
menanti di rumah dengan setia.
`;
    }
    // Event handler form submit
    document.getElementById('formPengeluaran').addEventListener('submit', function(e) {
      e.preventDefault();
      const namaDriver = this.namaDriver.value.trim();
      const typeUnit = this.typeUnit.value;
      const tujuan = this.tujuan.value;
      const uangJalan = parseRupiah(document.getElementById('uangJalanDisplay').value);
      const pengeluaran = parseRupiah(this.pengeluaranDisplay.value);
      const rincian = this.rincian.value.trim();
      if (!namaDriver || !typeUnit || !tujuan || !rincian) {
        alert('Semua kolom harus diisi..');
        return;
      }
      if (pengeluaran > uangJalan) {
        if (!confirm('Pengeluaran melebihi uang jalan, lanjutkan?')) {
          return;
        }
      }
      const sisa = uangJalan - pengeluaran;
      const tanggal = new Date().toLocaleString('id-ID', {
        year: 'numeric',
        month: '2-digit',
        day: '2-digit',
        hour: '2-digit',
        minute: '2-digit',
        second: '2-digit'
      });
      const data = {
        tanggal,
        namaDriver,
        typeUnit,
        tujuan,
        uangJalan,
        pengeluaran,
        sisa,
        rincian
      };
      const ringkasanText = generateRingkasan(data);
      const ringkasanContainer = document.getElementById('ringkasanContainer');
      ringkasanContainer.textContent = ringkasanText;
      // Setup event download
      downloadBtn.onclick = () => {
        const canvas = document.createElement('canvas');
        const ctx = canvas.getContext('2d');
        const lines = ringkasanText.split('\n');
        const fontSize = 16;
        const lineHeight = fontSize * 1.5;
        const padding = 20;
        const width = 340;
        const height = padding * 2 + lines.length * lineHeight;
        canvas.width = width;
        canvas.height = height;
        const bgImage = new Image();
        bgImage.crossOrigin = 'anonymous';
        bgImage.src = 'https://i.postimg.cc/kgM9QGvG/sdedyatm.png';
        bgImage.onload = () => {
          // Gambar background disesuaikan agar pas tengah
          const imgAspect = bgImage.width / bgImage.height;
          const canvasAspect = canvas.width / canvas.height;
          let drawWidth, drawHeight, drawX, drawY;
          if (imgAspect > canvasAspect) {
            drawHeight = canvas.height;
            drawWidth = bgImage.width * (canvas.height / bgImage.height);
            drawX = (canvas.width - drawWidth) / 2;
            drawY = 0;
          } else {
            drawWidth = canvas.width;
            drawHeight = bgImage.height * (canvas.width / bgImage.width);
            drawX = 0;
            drawY = (canvas.height - drawHeight) / 2;
          }
          ctx.drawImage(bgImage, drawX, drawY, drawWidth, drawHeight);
          // Tambahkan overlay semi-transparan agar teks terbaca
          ctx.fillStyle = 'rgba(255, 255, 255, 0.85)';
          ctx.fillRect(0, 0, canvas.width, canvas.height);
          // Gambar teks
          ctx.font = `${fontSize}px monospace`;
          ctx.fillStyle = 'black';
          lines.forEach((line, index) => {
            ctx.fillText(line, padding, padding + (index + 1) * lineHeight);
          });
          // Simpan hasil sebagai gambar
          canvas.toBlob((blob) => {
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `UJ_Driver_${namaDriver}_${new Date().toISOString().slice(0,10)}.png`;
            document.body.appendChild(a);
            a.click();
            a.remove();
            URL.revokeObjectURL(url);
          }, 'image/png');
        };
        bgImage.onerror = () => {
          alert('Gagal memuat gambar latar belakang.');
        };
      };
    });
    // Update uang jalan saat pilih type unit atau tujuan berubah
    document.getElementById('typeUnit').addEventListener('change', updateUangJalan);
    document.getElementById('tujuan').addEventListener('change', updateUangJalan);
    // Format input pengeluaran saat mengetik
    document.getElementById('pengeluaranDisplay').addEventListener('input', onPengeluaranInput);
    // Inisialisasi
    updateUangJalan();
  </script>
  <script>
    const sumateraDestinations = [
      "Lampung", "Palembang", "Bengkulu", "Jambi", "Pekanbaru", "Padang",
      "Sidempuan", "Labuhan Batu", "Siantar", "Medan", "Lhokseumawe", "Aceh", "Meulaboh"
    ];
    const typeUnitSelect = document.getElementById("typeUnit");
    const tujuanSelect = document.getElementById("tujuan");

    function checkUnitAndDestination() {
      const selectedType = typeUnitSelect.value;
      const selectedTujuan = tujuanSelect.value;
      const isEngineType = selectedType === "DUTRO ENGINE" || selectedType === "RM / RK";
      const isSumatera = sumateraDestinations.includes(selectedTujuan);
      if (isEngineType && isSumatera) {
        showPopup();
      }
    }

    function showPopup() {
      document.getElementById("popupAlert").style.display = "flex";
    }

    function closePopup() {
      document.getElementById("popupAlert").style.display = "none";
    }
    // Cek ketika user mengubah salah satu field
    typeUnitSelect.addEventListener("change", checkUnitAndDestination);
    tujuanSelect.addEventListener("change", checkUnitAndDestination);
  </script>
  <script>
    const CACHE_NAME = 'pwa-gas-v1';
    const urlsToCache = [
      '/',
      'manifest.json'
    ];
    self.addEventListener('install', function(event) {
      event.waitUntil(
        caches.open(CACHE_NAME).then(cache => cache.addAll(urlsToCache))
      );
    });
    self.addEventListener('fetch', function(event) {
      event.respondWith(
        caches.match(event.request).then(response => response || fetch(event.request))
      );
    });
  </script>
  <script>
    const CACHE_NAME = 'pwa-gas-v1';
    const urlsToCache = [
      '/',
      'manifest.json'
    ];
    self.addEventListener('install', function(event) {
      event.waitUntil(
        caches.open(CACHE_NAME).then(cache => cache.addAll(urlsToCache))
      );
    });
    self.addEventListener('fetch', function(event) {
      event.respondWith(
        caches.match(event.request).then(response => response || fetch(event.request))
      );
    });
  </script>

</body>

</html>
