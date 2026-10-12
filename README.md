# InventoryManagementSystem-Web-4-
# GlowMart — Inventory Management System

## 1. Deskripsi Proyek

GlowMart adalah aplikasi berbasis web untuk mengelola persediaan produk toko. Aplikasi ini dibuat menggunakan PHP dan MySQL dengan tujuan mempermudah pengelolaan data produk, kategori, supplier, serta transaksi stok masuk dan stok keluar.

Sistem ini memiliki dua jenis pengguna, yaitu Admin dan Staff, dengan hak akses yang berbeda.

## 2. Fitur Aplikasi

- Login dan logout pengguna.
- Pengelolaan data produk (tambah, lihat, ubah, dan hapus).
- Pengelolaan kategori produk.
- Pengelolaan data supplier.
- Hubungan antara produk dan supplier.
- Pencatatan transaksi stok masuk.
- Pencatatan transaksi stok keluar.
- Riwayat transaksi persediaan.
- Dashboard yang menampilkan ringkasan persediaan.
- Peringatan ketika stok produk mencapai batas minimum.
- Pencarian, filter kategori, pengurutan, dan pagination produk.
- Pembatasan hak akses berdasarkan role pengguna.

## 3. Teknologi yang Digunakan

- **Bahasa pemrograman:** PHP
- **Database:** MySQL
- **Web server:** Apache melalui XAMPP
- **Pengelolaan database:** phpMyAdmin
- **Editor kode:** Visual Studio Code
- **Antarmuka:** HTML dan CSS

## 4. Struktur Folder

```text
inventory_management_system/
├── config/
│   └── database.php
├── database/
│   └── schema.sql
├── helpers/
│   ├── auth.php
│   ├── validation.php
│   └── escape.php
├── public/
│   ├── login.php
│   ├── dashboard.php
│   ├── products/
│   │   ├── index.php
│   │   ├── create.php
│   │   ├── edit.php
│   │   ├── delete.php
│   │   ├── category.php
│   │   └── supplier.php
│   └── stock/
│       ├── incoming.php
│       ├── outgoing.php
│       └── history.php
└── views/
    └── header.php
```

## 5. Cara Instalasi dan Menjalankan Aplikasi

1. Instal dan jalankan XAMPP.
2. Aktifkan Apache dan MySQL.
3. Letakkan folder proyek `inventory_management_system` di dalam folder `htdocs`.
4. Buka phpMyAdmin melalui `http://localhost/phpmyadmin`.
5. Buat database dengan nama `glowmart`.
6. Jika database belum berisi tabel, pilih database `glowmart`, lalu impor file `database/schema.sql`.
7. Pastikan konfigurasi koneksi database pada `config/database.php` sesuai dengan konfigurasi MySQL di komputer.
8. Buka aplikasi melalui alamat berikut:

   `http://localhost/inventory_management_system/public/login.php`

Jika database sudah berisi data, lakukan backup terlebih dahulu sebelum mengimpor ulang file SQL agar data yang ada tidak hilang.

## 6. Jenis Pengguna dan Hak Akses

### Admin
Admin memiliki akses untuk mengelola produk, kategori, supplier, serta fitur transaksi dan riwayat stok yang tersedia pada aplikasi.

### Staff
Staff dapat melihat data produk serta melakukan aktivitas stok sesuai dengan izin yang diberikan sistem. Staff tidak memiliki izin untuk mengelola data yang dikhususkan bagi Admin.

## 7. Struktur Database

Database `glowmart` terdiri dari enam tabel utama:

1. **users** — menyimpan data akun pengguna dan role.
2. **categories** — menyimpan kategori produk.
3. **products** — menyimpan informasi produk, SKU, harga, jumlah stok, dan batas minimum stok.
4. **suppliers** — menyimpan informasi pemasok.
5. **product_suppliers** — menghubungkan produk dengan supplier, termasuk harga dari supplier jika tersedia.
6. **stock_movements** — menyimpan riwayat stok masuk dan stok keluar, jumlah, pengguna, serta waktu transaksi.

Relasi antartabel menggunakan primary key dan foreign key untuk menjaga hubungan data.

## 8. Aturan Pengelolaan Stok

- SKU produk harus unik.
- Harga dan jumlah stok harus divalidasi sebelum disimpan.
- Transaksi stok masuk menambah jumlah persediaan.
- Transaksi stok keluar mengurangi jumlah persediaan.
- Transaksi stok keluar tidak boleh melebihi stok yang tersedia.
- Riwayat transaksi mencatat jenis transaksi, produk, jumlah, pengguna, dan waktu.
- Produk yang telah memiliki riwayat transaksi stok tidak dapat dihapus melalui fitur penghapusan produk.

## 9. Keamanan Aplikasi

Aplikasi menerapkan beberapa mekanisme keamanan, yaitu:

- Autentikasi pengguna melalui login.
- Penyimpanan kata sandi menggunakan password hashing.
- Pembatasan akses berdasarkan role.
- Prepared statements untuk query database.
- Validasi input sebelum data diproses.
- Escaping output untuk membantu mencegah serangan XSS.
- Token CSRF pada formulir logout.

## 10. Pengujian Aplikasi

Pengujian dilakukan pada fitur-fitur utama, meliputi:

- Login dan logout Admin serta Staff.
- Pembatasan akses berdasarkan role.
- Pengelolaan produk, kategori, dan supplier.
- Validasi data produk.
- Pencatatan stok masuk dan stok keluar.
- Pencegahan transaksi stok keluar melebihi persediaan.
- Pemeriksaan riwayat transaksi.
- Pengujian pencarian, filter, pengurutan, dan pagination.
- Pemeriksaan statistik pada dashboard.

Berdasarkan pengujian yang telah dilakukan, fitur-fitur utama aplikasi berjalan sesuai hasil pengujian.

## 11. Penutup

GlowMart Inventory Management System dikembangkan untuk membantu pengelolaan produk dan persediaan secara terstruktur melalui aplikasi berbasis web. Dengan adanya pencatatan transaksi stok dan pembatasan hak akses pengguna, pengelolaan persediaan diharapkan menjadi lebih mudah, tertib, dan terkontrol.
