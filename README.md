# Studio Bata

Editor 3D bata LEGO-compatible di browser: 108 part dari koleksi STL, 15 aksesori, dan 3 template adegan (Ruang kantor, Bengkel mobil, Studio band). Model bisa diekspor sebagai STL atau PNG.

Situs statis murni, tanpa server dan tanpa build. Pustaka three.js dimuat dari CDN jsDelivr, jadi pengunjung perlu koneksi internet.

## Isi folder
| Path | Isi |
|---|---|
| `index.html` | Aplikasi editor |
| `parts.json` | Daftar part (ukuran, tinggi, kategori) |
| `parts/*.wasm` | Mesh part terkompresi (biner, bukan WebAssembly; ekstensi dipilih agar server mana pun menyajikannya) |
| `stl-cetak/` | STL siap cetak untuk aksesori baru + `uji-toleransi.stl` + `PANDUAN-CETAK.txt` |

## Coba di komputer sendiri
Jangan buka `index.html` dengan klik dua kali, karena browser memblokir pemuatan file lokal. Jalankan server kecil dari folder ini:

```bash
python3 -m http.server 8000
```
Lalu buka http://localhost:8000

## Opsi 1: GitHub Pages (gratis)
1. Buat repository baru di https://github.com/new, misalnya `studio-bata`, dengan visibilitas **Public**.
2. Klik **uploading an existing file**, lalu seret **seluruh isi** folder ini (bukan foldernya) dan klik **Commit changes**.
   Jika jumlah file terlalu banyak untuk satu unggahan, unggah dalam dua tahap, atau gunakan git:
   ```bash
   cd studio-bata
   git init && git add . && git commit -m "Studio Bata"
   git branch -M main
   git remote add origin https://github.com/USERNAME/studio-bata.git
   git push -u origin main
   ```
3. Buka **Settings → Pages**. Pada *Source* pilih **Deploy from a branch**, branch **main**, folder **/ (root)**, lalu klik **Save**.
4. Tunggu 1–2 menit. Situs tersedia di `https://USERNAME.github.io/studio-bata/`

## Opsi 2: Netlify Drop (paling cepat, tanpa akun git)
1. Buka https://app.netlify.com/drop
2. Seret folder `studio-bata` ke halaman tersebut.
3. Netlify langsung memberi alamat publik (bisa diganti namanya setelah login).

## Opsi 3: Server kampus / hosting biasa
Unggah seluruh isi folder ke direktori web (misalnya `public_html/studio-bata/`) lewat FTP atau cPanel. Tidak perlu PHP atau database.

## Catatan
- Model yang dibuat pengunjung tersimpan di browser masing-masing (localStorage). Untuk memindahkan model, gunakan **Simpan/Muat**.
- Tombol **Ekspor STL** mengunduh seluruh model dalam satuan mm dengan sumbu Z ke atas, siap untuk slicer.
