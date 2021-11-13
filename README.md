# Internet-Messenger


# Internet Communicator



## Cel systemu
Celem jest stworzenie aplikacji platformy społecznościowej dla indywidualnych/firmowych użytkowników gdzie będą mogli organizować się w grupy do wymiany wiadomości, notatek, zdjęć i innych rodzajów informacji.

Użytkownik zarejestrowany za pomocą platformy będzie mógł wymieniać się wiadomościami indywidalnie bądź grupowo, a także przeglądać treści umieszczone przez innych użytkowników.

Platforma posiadała będzie z góry narzucone grupy których członkami będą zarejestrowani użytkownicy (np. w przypadku konta firmowego użytkownik będzie przypisywany do grupy organizacji) lub sami będą mogli tworzyć takowe grupy i zarządzać treściami tam umieszczanymi.
## Słownik pojęć
**Treść** - materiały tworzone przez użytkownika. Mogą to być posty, komentarze, zdjęcia, notatki. Mogą być dostępne **publicznie** (dla wszystkich) lub **prywatne** (dla członków grupy).

**Moduł** - produkt cząstkowy systemu, posiadający wyodrębiony zestaw funkcjonalności. 

**Grupa**  - kompozycja treści i grup. W odrębie grupy użytkownik będzie mógł tworzyć treści jak i nowe grupy. 

**Uprawnienia** - prawa jakie będą przypisywane członkom grupy. Zależnie od ich poziomu będzie mógł tworzyć/wyświetlać treści. 

## Wymagania
1. Aplikacja będąca przedmiotem specyfikacji działać będzie na systemach komputerowych Windows w trybie aplikacji internetowej i desktopowej.
2. Aplikacja do działania powinna mieć zapewniony dostęp do internetu. 
3. Aplikacja zostanie wykonana w technologii C# .NET Framework oraz z zastosowaniem relacyjnej bazy danych SQL.
4. Komunikacja klienta z bazą danych będzie realizowana przy użyciu JSON oraz REST API.

## Aktorzy i uprawnienia
 **Użytkownicy**
- **Użytkownik niezarejestrowany** - użytkowników który może jedynie wyświetlać publiczne treści.
- **Użytkownik zarejestrowany** - użytkownik posiadający utworzone konto po stronie serwisu. Z pośród nich wyróżnić będzie można:
-- **Użytkownik firmowy** - którego konto od momentu założenia będzie członkiem określonej grupy (np. organizacji w której pracuje).
-- **Użytkownik indywidualny** - który nie będzie związany z żadną organizacją.  

**Uprawnienia**
- **Użytkownik niezarejestrowany** posiadać będzie uprawnienia do odczyty treści.
- **Użytkownicy zarejestrowany** posiadać będą uprawnienia do odczytu, tworzenia i publikowania nowych treści, jak i do tworzenia, dołączania i moderowania grup, przy czym uprawnienia **użytkowników firmowych** będą z góry określone przez administratora grupy.

