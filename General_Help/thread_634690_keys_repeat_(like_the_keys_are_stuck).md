---
title: "keys repeat (like the keys are stuck)"
date: 2007-12-08
forum: General Help
---

### Post by 3djake on 2007-12-08
I have being using linux for about 1 year now, i will never go back to windows, 
this is the first issue i have had with any linux distro that i couldnt fix.

I have gusty gibben installed on 2 computers. On one of them the key somtimes appear to repeat and i cant stop it, the same thing sometime happens with the mouse buttons.
There is nothing wrong with the mouse or keyboard. It all worked fine on ubuntu 6.06.

Please som1 help me, i have no idea what would cause this. I have to restart my computer when this happens

---

### Post by HermanAB on 2007-12-08
The screen, keyboard and mouse are controlled by Xorg.  If the keyboard driver/hardware gets confused, then you should be able to fix it by restarting X with ctrl-alt-backspace.

Cheers,

Herman

---

### Post by bingoUV on 2007-12-08
How frequently does it happen? Does this help fix the problem? If yes, put it in ~/.xsession file. 
```

xset -r

```


This  will stop auto repeat of keys.

---

### Post by 3djake on 2007-12-08
it occurs very often, mostly when i am using firefox but not alwayz, I have tried ctrl alt backspace when the problem first started but the key (or mouse button) still repeats at the log in screen.

thanks for nnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnnn Edit - for you replies is what iwas going to say lol

i will try that command

---

### Post by bingoUV on 2007-12-08
did you try that command?

---

### Post by 3djake on 2007-12-08
I am going to try it now, as u can see the problem accured while i was posting and i just wanted to go to bed so I hit the submit button and turned off my computer. I am going to surf the net for a while and see if it happens.

---

### Post by ~LoKe on 2007-12-08
Hold the function key between control and alt, then press some key you don't use.

This magically fixes the problem for me...hell if I know what's going on.

///

See?  I set it as the forward slash on the keypad.

---

