# System-zarz-dzania-firm-produkcyjn-
Projekt na zaliczenie programowania 3
---------------------------------------
using System;
using System.Threading.Channels;

namespace SystemZarzadzaniaProdukcja
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Title = "System Zarządzania Produkcją - Etap 1";

            Console.WriteLine("=== SYSTEM ZARZĄDZANIA PRODUKCJĄ ===\n");

            Console.Write("Podaj nazwę firmy: ");
            string nazwaFirmy = Console.ReadLine();

            Console.Write("Podaj liczbę pracowników: ");
            int liczbaPracownikow;
            while (!int.TryParse(Console.ReadLine(), out liczbaPracownikow) || liczbaPracownikow < 0)
            {
                Console.Write("Błąd! Podaj poprawną liczbę pracowników: ");
            }

            Console.Write("Podaj średnie wynagrodzenie pracownika: ");
            double pensja;
            while (!double.TryParse(Console.ReadLine(), out pensja) || pensja < 0)
            {
                Console.Write("Błąd! Podaj poprawne wynagrodzenie: ");
            }

            Console.Write("Podaj miesięczny budżet firmy: ");
            double budzet;
            while (!double.TryParse(Console.ReadLine(), out budzet) || budzet < 0)
            {
                Console.Write("Błąd! Podaj poprawny budżet: ");
            }

            double kosztPracownikow = liczbaPracownikow * pensja;
            double zysk = budzet - kosztPracownikow;

            Console.WriteLine("\n=== RAPORT MIESIĘCZNY ===");
            Console.WriteLine($"Nazwa firmy: {nazwaFirmy}");
            Console.WriteLine($"Liczba pracowników: {liczbaPracownikow}");
            Console.WriteLine($"Łączne koszty wynagrodzeń: {kosztPracownikow} zł");
            Console.WriteLine($"Budżet: {budzet} zł");

            if (zysk > 0)
            {
                Console.WriteLine($"✅ Firma osiągnęła zysk: {zysk} zł");
            }
            else if (zysk == 0)
            {
                Console.WriteLine("⚖ Firma wyszła na zero.");
            }
            else
            {
                Console.WriteLine($" Firma ma stratę: {-zysk} zł");
            }

            Console.WriteLine("\nWybierz działanie:");
            Console.WriteLine("1. Zwiększ budżet o 10%");
            Console.WriteLine("2. Zmniejsz budżet o 10%");
            Console.WriteLine("3. Zakończ program");
            Console.Write("Twój wybór: ");

            string wybor = Console.ReadLine();

            switch (wybor)
            {
                case "1":
                    budzet *= 1.1;
                    Console.WriteLine($"Nowy budżet: {budzet} zł");
                    break;
                case "2":
                    budzet *= 0.9;
                    Console.WriteLine($"Nowy budżet: {budzet} zł");
                    break;
                case "3":
                    Console.WriteLine("Zamykanie programu...");
                    break;
                default:
                    Console.WriteLine("Nieprawidłowy wybór.");
                    break;
            }

            Console.WriteLine("\nNaciśnij dowolny klawisz, aby zakończyć...");
            Console.ReadKey();
            
            Console.WriteLine("\n=== Dodawanie pracownikow ===");
            Console.WriteLine("Ilu pracownikow chcesz dodac? ");
            int liczba = int.Parse(Console.ReadLine());

            string[] pracownicy = new string[liczba];

            for (int i = 0; i < liczba; i++)
            {
                Console.Write($"Podaj imie pracownika {i + 1}: ");
                pracownicy[i] = Console.ReadLine();
            }

            Console.WriteLine("\nLista pracownikow:");
            foreach (var p in pracownicy)
            {
                Console.WriteLine($"- {p}");
            }
            Console.WriteLine("\n=== DANE PRODUKCYJNE ===");
            Console.WriteLine("Podaj liczbe tygodni: ");
            int tygodnie = int.Parse(Console.ReadLine());
            Console.WriteLine("Podaj liczbe dni w tygodniu: ");
            int dni = int.Parse(Console.ReadLine());

            int[][] produkcja = new int[tygodnie][];

            for (int i = 0; i < tygodnie; i++)
            {
                produkcja[i] = new int[dni];
                Console.WriteLine($"\nTydzien {i + 1}:");
                for (int j = 0; j < dni; j++)
                {
                    Console.Write($"Dzien {j + 1}: ");
                    produkcja[i][j] = int.Parse(Console.ReadLine());
                }
            }


        }
    }
}