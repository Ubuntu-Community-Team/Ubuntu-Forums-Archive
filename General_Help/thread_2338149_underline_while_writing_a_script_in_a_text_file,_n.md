---
title: "underline while writing a script in a text file, not by the terminal (nano,vi exc..)"
date: 2016-09-25
forum: General Help
---

### Post by albert1905 on 2016-09-25
hey guys im writhing a script using the simple text editor in ubuntu, im trying to so some underlines, but nothing seems to work
the things i tried

1.${underline}text${normal}

2.[COLOR=#303336][FONT=Consolas]echo [/FONT][/COLOR][COLOR=#303336][FONT=Consolas]-[/FONT][/COLOR][COLOR=#303336][FONT=Consolas]e [/FONT][/COLOR][COLOR=#7D2727][FONT=Consolas]"\e[4munderline\e[0m" 
[/FONT][/COLOR]
someone has an idea how it's done?
what am i missing?
thx!

---

### Post by sudodus on 2016-09-25
If you want the underline to show in a command line window or in a text screen, maybe you can use ANSI escape sequences:

[wiki/ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)

Try according to this example:

```
echo -e "before \0033[4munderline\0033[0m after"
```

---

### Post by albert1905 on 2016-09-25
it worked, thx man!!!

---

### Post by sudodus on 2016-09-25
You are welcome :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

