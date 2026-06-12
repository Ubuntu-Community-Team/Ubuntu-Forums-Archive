---
title: "Cant get irssi working in Edgy :("
date: 2006-10-30
forum: General Help
---

### Post by Buffi on 2006-10-30
Alt + number does not work for me in Edgy, that is it does not produce the input that changes tabs in irssi and so on. Instead chars like ²³´µ¶·¸¹ are outputted. Im using swedish locales so swedish special characters also need to work.

$ echo $TERM $SHELL $LANG
xterm /bin/bash sv_SE.UTF-8

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "se"
EndSection

Worked fine in Dapper :(

---

