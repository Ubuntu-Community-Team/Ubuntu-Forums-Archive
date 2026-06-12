---
title: "Terminal, screen detachment issue"
date: 2012-10-26
forum: General Help
---

### Post by xavieranderson on 2012-10-26
I'm trying to detach a screen in terminal using CTRL A+D, however it never works. Ctrl now actually prints the "^" in the terminal.
So when I try to do CTRL A+D, it actually echos "^Ad".

This issue also happens through putty, on windows...

What am I doing wrong?

---

### Post by danielbauwens on 2012-10-26
Which Ubuntu are you using?
Also when I do ```
CTRL-A-D
``` Then it just closes the terminal.

---

### Post by xavieranderson on 2012-10-26
12.04.

Same issue happens in CentOS.

And in Putty in Windows.

---

### Post by danielbauwens on 2012-10-26
It may be it's just because you don't have the latest version, though i doubt that actually.
I use 12.10 at the moment, and for me I can type CTRL and it wont make the ^ 
I'm still not sure to what you want to do with it, but otherwise try using it by typing ```
CTRL-ALT-F1
```

---

