# Pembina Dashboard

Pembina dashboard profesional **satu fail** (single-file) — bina, sunting, dan kongsi dashboard interaktif terus dalam pelayar, **tanpa pelayan, tanpa pemasangan, 100% client-side**.

Seret-dan-lepas widget, sambung data langsung, tukar tema, dan eksport — semuanya dalam satu fail HTML.

| Fail | Keterangan |
|---|---|
| **`Professional_Dashboard.html`** | Fail utama untuk digunakan — buka terus dalam pelayar |
| `pembina-dashboard_V2.html` | Fail kerja/pembangunan (kandungan identik) |

---

## 🚀 Mula pantas

1. **Buka** `Professional_Dashboard.html` dalam pelayar moden (Chrome / Edge / Firefox / Safari).
2. Dari panel kiri, **tambah widget** atau **mula dari templat**.
3. **Seret** tajuk widget untuk gerak, **seret sudut** untuk ubah saiz.
4. **Klik** widget → sunting sifatnya di panel kanan.
5. Kerja anda **disimpan automatik** dalam pelayar.

> 💡 Untuk fungsi penuh (terutama **Simpan ke fail** & **data langsung**), buka melalui `https://` atau `localhost`. Membuka terus (`file://`) tetap berfungsi untuk kebanyakan ciri.

---

## 🧩 Widget

| Widget | Kegunaan |
|---|---|
| **Kad KPI** | Nombor utama + **sparkline** (mini-trend) + warna bersyarat ikut ambang |
| **Bar Kemajuan** | Kemajuan vs sasaran (bullet) dengan penanda sasaran & peratus |
| **Carta garis / kawasan / bar** | Trend & perbandingan (berbilang siri, bertindan, lengkung) |
| **Carta donut** | Bahagian keseluruhan + jumlah di tengah |
| **Tolok (gauge)** | Nilai vs sasaran |
| **Jadual** | Data tersusun + skala warna sel angka (heatmap) |
| **Teks / Tajuk** | Tajuk seksyen atau nota |
| **Imej / Logo** | Gambar atau ikon |
| **Peta Web** | Peta interaktif (Leaflet) — lihat di bawah |

### 🗺️ Ciri Peta Web
- **Mod penanda**: Buih (saiz ikut nilai) · Penanda · **Peta haba (heatmap)**
- **5 gaya peta**: Cahaya · Jalan · Voyager · Satelit · Gelap
- **Warna ikut nilai** (gradient + legenda)
- **Garis sambungan** (turutan / hab)
- **Kesan denyut (pulse)**, label nilai, popup
- **Import CSV** (label, lat, lng, nilai)

---

## ⚙️ Fungsi utama

### Penyuntingan
- **Seret & lepas** + ubah saiz pada grid 12-lajur
- **Jajaran tajuk** widget: kiri / tengah / kanan
- **Saiz paparan fleksibel** — teks/nombor berskala mengikut saiz widget (container queries)
- **Kunci widget** — elak gerak/ubah/padam tak sengaja
- **Undo / Redo** (`Ctrl+Z` / `Ctrl+Y`)
- **Mod**: Sunting ↔ Pratonton

### Data
- **Sambungan data langsung** — tarik dari **URL CSV atau JSON** + **auto-segar** berkala
- **Import CSV** ke jadual & peta
- **Pemformatan nombor** — ringkaskan nombor besar (`1,200,000 → 1.2J`)
- **Pemformatan bersyarat** — warna KPI ikut ambang, heatmap sel jadual

### Tema & paparan
- **Mod gelap / terang**
- **8 warna aksen** tema
- **7 templat** siap: Ringkasan Jualan · Papan Operasi · Kewangan Peribadi · Sumber Manusia · Pemasaran · Pengurusan Projek · E-Dagang

### Fail & eksport
- **Cipta** dashboard baharu
- **Simpan ke fail** `.json` (dialog "Simpan sebagai" jika disokong)
- **Muat naik** dashboard `.json` dari PC
- **Eksport PDF** (satu halaman) & **PNG**
- **Auto-simpan** ke `localStorage` (pulih ke keadaan terakhir)

---

## 🌐 Sambungan data langsung

Untuk widget data (jadual, carta, donut, peta): panel kanan → **Sumber data langsung** → masukkan URL, pilih format, dan tetapkan selang auto-segar.

**Pemetaan data:**

| Widget | Susunan |
|---|---|
| Jadual | Baris 1 = tajuk lajur, seterusnya = data |
| Carta | Lajur 1 = label, lajur lain = siri |
| Donut | label, nilai |
| Peta | label, lat, lng, nilai |

**Contoh termudah:** Google Sheets → *File → Share → Publish to web → CSV* → tampal URL.

> ⚠️ **CORS**: pelayar hanya benarkan ambil data dari URL yang menghantar pengepala CORS (cth Google Sheets terbit, GitHub raw, banyak API awam). URL tanpa CORS akan gagal — ini had keselamatan pelayar.

---

## ⌨️ Pintasan papan kekunci

| Kekunci | Tindakan |
|---|---|
| `Ctrl/⌘ + Z` | Buat asal (undo) |
| `Ctrl/⌘ + Y` / `Ctrl+Shift+Z` | Buat semula (redo) |
| `Delete` | Padam widget dipilih (kecuali terkunci) |
| `Esc` | Nyahpilih / tutup menu |

---

## 🛠️ Teknologi

- **Satu fail HTML** — tiada *build step*, tiada *dependency* tempatan
- Pustaka (dimuat dari CDN, perlukan internet):
  - [Chart.js](https://www.chartjs.org/) — carta
  - [Leaflet](https://leafletjs.com/) + leaflet.heat — peta & peta haba
  - [html2canvas](https://html2canvas.hertzen.com/) — eksport imej/PDF
- **Storan**: `localStorage` pelayar (auto-simpan) + eksport/import fail `.json`

### Keperluan pelayar
Pelayar moden (2022+): **Chrome 105+, Edge 105+, Firefox 110+, Safari 16+** — diperlukan untuk *CSS container queries* (saiz widget fleksibel).

---

## 💾 Simpanan & privasi

- Semua data kekal **dalam pelayar anda** (`localStorage`) — tiada data dihantar ke mana-mana pelayan.
- Untuk simpan kekal / kongsi / pindah, guna **Simpan ke fail** (`.json`) dan **Muat naik** di komputer lain.

---

## 📋 Struktur data (fail `.json`)

```json
{
  "app": "pembina-dashboard",
  "version": 1,
  "name": "Nama Dashboard",
  "accent": "#4355E0",
  "widgets": [
    { "type": "kpi", "x": 0, "y": 1, "w": 3, "h": 3, "title": "...", "config": { } }
  ]
}
```

---

*Dibina sebagai alat dashboard ringan, mudah alih, dan tanpa pelayan.*