**Hierarchia użytkowników** 
![asd](https://i.ibb.co/2hcF1GF/userhierachy.jpg "asd")


## Specyfikacja użytkowników
| Nazwa | Użytkownik niezarejestrowany |
|--|--|
| Opis | Użytkownik nie posiadający identyfikującego go konta po stronie serwisu |
| Przypadki użycia  |Odczytywanie treści, otwieranie konta, logowanie |
| Uprawnienia | Odczyt publicznych treści |
-
| Nazwa | Użytkownik zarejestrowany firmowy|
|--|--|
| Opis | Użytkownik posiadający konto identyfikujące go po stronie serwisu jako pracownika określonej organizacji narzucając mu przy tym członkostwo w określonych grupach |
| Przypadki użycia  |Odczytywanie treści, tworzenie treści, modyfikowanie treści, publikowanie treści, wylogowanie |
| Uprawnienia | Odczyt treści, tworzenie treści, modyfikowanie treści, publikowanie treści |
-
| Nazwa | Użytkownik zarejestrowany indywidualny |
|--|--|
| Opis | Użytkownik posiadający identyfikującego go konto po stronie serwisu |
| Przypadki użycia  | Odczytywanie treści, tworzenie treści, modyfikowanie treści, publikowanie treści, tworzenie nowych grup, dołączanie do istniejących |
| Uprawnienia | Odczyt treści, tworzenie treści, modyfikowanie treści, tworzenie i dołączanie do grup, nadawanie uprawnień w grupach |
-
| Nazwa | Warstwa pośrednia |
|--|--|
| Opis | Aktor odpowiedzialny za przetwarzanie żądań użytkowników i wysyłanie ich do serwera, a także wysyłanie odpowiedzi serwera do użytkowników |
| Przypadki użycia  | Odczytywanie treści, tworzenie treści, modyfikowanie treści, publikowanie treści, tworzenie nowych grup, dołączanie do istniejących |
| Uprawnienia | Odczyt treści, tworzenie treści, modyfikowanie treści Tworzenie i dołączanie do grup Nadawanie uprawnień w grupach |

## Funkcjonalność aplikacji
|Nazwa| Tworzenie konta |
|--|--|
| Opis | Aplikacja oferuje tworzenie konta poprzez dostarczone przez użytkownika dane po poprawnej ich weryfikacji przez system|
| Aktorzy | Użytkownik niezarejestrowany |
| Uprawnienia | - |
- 
|Nazwa| Logowanie |
|--|--|
| Opis | Za pomocą dostarczonych danych uwierzytelniających użytkownik po potwierdzeniu swojej tożsamości ma możliwość korzystania z funkcji serwisu|
| Aktorzy | Użytkownik niezarejestrowany |
| Uprawnienia | - |
-
|Nazwa| Wylogowanie |
|--|--|
| Opis | Aplikacja oferuje użytkownikom przejście ze stanu zarejestrowany na niezarejestrowany|
| Aktorzy | Użytkownik zarejestrowany |
| Uprawnienia | - |
-
|Nazwa| Tworzenie treści |
|--|--|
| Opis | Użytkownik zarejestrowany będzie miał możliwość tworzenia nowych treści|
| Aktorzy | Użytkownik zarejestrowany |
| Uprawnienia | Tworzenie treści |
-
|Nazwa| Modyfikowanie treści |
|--|--|
| Opis | Użytkownicy będą mogli modyfikować istniejące treści|
| Aktorzy | Użytkownik zarejestrowany |
| Uprawnienia | Modyfikowanie treści |
-
|Nazwa| Tworzenie grup|
|--|--|
| Opis | Użytkownicy zarejestrowani indywidualni będą mogli tworzyć nowe grupy|
| Aktorzy | Użytkownik zarejestrowany indywidualny |
| Uprawnienia | Tworzenie grup|
-
|Nazwa| Modyfikowanie grup |
|--|--|
| Opis | Użytkownicy będą mogli dodawać nowych członków do grup|
| Aktorzy | Użytkownik zarejestrowany indywidualny |
| Uprawnienia | Modyfikowanie grup |
-
### Opis modułów
- **Tablica** - moduł dla którego głównym źródłem informacji będą treści zamieszczone na grupach do których użytkownik ma dostęp
- **Grupy** - Wgląd do każdej grupy będzie realizowany poprzez moduł, gdzie treści będą umieszczane przez jej członków
- **Konto** - miejsce gdzie użytkownik będzie mógł zarządzać swoim kontem 

### Szkic przykładowego modułu
![enter image description here](https://i.ibb.co/NnvqjLG/app.jpg)

## Przypadki użycia
### Dla użytkowników niezarejestrowanych
![enter image description here](https://i.ibb.co/YTd4thb/guest.jpg)
### Dla użytkowników zarejestrowanych
![enter image description here](https://i.ibb.co/m6GWB6q/user.jpg)
## Opis architektury

Grupy wraz z ich zawartością będą tworzyły kompozycje obiektów. W tym celu wykorzystany zostanie wzorzec projektowy kompozycji.

Interfejs z którego będą korzystały grupy razem z zawartością będzie posiadał metody powiadamiania użytkowników którzy zasubskrybowali daną treść aby otrzymywać powiadomienia o zmianach. Do tego wykorzystany został wzorzec obserwator. 

Dodatkowo, interfejs będzie częściom abstrakcyjnej klasy odpowiedzialnej za widok, a całość będzie połączona wzorcem projektowym most.

Do tworzenia użytkowników wykorzystany zostanie wzorzec projektowy metoda wytwórcza.

Do komunikacji klienta z serwerem wykorzystany zostanie wzorzec projektowy Singleton.

![enter image description here](https://i.ibb.co/LYhCDzR/diagram.jpg)
