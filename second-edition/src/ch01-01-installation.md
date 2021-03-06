## Встановлення

Перше, що треба зробити, щоб почати використовувати Rust - це встановити її. 
Щоб запускати команди з цього розділу, вам знадобиться з'єднання з Інтернетом, 
бо ми завантажимо Rust з Інтернету.

> Примітка: Якщо ви з якихось причин не бажаєте використовувати `rustup`, 
> прочитайте [сторінку встановлення Rust](https://www.rust-lang.org/tools/install), щоб дізнатися про інші варіанти.

Наступні кроки встановлять найостаннішу стабільну версію компілятора Rust. 
Принципи стабільності Rust гарантують, що всі приклади в цій книжці, які можна 
скомпілювати, будуть компілюватися в новіших версіях Rust. Повідомлення можуть 
незначно змінюватися від версії до версії, бо Rust часто покращує повідомлення 
і попередження про помилки. Іншими словами, будь-яка новіша стабільна версія 
Rust, яку ви встановите за цією інструкцією, має працювати відповідно змісту 
до цієї книжки.

> ### Запис у командному рядку
>
> У цьому розділі і надалі в книзці ми використовуватимемо команди терміналу. 
> Рядки, що треба вводити в термінал, починаються з `$`. Не треба вводити сам 
> символ `$`; він лише позначає початок команди. Рядки, що не починаються з `$`,
> зазвичай відображають те, що виводить попередня команда. Крім того, приклади,
> специфічні для PowerShell, будуть починатися на `>` замість `$`.

### Встановлення `rustup` на Linux або macOs

Якщо ви користувач Linux або Mac, відкрийте термінал і введіть цю команду:

```text
$ curl https://sh.rustup.rs -sSf | sh
```

Ця команда завантажує сценарій і почнає встановлення інструменту `rustup`, що 
встановить останню стабільну версію Rust. Можливо, у вас запитають ваш 
пароль. Якщо встановлення буде успішним, з'явиться цей рядок:

```text
Rust is installed now. Great!
```

Якщо ви бажаєте, можете завантажити сценарій і дослідити його перед запуском.

Сценарій встановлення автоматично додасть Rust до системної змінної PATH, коли 
ви наступного разу увійдете до системи. Якщо ви хочете почати використовувати 
Rust негайно, а не перезапускати термінал, виконайте цю команду, щоб додати Rust
до системної змінної PATH вручну:

```text
$ source $HOME/.cargo/env
```

Або ж можете додати такий рядок до файлу *~/.bash_profile*:
```text
$ export PATH="$HOME/.cargo/bin:$PATH"
```

Крім того, вам знадобиться якийсь лінкувальник (linker). Швидше за все, він уже 
встановлений, але якщо ви спробуєте скомпілювати програму на Rust і отримаєте 
повідомлення, що лінкувальник неможливо запустити, це означатиме, що 
лінкувальник не встановлено в системі і вам потрібно встановити його вручну.
Компілятори мови C зазвичай мають потрібний лінкувальник. Перегляньте 
документацію до вашої системи, щоб дізнатися, як встановити компілятор C. Також
деякі поширені пакети Rust залежать від коду на C і потребуватимуть 
компілятора C. Враховуючи це, може бути варто встановити його зараз.

### Встановлення `rustup` на Windows

На Windows перйдіть на [https://www.rust-lang.org/tools/install][install] 
і дотримуйтесь інструкцій, щоб встановити Rust. У певний момент встановлення ви
отримаєте повідомлення, що вам також знадобляться інструменти побудови C++ для 
Visual Studio 2013 чи пізнішої. Найпростіший спосіб отримати інструменти 
побудови - встановити [Build Tools for Visual Studio 2019][visualstudio]. 
Інструменти розташовані в розділі "Інші інструменти" (Other Tools) і 
"Frameworks".

[install]: https://www.rust-lang.org/tools/install
[visualstudio]: https://www.visualstudio.com/downloads/#build-tools-for-visual-studio-2019

Надалі книжка використовує команди, що працюють і як у *cmd.exe*, так і в 
PowerShell. Якщо будуть відмінності, ми пояснимо, що робити.

### Оновлення і видалення

Після встановлення Rust за допомогою `rustup`, оновлення до останньої версії 
робиться легко. З командної оболонки запустіть такий сценарій оновлення:

```text
$ rustup update
```

Щоб видалити Rust і `rustup`, виконайте такий сценарій видалення з командної 
оболонки:

```text
$ rustup self uninstall
```

### Вирішення проблем

Щоб перевірити, чи правильно встановилася Rust, відкрийте командну оболонку і 
введіть рядок:

```text
$ rustc --version
```

Ви маєте побачити номер версії, геш-код та дату коміту останньої випущеної стабільної
версії в такому форматі:

```text
rustc x.y.z (abcabcabc yyyy-mm-dd)
```

Якщо ви це бачите, Rust було успішно встановлено! Як ні і ви в Windows, 
переконайтеся, що Rust є у системній змінній `%PATH%`. Якщо вона там є і Rust 
все одно не працює, є кілька місць, де вам можуть надати допомогу. 
Найпростіше - це канал #beginners на [офіційному Rust Discord][discord]. Там ви
можете списатися з іншими растацеанцями (кумедне ім'я, яким ми звемо себе), які
можуть допомогти вам розібратися. Інші чудові ресурси включають 
[користувацький форум][users] та [Stack Overflow][stackoverflow].

[discord]: https://discord.gg/rust-lang
[users]: https://users.rust-lang.org/
[stackoverflow]: http://stackoverflow.com/questions/tagged/rust

### Локальна документація

Програма встановлення також включає локальну копію документації, тож ви можете 
читати її в офлайні. Запустіть `rustup doc`, щоб відкрити локальну документацію 
у веб-переглядачі.

Кожного разу, коли ви зустрінете тип чи функцію у стандартній бібліотеці і не
будете певні, що воно робить чи як ним користатися, скористайтеся документацією 
прикладного програмного інтерфейсу (API), щоб з'ясувати це!
