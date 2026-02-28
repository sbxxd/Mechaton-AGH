# Algorytm sterowania robotem SCARA dla losowej manipulacji obiektami - MECHATON AGH 2025

## 📋 Opis działania

Robot realizuje pracę w dwóch fazach:
1.  **Inicjalizacja i Rozstawianie:** Pobranie 4 klocków z magazynu (siatka 2x2) wejściowego i losowe rozmieszczenie ich na głównej planszy roboczej (siatka 3x3).
2.  **Sortowanie:** Ciągłe, losowe przekładanie klocków pomiędzy wolnymi miejscami na planszy, z zachowaniem zasad kolizji (nie odkładamy klocka na zajęte miejsce).

## 🎥 Prezentacja Działania Układu

[![Prezentacja działania układu](http://img.youtube.com/vi/kAkIM0crl6g/0.jpg)](http://www.youtube.com/watch?v=kAkIM0crl6g)

## 🖥️ Wykorzystane środowiska
![EPSON RC+](https://img.shields.io/badge/EPSON_RC+-v8.0-blue?style=for-the-badge)
![Autodesk Inventor](https://img.shields.io/badge/Autodesk_Inventor-CAD-orange?style=for-the-badge)
* **🔵 EPSON RC+ 8.0** – Zaprogramowanie ruchu i symulacji dla wirtualnego robota **SCARA** w **języku SPEL+**.
* **🟠 Autodesk Inventor** – Zaprojektowanie elementów i zaimportowanie ich do symulacji.

## 🧠 Zastosowane Rozwiązania

* **Logika stanu:** Wykorzystanie tablicy globalnej `iDetails` do mapowania fizycznej planszy na wirtualną logikę.
* **Symulacja chwytaka:** Pełna wizualizacja procesu chwytania (`SimPick`) i puszczania (`SimPlace`) obiektów w środowisku 3D Epson RC+.
* **Losowość:** Użycie generatora liczb losowych (`Rnd`) do wyboru klocka i miejsca docelowego.
* **Obsługa błędów:** Zabezpieczenia przed zgubieniem logicznej pozycji klocka.
* **Reset środowiska:** Automatyczne przywracanie obiektów 3D do pozycji startowych po restarcie programu.
  
## 📂 Struktura Kodu

* **`Main`**: Główna pętla sterująca. Inicjalizuje zmienne, resetuje środowisko i zarządza fazami ruchu.
* **`ResetSimGrip`**: Funkcja pomocnicza czyszcząca przypisania obiektów do chwytaka (rozwiązuje problem "przyklejonych" klocków po restarcie).
* **`SimPick` / `SimPlace`**: Funkcje obsługujące komendy symulatora (`SimSet`), które wizualnie łączą obiekt z flanszą robota.
* **`homecube1-4`**: Funkcje resetujące współrzędne X,Y,Z klocków do pozycji startowej w magazynie.
