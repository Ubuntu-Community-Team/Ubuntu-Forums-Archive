---
title: "Desktop suddendly broken. (Login screen won't show up)"
date: 2017-08-06
forum: General Help
---

### Post by buddyx on 2017-08-06
As i started my Kubuntu this morning it felt to a black screen right after showing up the boot screen.

I went to another Screen (?) (with Ctrl+Alt+F1) and executed startx which lead me to a black screen where one dolphin window was opened.
No background, no icons - nothing. I run any command which usually fixed all those massive problems with KDE Plasma on Kubuntu (plasmashell, kwin, ...) but this time its not fixable for me.

Maybe someone can help me.

uname -a
[FONT=monospace][COLOR=#000000]Linux Buddy 4.4.0-89-generic #112-Ubuntu SMP Mon Jul 31 19:38:41 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

[/COLOR]lsb_release -a[/FONT][FONT=monospace]
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial

[/FONT][FONT=monospace][COLOR=#000000]plasmashell --version
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]plasmashell 5.5.5


Greetings
[/COLOR][/FONT][FONT=monospace]
[/FONT]

---

### Post by buddyx on 2017-08-06
Okey it was the grapic card driver...

---

