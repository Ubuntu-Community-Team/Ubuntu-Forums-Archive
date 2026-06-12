---
title: "How to use a second keyboard for shortcuts"
date: 2022-03-26
forum: General Help
---

### Post by demonenero84 on 2022-03-26
I really like keyboard shortcuts for programs :o. I was wondering If is it possible to use a second keyboard just for shortcuts.
To make a practical example super key + e opens your file manager, I would like to use my second keyboard and simply use e to open my file manager, so I could use my primary keyboard for typing and my secondary keyboard for shortcuts
Thanks a lot in advance

---

### Post by HermanAB on 2022-03-26
Just plug the second keyboard in and see what happens.  When using Xorg there are commands like 'xinput create-master Second' and 'xinput reattach ' and ‘xmodmap’. Google these for some clues.

---

### Post by demonenero84 on 2022-03-26
Thanks a lot for the reply :P Before posting here I googled "xinput" I shall google what you suggested me, I tried plugging a second keyboard and it works fine, I did a few test with xev command both keyboards work normally.

---

### Post by HermanAB on 2022-03-27
I’ve never given it any thought before, but laptop machines are commonly used with second screens keyboards and mice and they all live happily ever after. &#128514;

---

### Post by demonenero84 on 2022-03-27
So I tried xkbcomp
[https://www.lempjs.com/remapchange-your-secondaryusb-keyboard-keys/](https://www.lempjs.com/remapchange-your-secondaryusb-keyboard-keys/)
but I get this error when I load my .xkb file, I cannot change any keys :(
> 
[FONT=monospace][COLOR=#000000]Warning:          No symbols defined for <AB11> (keycode 97) [/COLOR]
Warning:          No symbols defined for <JPCM> (keycode 103) 
Warning:          No symbols defined for <I120> (keycode 120) 
Warning:          No symbols defined for <AE13> (keycode 132) 
Warning:          No symbols defined for <I149> (keycode 149) 
Warning:          No symbols defined for <I154> (keycode 154) 
Warning:          No symbols defined for <I168> (keycode 168) 
Warning:          No symbols defined for <I178> (keycode 178) 
Warning:          No symbols defined for <I183> (keycode 183) 
Warning:          No symbols defined for <I184> (keycode 184) 
Warning:          No symbols defined for <FK19> (keycode 197) 
Warning:          No symbols defined for <FK24> (keycode 202) 
Warning:          No symbols defined for <I217> (keycode 217) 
Warning:          No symbols defined for <I219> (keycode 219) 
Warning:          No symbols defined for <I222> (keycode 222) 
Warning:          No symbols defined for <I230> (keycode 230) 
Warning:          No symbols defined for <I247> (keycode 247) 
Warning:          No symbols defined for <I248> (keycode 248) 
Warning:          No symbols defined for <I249> (keycode 249) 
Warning:          No symbols defined for <I250> (keycode 250) 
Warning:          No symbols defined for <I252> (keycode 252) 
Warning:          No symbols defined for <I253> (keycode 253)
[/FONT]
thanks in advance
EDIT:
Actually it works, I forgot to add "$DISPLAY" at the end of the command to load .xkb file, so the only part that I miss is how to bind a key to multiple key presses ( like binding "e" for my second keyboard to be "e" and "super" at the same time

---

### Post by HermanAB on 2022-03-28
BTW, I used *autokey* in the past to make keyboard macros.  It worked well.

---

### Post by dragonfly41 on 2022-03-28
Struck me as odd to use a second keyboard.
There are a number of UI emulation tools around.
One is .. xdotool .. at command line.
Then there are tools such as Albert, Actiona, AutoHotKey.
Then Python.
Then for complex automation a combination of these.

---

### Post by demonenero84 on 2022-03-28
I use autokey and it does its job very well I will take a look at the others you suggested me
thanks
> **HermanAB said:**
> BTW, I used *autokey* in the past to make keyboard macros.  It worked well.

the only problem that I have is that autokey  does not recognize inputs from my remapped keyboard ( if I rebind q to  &#937; it still considers it a q)

---

### Post by vanadium on 2022-03-29
> **dragonfly41 said:**
> Struck me as odd to use a second keyboard.

To me, it doesn't. It would make perfect sense to have some extra keyboard programmed such that a single keystroke launches applications or macros.

Linux obviously can work with multiple keyboards. Each keyboard can be assigned a different layout. So at that level, it would be possible to change for example "E" on the second keyboard to become say "1" or another character. What will not be possible - afaik - is what you ask: have the "E" on your second keyboard issue a Super+E. A key can only issue a keycode. Super+E is a combination of keystrokes.

With tools like autokey or xdotool, you can have E issue a Super+E instead. However, that will cause any input of E, both from your first or second keyboard, to issue a Super+E.

Hypothetically, you may be able to reprogram the keys on the second keyboard to foreign characters. For example, you could make e issue dead_acute (é) instead. Then, you could use xdotool to issue Super+E when dead_acute is received - that happens when you press e on the second keyboard.

That would, however, disable the use of accented characters. Still, foreign characters then still may be input using the Linux Compose key system.

So, unfortunately, what you are looking for  may remotely be possible, but it is far from obvious.

What will likely not be possible is to make for example the E on the second keyboard do something else

---

### Post by demonenero84 on 2022-03-29
I think that I have all the necessary info to setup what I wanted ( I am going to use xkbcomp to load a different key layout on my second keyboard)
thanks to everyone for your help and suggestions

---

