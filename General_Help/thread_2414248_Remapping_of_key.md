---
title: "Remapping of key"
date: 2019-03-07
forum: General Help
---

### Post by valravn on 2019-03-07
Hi,
I have a question about remapping a key on a macbook pro mid 2012 the layout is Azerty Belgian.
The key with the red circle around it is an @ and # key on my keyboard but when i press it it gives me ² and ³ is there any way to change this?
I run Ubuntu 18.04LTS on this mac.
[IMG]http://i65.tinypic.com/2hxoi2r.jpg[/IMG]

Grtz

---

### Post by HermanAB on 2019-03-08
The keyboard is managed by Xorg.

Read up on xdev and xmodmap.

---

### Post by Holger_Gehrke on 2019-03-08
@HermanAB: I think you meant xev, didn't you ?

@valravn: Start xev from a terminal. It will pop up a small window and produce lots of output in the terminal. Hit the key you want to remap. This should produce some more output in the terminal, looking somewhat like this:
```
KeyPress event, serial 34, synthetic NO, window 0x4a00001,
    root 0x6c4, subw 0x0, time 943652884, (-366,-396), root:(505,79),
    state 0x10, **keycode 49** (keysym 0xfe52, dead_circumflex), same_screen YES,
    XLookupString gives 1 bytes: (5e) "^"
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: True

KeyRelease event, serial 37, synthetic NO, window 0x4a00001,
    root 0x6c4, subw 0x0, time 943652999, (-366,-396), root:(505,79),
    state 0x10, **keycode 49** (keysym 0xfe52, dead_circumflex), same_screen YES,
    XLookupString gives 1 bytes: (5e) "^"
    XFilterEvent returns: False

```
(That's what I get if I press the key in that position, it will be slightly different on your machine)
The interesting bit is the keycode (in bold). End xev by closing the window it opened. Now run xmodmap to redefine the symbols assigned to the keycode:
```
xmodmap -e "keycode **keycode**=0x0040 0x0023"
``` replace **keycode **with the code you got from xev. The 0x0040 and 0x0023 are unicode for "@" and "#". "@" is assigned to the key and "#" is assigned to the key with shift. Switch the order of those values if that's the wrong way around. You should now get the symbols you want when pressing the key.

This remapping is **not** persistent - meaning it won't survive a log out. [This page]("https://help.ubuntu.com/lts/ubuntu-help/startup-applications.html.en") in the documentation describes how to set up programs to run at start-up on mainline Ubuntu. It's slightly different in other desktop environments but AFAIK it's possible in all of them.

Holger

---

### Post by valravn on 2019-03-08
[COLOR=#000000]@holger_Gehrke 

Thanks for the help it worked

GRTZ[/COLOR]

---

