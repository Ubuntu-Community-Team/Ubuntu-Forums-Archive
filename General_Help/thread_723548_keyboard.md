---
title: "keyboard"
date: 2008-03-13
forum: General Help
---

### Post by joe0301 on 2008-03-13
the keys on my keyboard need to b pressed a number of times before they react,.anyone able to help....

---

### Post by sumguy231 on 2008-03-13
This may sound too obvious, but have you tried a different keyboard? It could be a hardware problem.

---

### Post by erginemr on 2008-03-13
Also check and play with your keyboard  settings in; 
Main Menu -> Preferences -> Keyboard.

---

### Post by unutbu on 2008-03-13
Open up a Terminal window by going to the upper gnome panel and clicking on Applications>Accessories>Terminal.

In the terminal window type 
```

xev

```

A square window will pop up. Inside that window, type a key. You should get 
stuff that looks like this

```

KeyRelease event, serial 34, synthetic NO, window 0x3000001,
    root 0x13a, subw 0x0, time 2854895227, (131,69), root:(137,598),
    state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False

```

everytime you press a key. If you are still not seeing anything, then perhaps your hardware is failing.

To quit, go back to the terminal window and type Ctrl-C.

If in the xev window you are seeing responses to each key press, then perhaps your key repeat rate is set to slow. In which case:

Go to the upper left-hand corner of your screen. On the gnome panel, click System>Preferences>Keyboard. There you will find slider bars to control two slider bars:
Delay and Speed.

---

