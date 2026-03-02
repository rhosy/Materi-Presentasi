# 📖 Dokumentasi Penggunaan Aplikasi Absensi Sekolah

> Panduan lengkap untuk administrator dalam mengelola dan mengoperasikan sistem absensi sekolah.

---

## 📋 Daftar Isi

1. [Login & Akses](#1-login--akses)
2. [Urutan Setup Awal](#2-urutan-setup-awal-wajib-ikuti-urutan-ini)
3. [Pengaturan Sekolah](#3-pengaturan-sekolah)
4. [Manajemen Pengguna & Role](#4-manajemen-pengguna--role)
5. [Tahun Ajaran](#5-tahun-ajaran)
6. [Semester](#6-semester)
7. [Kelas](#7-kelas)
8. [Data Siswa](#8-data-siswa)
9. [Data Guru & Staff](#9-data-guru--staff)
10. [Kalender Akademik](#10-kalender-akademik)
11. [Manajemen Kartu QR](#11-manajemen-kartu-qr)
12. [Designer Kartu ID](#12-designer-kartu-id)
13. [Absensi](#13-absensi)
14. [Notifikasi WhatsApp](#14-notifikasi-whatsapp)
15. [Laporan](#15-laporan)
16. [Portal Orang Tua](#16-portal-orang-tua)
17. [Perangkat RFID](#17-perangkat-rfid)

---

## 1. Login & Akses

**Halaman:** `/login`

Masukkan **email** dan **password** akun yang telah diberikan oleh administrator sistem.

> ⚠️ Jika lupa password, hubungi administrator untuk reset.

---

## 2. Urutan Setup Awal *(Wajib ikuti urutan ini)*

Sebelum menggunakan sistem untuk absensi, data berikut **harus** diisi terlebih dahulu secara berurutan:

```
① Pengaturan Sekolah
② Tahun Ajaran (aktifkan salah satu)
③ Semester (aktifkan salah satu)
④ Kelas (hubungkan ke tahun ajaran)
⑤ Guru & Staff
⑥ Data Siswa (hubungkan ke kelas)
⑦ Generate Kartu QR untuk siswa & guru
⑧ Siap digunakan!
```

---

## 3. Pengaturan Sekolah

**Menu:** Pengaturan → Pengaturan Sekolah

Isi informasi dasar sekolah dan konfigurasi sistem.

### Data Sekolah

| Field | Keterangan | Wajib |
|-------|-----------|-------|
| Nama Sekolah | Nama lengkap sekolah | — |
| Alamat | Alamat lengkap sekolah | — |
| No. Telepon | Telepon sekolah | — |
| Email | Email resmi sekolah | — |
| Logo Sekolah | File gambar (max 2MB) | — |
| Favicon | Ikon browser (PNG/ICO, max 512KB) | — |

### Konfigurasi Absensi

| Field | Keterangan | Contoh |
|-------|-----------|--------|
| Jam Mulai Absensi | Batas mulai scan kartu | `06:30` |
| Jam Tutup Absensi | Batas akhir scan kartu | `08:00` |
| Toleransi Terlambat | Menit sebelum dianggap terlambat | `15` |

> **Contoh:** Jam mulai `06:30`, toleransi `15` menit → siswa yang scan setelah `06:45` dicatat **Terlambat**.

### Konfigurasi WhatsApp

| Field | Keterangan |
|-------|-----------|
| Aktifkan Notifikasi WA | Toggle on/off |
| URL API WhatsApp | Endpoint API gateway WA yang digunakan |
| API Key | Kunci autentikasi dari penyedia WA API |

### Konfigurasi Peringatan Otomatis

| Field | Keterangan | Contoh |
|-------|-----------|--------|
| Hari Absen Berturut-turut | Trigger peringatan jika absen N hari | `3` |
| Ambang Kehadiran (%) | Peringatan jika kehadiran di bawah % ini | `75` |
| Cooldown Peringatan | Jeda hari antar pengiriman peringatan | `7` |

---

## 4. Manajemen Pengguna & Role

**Menu:** Pengaturan → Pengguna / Role

### Membuat Role Baru

Role menentukan hak akses setiap pengguna. Contoh role: `Admin`, `Kepala Sekolah`, `Tata Usaha`, `Guru Kelas`.

> Role diatur dengan permission yang spesifik (contoh: `students.view`, `attendance.create`, dsb.).

### Membuat Pengguna Baru

| Field | Keterangan | Wajib |
|-------|-----------|-------|
| Nama | Nama lengkap pengguna | ✅ |
| Email | Akan digunakan untuk login | ✅ |
| Password | Minimal 8 karakter | ✅ |
| Konfirmasi Password | Harus sama dengan password | ✅ |
| Role | Pilih minimal satu role | ✅ |
| Aktif | Status akun | — |
| Link ke Data Guru | Hubungkan akun ke data guru (opsional) | — |

> 💡 Menghubungkan akun ke data guru memungkinkan pengguna tersebut punya kartu QR untuk absensi.

---

## 5. Tahun Ajaran

**Menu:** Master Data → Tahun Ajaran

### Menambah Tahun Ajaran

| Field | Keterangan | Contoh |
|-------|-----------|--------|
| Nama | Format bebas, biasanya `YYYY/YYYY` | `2025/2026` |
| Tanggal Mulai | Awal tahun ajaran | `2025-07-14` |
| Tanggal Selesai | Akhir tahun ajaran | `2026-06-30` |

### Mengaktifkan Tahun Ajaran

Klik tombol **Aktifkan** pada baris tahun ajaran yang ingin dijadikan aktif.

> ⚠️ Hanya **satu** tahun ajaran yang bisa aktif sekaligus. Mengaktifkan satu akan menonaktifkan yang lain.

---

## 6. Semester

**Menu:** Master Data → Semester

### Menambah Semester

| Field | Keterangan | Contoh |
|-------|-----------|--------|
| Nama | Nama semester | `Semester Ganjil` |
| Tahun Ajaran | Pilih dari daftar | `2025/2026` |
| Tanggal Mulai | Awal semester | `2025-07-14` |
| Tanggal Selesai | Akhir semester | `2025-12-20` |

> Aktifkan semester yang sedang berjalan dengan klik **Aktifkan**.

---

## 7. Kelas

**Menu:** Master Data → Kelas

### Menambah Kelas

| Field | Keterangan | Contoh | Wajib |
|-------|-----------|--------|-------|
| Nama Kelas | Nama unik kelas | `X IPA 1` | ✅ |
| Tingkat | Pilih tingkat kelas | `10`, `11`, atau `12` | ✅ |
| Tahun Ajaran | Pilih tahun ajaran terkait | `2025/2026` | ✅ |
| Wali Kelas | Pilih dari daftar pengguna (opsional) | — | — |

> 💡 Buat semua kelas yang ada di sekolah. Tiap kelas terikat ke satu tahun ajaran.

---

## 8. Data Siswa

**Menu:** Siswa

### Menambah Siswa Satu per Satu

| Field | Keterangan | Wajib |
|-------|-----------|-------|
| Kelas | Pilih kelas yang sudah dibuat | ✅ |
| NIS | Nomor Induk Siswa (unik) | ✅ |
| NISN | Nomor Induk Siswa Nasional (opsional, unik) | — |
| Nama Lengkap | Nama siswa | ✅ |
| Jenis Kelamin | Laki-laki / Perempuan | ✅ |
| Tanggal Lahir | Format tanggal, harus sebelum hari ini | ✅ |
| Foto | File gambar, max 2MB (opsional) | — |
| Alamat | Alamat lengkap (opsional) | — |

**Data Orang Tua/Wali** *(opsional, bisa diisi hingga 2 orang)*

| Field | Keterangan |
|-------|-----------|
| Nama | Nama orang tua/wali |
| Hubungan | Ayah / Ibu / Wali |
| No. HP | Nomor WhatsApp orang tua |
| WA Aktif | Centang jika nomor adalah WhatsApp |

> 📲 Nomor WA orang tua **wajib diisi** agar notifikasi kehadiran bisa terkirim.

---

### Import Siswa dari Excel

Untuk input data siswa dalam jumlah banyak sekaligus:

1. Klik **Download Template** untuk mendapatkan file Excel kosong
2. Isi data siswa sesuai format di template
3. Klik **Import** dan upload file Excel yang sudah diisi
4. Sistem akan memvalidasi data dan menampilkan hasil import

---

## 9. Data Guru & Staff

**Menu:** Guru & Staff

### Menambah Guru/Staff

| Field | Keterangan | Wajib |
|-------|-----------|-------|
| Nama Lengkap | Nama guru/staff | ✅ |
| NIP | Nomor Induk Pegawai (opsional, unik) | — |
| Mata Pelajaran | Mata pelajaran yang diajarkan | — |
| No. Telepon/WA | Nomor kontak | — |
| Foto | File gambar, max 2MB | — |
| Aktif | Status aktif/nonaktif | — |

> 💡 Setelah data guru dibuat, hubungkan ke akun pengguna jika guru tersebut perlu login ke sistem.

---

## 10. Kalender Akademik

**Menu:** Master Data → Kalender Akademik

Kalender akademik digunakan oleh sistem untuk menentukan hari sekolah vs hari libur saat menghitung rekap kehadiran.

### Menambah Event/Libur

| Field | Keterangan | Contoh | Wajib |
|-------|-----------|--------|-------|
| Tahun Ajaran | Pilih tahun ajaran | `2025/2026` | ✅ |
| Nama Event | Deskripsi singkat event | `Idul Fitri` | ✅ |
| Jenis | Kategori event | Libur / Event / Ujian / Lainnya | ✅ |
| Tanggal Mulai | Awal event | `2026-03-30` | ✅ |
| Tanggal Selesai | Akhir event | `2026-04-02` | ✅ |
| Hari Sekolah? | Apakah masih ada kegiatan sekolah | ✅/❌ | — |
| Keterangan | Catatan tambahan | — | — |

---

## 11. Manajemen Kartu QR

**Menu:** Manajemen Kartu → Kartu Siswa / Kartu Guru & Staff

Kartu QR digunakan siswa dan guru untuk scan absensi.

### Generate Kartu Siswa

1. Buka halaman **Kartu Siswa**
2. Cari siswa yang belum punya kartu (tandanya tidak ada QR aktif)
3. Klik **Generate Kartu** pada baris siswa tersebut
4. Kartu QR otomatis dibuat dengan kode unik

### Assign RFID ke Siswa

Jika menggunakan kartu RFID fisik:

1. Klik **Assign RFID** pada baris siswa
2. Masukkan **kode RFID** dari kartu fisik siswa
3. Simpan — kartu RFID sekarang terhubung ke siswa tersebut

### Nonaktifkan Kartu

Jika kartu siswa hilang atau rusak:
1. Klik **Nonaktifkan** pada kartu yang bersangkutan
2. Generate kartu baru untuk siswa tersebut

### Cetak Kartu

1. Pilih **kelas** yang ingin dicetak kartunya
2. Klik **Cetak Kartu**
3. Halaman cetak terbuka — gunakan `Ctrl+P` / `Cmd+P` untuk print

---

## 12. Designer Kartu ID

**Menu:** Pengaturan → Designer Kartu

Buat desain kartu ID sesuai identitas sekolah sebelum mencetak.

### Membuka Designer

1. Pilih **Kartu Siswa** atau **Kartu Guru & Staff**
2. Klik **Desain** untuk membuka halaman editor

### Elemen yang Bisa Ditambahkan

| Tombol | Fungsi |
|--------|--------|
| Nama / NIS / Kelas / dll | Data dinamis — otomatis terisi dari database |
| Logo | Logo sekolah (otomatis menggunakan logo dari pengaturan) |
| Foto | Foto siswa/guru |
| QR Code | Kode QR untuk scan absensi |
| Teks Bebas | Teks statis yang Anda ketik sendiri |

### Cara Mendesain

1. **Tambah elemen** dengan klik tombol di panel kiri
2. **Drag** elemen ke posisi yang diinginkan di canvas
3. **Resize** elemen dengan tarik sudut/sisi elemen
4. **Klik elemen** untuk membuka properti di panel kanan:
   - Posisi & ukuran (X%, Y%, Lebar%, Tinggi%)
   - Font (jenis, ukuran, warna, tebal)
   - Background, border, border-radius
   - Opacity (transparansi)
   - Urutan layer (z-index)
5. **Orientasi**: Toggle Landscape/Portrait di toolbar
6. **Background**: Upload gambar background atau pilih warna
7. **Simpan** dengan klik tombol **Simpan** di toolbar

> 💡 Setelah desain disimpan, semua cetak kartu akan menggunakan desain ini secara otomatis.

---

## 13. Absensi

**Menu:** Absensi

### Metode 1: Scan QR (Halaman Scan)

1. Buka **`/scan`** di browser perangkat yang dipasang di pintu/gerbang
2. Halaman scan kamera terbuka — arahkan ke QR kartu siswa/guru
3. Sistem otomatis mencatat kehadiran dan mengirim notifikasi WA

### Metode 2: Input Manual

1. Buka **Absensi → Input Absensi**
2. Pilih kelas dan tanggal
3. Isi status kehadiran tiap siswa: **Hadir / Izin / Sakit / Alpha**
4. Klik **Simpan**

### Metode 3: Absensi Massal

1. Buka **Absensi → Absensi Massal**
2. Pilih kelas — semua siswa tampil
3. Ubah status yang diperlukan
4. Simpan sekaligus

### Status Kehadiran

| Status | Keterangan |
|--------|-----------|
| Hadir | Siswa hadir tepat waktu |
| Terlambat | Hadir melebihi toleransi waktu |
| Izin | Ada surat izin resmi |
| Sakit | Sakit (dengan/tanpa keterangan dokter) |
| Alpha | Tidak hadir tanpa keterangan |

---

## 14. Notifikasi WhatsApp

**Menu:** Notifikasi

> ⚠️ Pastikan konfigurasi WA API sudah diisi di Pengaturan Sekolah.

### Template Pesan

Template adalah format pesan yang dikirim otomatis. Variabel dinamis yang tersedia:

| Variabel | Diganti dengan |
|----------|---------------|
| `{student_name}` | Nama siswa |
| `{school_name}` | Nama sekolah |
| `{date}` | Tanggal absensi |
| `{time}` | Jam absensi |
| `{status}` | Status kehadiran |
| `{class_name}` | Nama kelas |

Untuk edit template: **Notifikasi → Template** → pilih template → edit → simpan.

---

### Log Notifikasi

**Notifikasi → Log** menampilkan histori semua pesan yang terkirim beserta statusnya.

- ✅ **Terkirim** — pesan berhasil sampai
- ❌ **Gagal** — pesan tidak terkirim

Klik **Kirim Ulang** untuk mencoba kembali pesan yang gagal.

---

### Blast Notifikasi

Kirim pengumuman ke semua orang tua sekaligus:

1. Buka **Notifikasi → Blast**
2. Pilih target penerima:
   - **Semua** — seluruh orang tua di database
   - **Per Kelas** — pilih kelas tertentu
3. Ketik pesan (10–1000 karakter)
4. Klik **Kirim**

---

## 15. Laporan

**Menu:** Laporan

### Laporan Per Siswa

1. Buka **Laporan → Per Siswa**
2. Pilih siswa yang ingin dilihat
3. Filter berdasarkan **rentang tanggal** atau **semester**
4. Lihat ringkasan: total hadir, terlambat, izin, sakit, alpha
5. Export ke **Excel** atau **PDF**

### Laporan Per Kelas

1. Buka **Laporan → Per Kelas**
2. Pilih kelas dan periode
3. Lihat rekap semua siswa dalam kelas tersebut
4. Export ke **Excel** atau **PDF**

### Laporan Global

1. Buka **Laporan → Global**
2. Lihat rekap kehadiran seluruh sekolah
3. Export ke **Excel** atau **PDF**

### Laporan Guru

1. Buka **Laporan → Guru & Staff**
2. Lihat rekap kehadiran semua guru/staff

---

## 16. Portal Orang Tua

Portal orang tua adalah halaman khusus yang bisa diakses orang tua **tanpa perlu login**, menggunakan **link unik** (token).

### Cara Generate Token Portal

1. Buka detail siswa (klik nama siswa di daftar)
2. Di bagian **Data Orang Tua**, klik **Generate Link Portal**
3. Salin link yang muncul
4. Bagikan ke orang tua via WhatsApp atau media lain

### Yang Bisa Dilihat Orang Tua di Portal

- **Riwayat Kehadiran** — rekap absensi anak
- **Notifikasi** — pengumuman dari sekolah
- **Izin/Sakit** — orang tua bisa mengajukan izin langsung dari portal

### Form Izin di Portal

| Field | Keterangan | Wajib |
|-------|-----------|-------|
| Tanggal Mulai | Awal izin/sakit | ✅ |
| Tanggal Selesai | Akhir izin/sakit | ✅ |
| Alasan | Penjelasan izin | ✅ |

---

## 17. Perangkat RFID

**Menu:** Pengaturan → Perangkat RFID

Perangkat RFID (scanner fisik di gerbang/pintu) perlu didaftarkan agar bisa mengirim data absensi ke sistem.

### Mendaftarkan Perangkat

1. Buka **Perangkat RFID**
2. Klik **Tambah Token**
3. Isi nama perangkat (contoh: `Scanner Gerbang Utama`)
4. Token otomatis dibuat — salin token ini
5. Masukkan token ke konfigurasi firmware perangkat RFID

### Mengelola Token

| Aksi | Fungsi |
|------|--------|
| Toggle Aktif/Nonaktif | Matikan perangkat sementara tanpa hapus |
| Regenerate Token | Buat token baru (token lama langsung tidak valid) |
| Hapus | Hapus perangkat permanen |

---

## ❓ Tips & Troubleshooting

### Siswa scan tapi tidak tercatat
- Pastikan jam scan masih dalam rentang **jam mulai–jam tutup absensi**
- Periksa apakah kartu QR siswa masih **aktif**
- Cek apakah tanggal hari ini adalah hari libur di **Kalender Akademik**

### Notifikasi WA tidak terkirim
- Cek WA API URL dan API Key di **Pengaturan Sekolah**
- Pastikan toggle **Aktifkan Notifikasi WA** dalam kondisi ON
- Lihat **Log Notifikasi** untuk melihat pesan error

### Data siswa tidak muncul saat absensi
- Pastikan siswa sudah terdaftar di **kelas** yang aktif
- Pastikan tahun ajaran sudah **diaktifkan**

### Kartu tidak bisa dicetak
- Pastikan siswa sudah punya kartu QR aktif (sudah di-generate)
- Izinkan pop-up browser jika halaman cetak tidak muncul

---

*Dokumentasi ini dibuat berdasarkan versi terkini aplikasi. Hubungi administrator sistem untuk pertanyaan lebih lanjut.*
