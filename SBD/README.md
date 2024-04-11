# Wypożyczalnia

## Baza danych

```

CREATE DATABASE IF NOT EXISTS wypozyczalnia_samochodow;

USE wypozyczalnia_samochodow;

CREATE TABLE IF NOT EXISTS Samochody (
    id INT AUTO_INCREMENT PRIMARY KEY,
    marka VARCHAR(50) NOT NULL,
    model VARCHAR(50) NOT NULL,
    rok_produkcji YEAR,
    cena DECIMAL(10, 2) NOT NULL,
    dostepnosc BOOLEAN NOT NULL
);

CREATE TABLE IF NOT EXISTS Klienci (
    id INT AUTO_INCREMENT PRIMARY KEY,
    imie VARCHAR(50) NOT NULL,
    nazwisko VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL,
    telefon VARCHAR(20) NOT NULL
);

CREATE TABLE IF NOT EXISTS Wypozyczenia (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_samochodu INT,
    id_klienta INT,
    data_wypozyczenia DATE,
    data_zwrotu DATE,
    FOREIGN KEY (id_samochodu) REFERENCES Samochody(id),
    FOREIGN KEY (id_klienta) REFERENCES Klienci(id)
);
```
## Wsad

```
INSERT INTO Samochody (marka, model, rok_produkcji, cena, dostepnosc) VALUES
('Toyota', 'Corolla', 2019, 150.00, 1),
('Ford', 'Focus', 2018, 130.00, 1),
('Volkswagen', 'Golf', 2020, 170.00, 1),
('BMW', '3 Series', 2017, 200.00, 1),
('Audi', 'A4', 2019, 220.00, 1);

INSERT INTO Klienci (imie, nazwisko, email, telefon) VALUES
('Jan', 'Kowalski', 'jan.kowalski@example.com', '123456789'),
('Anna', 'Nowak', 'anna.nowak@example.com', '987654321'),
('Piotr', 'Wiśniewski', 'piotr.wisniewski@example.com', '567890123'),
('Katarzyna', 'Dąbrowska', 'katarzyna.dabrowska@example.com', '321098765');

INSERT INTO Wypozyczenia (id_samochodu, id_klienta, data_wypozyczenia, data_zwrotu) VALUES
(1, 1, '2024-04-10', '2024-04-15'),
(2, 2, '2024-04-11', '2024-04-16'),
(3, 3, '2024-04-12', '2024-04-17'),
(4, 4, '2024-04-13', '2024-04-18');
