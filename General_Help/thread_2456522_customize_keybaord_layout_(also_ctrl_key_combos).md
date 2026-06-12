---
title: "customize keybaord layout (also ctrl key combos)"
date: 2021-01-13
forum: General Help
---

### Post by crpz41 on 2021-01-13
I already know I can go to ```
 /usr/share/X11/xkb/symbols
``` for remapping keyboard. 
How can I create CTRL+key combinations.... for example CTRL+n = ñ

I would prefer if there is a way staying inside the layout file so if I reinstall the OS I don't need to modify multiples system files, but if there is 
no way to do that inside the layout file... it's ok


thanks

---

### Post by robert99999 on 2021-01-14
Have you looked at using the ~/.XCompose file to do this?
I used this to add the ability to enter Greek characters from the keyboard.
Useful info here:
[https://askubuntu.com/questions/787113/compose-dead-greek-with-compose-key](https://askubuntu.com/questions/787113/compose-dead-greek-with-compose-key)
[https://wiki.debian.org/XCompose](https://wiki.debian.org/XCompose)

---

### Post by Holger_Gehrke on 2021-01-14
If I were you I'd leave the system files alone because you'd have to redo your modifications whenever an update to the system files happens. There is a command to remap keys called xmodmap (this is for X11, I don't know how to do it on Wayland). See 'man xmodmap' for details. Please note that 'ctrl-whatever' produces control-characters which are used by many programs as shortcuts. 'ctrl-n' is for examples used in a lot of programs as 'New File' and in emacs as 'next-line' (basically 'cursor down', it's an alternate key meant for keyboards that don't have cursor control keys). So I'd probably map the character you want to AltGr-n (and the capital variant to Shift-AltGr-n).

Holger

---

### Post by crpz41 on 2021-01-14
my intention is to get **Ö** through **CTRL+[  **
in some rows you can see:
```

<dead_diaeresis> <O>                 : "Ö"   Odiaeresis # LATIN CAPITAL LETTER O WITH DIAERESIS
<Multi_key> <quotedbl> <O>           : "Ö"   Odiaeresis # LATIN CAPITAL LETTER O WITH DIAERESIS
<Multi_key> <O> <quotedbl>         : "Ö"   Odiaeresis # LATIN CAPITAL LETTER O WITH DIAERESIS
<Multi_key> <diaeresis> <O>         : "Ö"   Odiaeresis # LATIN CAPITAL LETTER O WITH DIAERESIS
<Multi_key> <O> <diaeresis>         : "Ö"   Odiaeresis # LATIN CAPITAL LETTER O WITH DIAERESIS
```

which should I modify and how?  
once I modified the file I can reboot and everything works right?

---

