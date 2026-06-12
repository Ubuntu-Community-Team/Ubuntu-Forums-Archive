---
title: "How to make a shortcut for key combination eg. CTRL+C"
date: 2007-11-16
forum: General Help
---

### Post by fantan on 2007-11-16
Dear members,

I would like to know how to make a shortcut for key combination eg. CTRL+C with help of one button if its keycode is known?

Some days ago I've got a multimedia Keyboard type Chikony Multimedia Fun-Touch. It has among others three special office function buttons, which in Windows environment serve as functions CTRL+X, CTRL+C, CTRL+V that is Cut, Copy, Paste.
I can scan the scancodes and the relevant keycodes of them.

Can anybody help me how to use theese keycodes that is one touch buttons as key combinations CTRL+X, CTRL+C, CTRL+V on our Linux system, for example Gutsy? 

Thanks for advance,

fantan

---

### Post by bingoUV on 2007-11-16
figure out the keycodes by xev. Map keys using xmodmap.

---

