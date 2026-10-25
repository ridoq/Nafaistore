# 📋 Panduan Kolaborasi & SOP GitHub Tim NAFA iSTORE

Panduan ini dibuat agar alur kerja tim (Ridho, Rista, Viola, Dika, Ipeng) berjalan rapi, cepat, dan terhindar dari *merge conflict*.

---

## 🌳 Struktur Branch

1. **`main`**: Branch produksi / demo final. **Terkunci** (hanya PM yang boleh merge).
2. **`develop`**: Branch integrasi utama. Tempat bertemunya semua fitur yang sudah di-review.
3. **`feat/nama-fitur-nama`**: Branch pengerjaan fitur baru.
   - Contoh: `feat/katalog-viola`, `feat/checkout-rista`, `feat/auth-dika`, `feat/crud-produk-ipeng`.
4. **`fix/nama-bug`**: Branch khusus perbaikan bug.
   - Contoh: `fix/navbar-mobile-viola`.

---

## 🔄 Alur Kerja Sehari-hari (Step-by-Step)

### Langkah 1: Selalu Awali dari Kode Terbaru
Sebelum mulai koding apa pun, pastikan branch `develop` di laptop kamu sudah paling update:
```bash
git checkout develop
git pull origin develop
```

### Langkah 2: Buat Branch Baru untuk Fiturmu
Jangan pernah ngoding di branch `develop` atau `main`!
```bash
git checkout -b feat/nama-fitur-namamu
# Contoh:
git checkout -b feat/katalog-viola
```

### Langkah 3: Koding & Simpan Perubahan (Commit)
Lakukan koding. Jangan tunggu sampai proyek selesai baru commit. Commit per tugas kecil selesai:
```bash
# Cek file apa saja yang diubah
git status

# Tambahkan file ke staging
git add .

# Tulis pesan commit dengan format yang rapi
git commit -m "feat(katalog): slicing layout card produk dan filter harga"
```

#### Format Pesan Commit:
- `feat(modul): deskripsi` → Tambah fitur baru
- `fix(modul): deskripsi` → Perbaiki bug/error
- `style(modul): deskripsi` → Merapikan CSS/tampilan tanpa ubah logika
- `refactor(modul): deskripsi` → Merapikan kode tanpa ubah fungsi

### Langkah 4: Upload Branch ke GitHub (Push)
```bash
git push -u origin feat/nama-fitur-namamu
```
*(Perintah `-u` hanya perlu di awal, push berikutnya cukup `git push`)*.

### Langkah 5: Buat Pull Request (PR) di GitHub
1. Buka repo di GitHub: [github.com/ridoq/Nafaistore](https://github.com/ridoq/Nafaistore)
2. Klik tombol hijau **Compare & pull request**.
3. **PENTING:** Pastikan:
   - **base**: `develop` (jangan pilih main!)
   - **compare**: `feat/nama-fitur-namamu`
4. Beri judul PR yang jelas, misal: `[FE] Slicing Halaman Katalog Produk`.
5. Tulis deskripsi singkat tentang apa saja yang telah dikerjakan.
6. Pada kolom kanan:
   - **Reviewers**: pilih `ridoq` (Ridho)
   - **Assignees**: pilih diri sendiri
7. Klik **Create pull request**.
8. Hubungi Ridho di WA/Discord untuk minta di-review.

---

## 🛑 Aturan Emas & Larangan Keras

1. ❌ **JANGAN PERNAH** `git push origin main` atau `git push origin develop` langsung!
2. ❌ **JANGAN PERNAH** commit file `.env`, folder `node_modules/`, `vendor/`, atau file dump database manual `.sql`!
3. ❌ **JANGAN** mengubah file milik anggota lain tanpa koordinasi terlebih dahulu.
4. ✅ **WAJIB** `git pull origin develop` sebelum bikin branch baru.
5. ✅ Untuk Backend: Buat perubahan database melalui **Laravel Migration & Seeder**, bukan export manual di phpMyAdmin.
