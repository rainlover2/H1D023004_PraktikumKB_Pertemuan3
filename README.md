# H1D023004_PraktikumKB_Pertemuan3
import random
import datetime

# Struktur Data: List untuk antrian dan dictionary untuk menyimpan informasi pelanggan
antrian = []
pelanggan_info = {}

def ambil_nomor_antrian(nama):
    nomor = random.randint(100, 999)
    waktu = datetime.datetime.now().strftime("%H:%M:%S")
    antrian.append(nomor)
    pelanggan_info[nomor] = {"nama": nama, "waktu": waktu}
    print(f"Nomor antrian {nomor} untuk {nama} telah diambil pada {waktu}.")

def layani_pelanggan():
    if not antrian:
        print("Tidak ada antrian saat ini.")
        return
    
    nomor = antrian.pop(0)
    pelanggan = pelanggan_info.pop(nomor)
    print(f"Melayani pelanggan {pelanggan['nama']} dengan nomor antrian {nomor} pada {datetime.datetime.now().strftime('%H:%M:%S')}.")

def main():
    opsi = ["1", "2", "3"]
    input_data = ["1", "Audi", "1", "Wildan", "2", "2", "3"]  # Simulasi input otomatis
    index = 0
    
    while True:
        print("\nMenu:")
        print("1. Ambil Nomor Antrian")
        print("2. Layani Pelanggan")
        print("3. Keluar")
        
        if index >= len(input_data):
            print("Simulasi selesai.")
            break
        
        pilihan = input_data[index]
        index += 1
        print(f"> {pilihan}")
        
        if pilihan == "1":
            if index >= len(input_data):
                print("Input tidak tersedia.")
                break
            nama = input_data[index]
            index += 1
            print(f"> {nama}")
            ambil_nomor_antrian(nama)
        elif pilihan == "2":
            layani_pelanggan()
        elif pilihan == "3":
            print("Terima kasih! Program selesai.")
            break
        else:
            print("Pilihan tidak valid, coba lagi.")

if __name__ == "__main__":
    main()
