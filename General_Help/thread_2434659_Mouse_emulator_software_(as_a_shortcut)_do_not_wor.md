---
title: "Mouse emulator software (as a shortcut) do not work in sub_menus"
date: 2020-01-09
forum: General Help
---

### Post by simba4 on 2020-01-09
My computer is a desktop, i7 with 32GB RAM and Ubuntu 16.04LTS.

Recently, my mouse's buttons started to stutter and I decided that until I'll find a suitable replacement, I would also use the keyboard to replace the stuttering buttons.

I found two programs : xte and xdotool.
For each program I set shortcuts..

    ..it works, but ..

In both programs, it doesn't work in all situations. Especially in sub menus. In those of Ubuntu itself and also in the sub_menus of FireFox and all kinds of other specific softwares.

I would like to know if there is a way to force one of these programs to work also in the sub-menus in the same way the physical mouse buttons work.

Tips and information will be appreciated,

Thanks

James

---

### Post by Holger_Gehrke on 2020-01-09
If you're using X and not Wayland, then mouse-emulation via the numeric keypad is built into X but deactivated. To switch it on you can use 'setxkbmap -option keypad:pointerkeys' in a terminal. Use shift+NumLock to activate (might have to use ctrl-shift-NumLock on some keyboards). The directions on the numerical pad move the mouse cursor. '/', '*' and '-' on the pad select right, middle and left button, '5' clicks, 'Insert' holds- and 'Del' releases the button.

Holger

---

