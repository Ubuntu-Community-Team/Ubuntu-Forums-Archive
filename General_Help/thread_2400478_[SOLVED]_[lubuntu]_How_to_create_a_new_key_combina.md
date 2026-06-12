---
title: "[SOLVED] [lubuntu] How to create a new key combination to type a symbol"
date: 2018-09-06
forum: General Help
---

### Post by virilo on 2018-09-06
Hi,

I have a Chromebook C202SA, with an EN keyboard, and I'd like to use it as a Spanish keyboard:

[INDENT]- I have configured keyboard layout for ES

- I put stickers on the keys to match the distribution ES[/INDENT]


The problem is that the ES distribution requires using an additional key for the letter Ñ. And, due to this lack, now I don't have a key to easily enter the symbols '<' and '>' (necessaries for programing)


It would be perfect to use the following key combinations to recover these two symbols:


[INDENT]AltGr + comma: <

AltGr + dot: >[/INDENT]


How could I configure my keyboard to respond to those key combinations?

Cheers

---

### Post by TheFu on 2018-09-06
check out xdotool

---

### Post by Holger_Gehrke on 2018-09-06
@TheFu: xdotool is for automation, sending key events programmatically, but virilo wants to redefine keys. xmodmap seems like a better fit.

@virilo: use xev from a terminal to get the key codes for the keys you want to redefine. Each key generates a press and a release event, they look like this in the output:
```

KeyPress event, serial 34, synthetic NO, window 0x5200001,
    root 0x5c7, subw 0x0, time 19959644, (140,364), root:(891,827),
    state 0x10, keycode [COLOR=#ff0000]59[/COLOR] (keysym 0x2c, comma), same_screen YES,
    XLookupString gives 1 bytes: (2c) ","
    XmbLookupString gives 1 bytes: (2c) ","
    XFilterEvent returns: False

```
I've marked the place you should be looking for in red. On my keyboard comma and period are codes 59 and 60 but they might be different on yours. Close xev by closing the window it pops up to capture mouse events. Use ```
xmodmap -pke>xmodmapfile
``` to get a file with all the current key code to symbol mappings. The file lists one keycode per line in the format 'keycode xxx = symbolname1 ... symbolname8'. Open this file and remove everything but the mappings for the two keycodes you got from xev. The symbol to generate for 'altgr+key' is the fifth. Replace that symbol with 'less' on the one line and with 'greater' on the other. The file should end up similar to this (this is for my keyboard, the keycodes and the symbols except the fifth one might be different for you):
```

keycode  59 = comma semicolon comma semicolon less multiply
keycode  60 = period colon period colon greater multiply

```
save the file, exit the editor and run
```

xmodmap xmodmapfile

```
Try whether the keys works as intended. If they do, you only need to find a way to run this xmodmap command automatically at session start. I don't use LUbuntu, so I don't know how to do that on LXDE.

Holger

---

### Post by HermanAB on 2018-09-06
I prefer to use Autokey to define key presses.

---

### Post by virilo on 2018-09-12
Hi Holger_Gehrke,

I followed your steps and it was very easy to configure it.

Look that!!!  <<< >>> :D

Thank you very much!

Virilo

---

