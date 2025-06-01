# Skrip Otomatisasi Laporan Reporting Engineer Jubelio

## Deskripsi
Skrip Python (`jubelio_reporting_automation.py`) ini dirancang untuk mengotomatisasi tugas-tugas yang biasa dihadapi oleh seorang Reporting Engineer di Jubelio, sebagaimana dijelaskan dalam sebuah studi kasus. Skrip ini akan melakukan hal berikut:
1.  Membuat database SQLite (`jubelio_report_data.db`) dan skema tabel yang diperlukan.
2.  Mengimpor data kode promo dari file `promo_code.csv`.
3.  Mengisi tabel-tabel lain (`marketplace_table`, `sales_table`, `seller_table`, `buyer_table`, `shipping_table`) dengan data contoh untuk keperluan demonstrasi.
4.  Memproses data untuk mengisi tabel laporan `Q3_Q4_Review` (analisis efektivitas promo Kuartal 3 dan 4) dan `shipping_summary` (ringkasan pengiriman untuk bulan Desember).
5.  Melakukan analisis data yang mirip dengan Pivot Table menggunakan Pandas untuk:
    * Trend aktivitas total penjualan bulanan setelah terpotong promo.
    * Trend bulanan perbandingan jumlah rasio penggunaan promo dan yang tidak menggunakan promo.
6.  Menghasilkan visualisasi (grafik garis dan grafik batang bertumpuk) dari hasil analisis menggunakan Matplotlib.
7.  Mengekspor semua data mentah yang relevan (`Q3_Q4_Review_Data`, `Shipping_Summary_Data`), hasil analisis (dalam bentuk tabel mirip Pivot), dan visualisasi ke dalam satu file Excel (`Jubelio_Report_TAUFIQURRAHMAN.xlsx`).
8.  Menghasilkan file `.sql` (`jubelio_database_schema_and_queries.sql`) yang berisi semua perintah SQL yang dieksekusi untuk pembuatan skema dan manipulasi data.
9.  Semua file output akan disimpan dalam folder `Task5_TAUFIQURRAHMAN_Python_Output`.

## Prasyarat
Sebelum menjalankan skrip, pastikan Anda memiliki:
1.  **Python 3.x** terinstal di sistem Anda.
2.  Library Python berikut terinstal:
    * `pandas`
    * `openpyxl`
    * `matplotlib`
    Anda dapat menginstalnya menggunakan pip:
    ```bash
    pip install pandas openpyxl matplotlib
    ```
3.  File **`promo_code.csv`** (yang telah Anda sediakan) berada di **direktori yang sama** dengan file skrip Python (`jubelio_reporting_automation.py`).

## Struktur File Proyek (Direkomendasikan)
.├── jubelio_reporting_automation.py  # Skrip utama Python├── promo_code.csv                   # File data input kode promo└── README.md                        # File ini
## Cara Menjalankan Skrip
1.  **Simpan File:** Pastikan file `jubelio_reporting_automation.py` dan `promo_code.csv` berada dalam satu direktori.
2.  **Buka Terminal atau Command Prompt:** Navigasikan ke direktori tempat Anda menyimpan file-file tersebut.
3.  **Jalankan Skrip:** Eksekusi skrip menggunakan perintah berikut:
    ```bash
    python jubelio_reporting_automation.py
    ```
4.  **Periksa Output:** Setelah skrip selesai berjalan, sebuah folder bernama `Task5_TAUFIQURRAHMAN_Python_Output` akan dibuat (atau diperbarui jika sudah ada) di direktori yang sama.

## Output yang Dihasilkan
Di dalam folder `Task5_TAUFIQURRAHMAN_Python_Output`, Anda akan menemukan file-file berikut:

1.  **`Jubelio_Report_TAUFIQURRAHMAN.xlsx`**:
    File Excel ini berisi beberapa sheet:
    * `Q3_Q4_Review_Data`: Data mentah dari tabel `Q3_Q4_Review`.
    * `Pivot_Revenue`: Tabel ringkasan (mirip Pivot Table) yang menunjukkan tren penjualan bulanan setelah promo, beserta grafik garis visualisasinya.
    * `Pivot_Rasio_Promo`: Tabel ringkasan (mirip Pivot Table) yang menunjukkan perbandingan rasio penggunaan promo dan non-promo per bulan, beserta grafik batang bertumpuk 100% sebagai visualisasinya.
    * `Shipping_Summary_Data`: Data mentah dari tabel `shipping_summary`.

2.  **`jubelio_database_schema_and_queries.sql`**:
    File teks ini berisi semua perintah SQL yang digunakan oleh skrip untuk:
    * Membuat skema tabel.
    * Memasukkan data (termasuk data contoh dan data yang diproses).
    * Kueri untuk mengisi tabel laporan.

3.  **`jubelio_report_data.db`**:
    File database SQLite. Ini adalah database aktual yang dibuat dan diisi oleh skrip. Anda dapat membukanya menggunakan alat bantu SQLite (seperti DB Browser for SQLite) untuk memeriksa tabel dan data secara langsung.

## Catatan Tambahan
* **Data Contoh:** Skrip ini menggunakan data contoh untuk tabel-tabel selain `promo_code` (yaitu `sales_table`, `marketplace_table`, dll.) untuk tujuan demonstrasi. Jika Anda memiliki data aktual untuk tabel-tabel tersebut, Anda perlu memodifikasi bagian `populate_sample_data()` dalam skrip atau menggantinya dengan proses impor data Anda sendiri.
* **Idempotensi:** Skrip ini dirancang untuk bersifat idempoten. Jika Anda menjalankannya beberapa kali, file database (`.db`) akan dihapus dan dibuat ulang untuk memastikan hasil yang konsisten dari awal setiap kali dijalankan. Folder output dan file di dalamnya akan ditimpa jika sudah ada.
* **Pembuatan Label Pengiriman Fisik:** Skrip ini menghasilkan data yang diperlukan untuk label pengiriman dalam sheet `Shipping_Summary_Data` di file Excel. Untuk membuat label fisik dengan layout "2 Across dan 1 Down" (atau layout lainnya), Anda perlu menggunakan fitur Mail Merge di aplikasi pengolah kata (seperti Microsoft Word atau LibreOffice Writer) dengan menggunakan data dari sheet tersebut sebagai sumbernya.

---
*Dibuat oleh TAUFIQURRAHMAN*
*Tanggal: 1 Juni 2025*
