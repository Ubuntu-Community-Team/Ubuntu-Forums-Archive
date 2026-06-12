---
title: "How to open a gui program from a text tty???"
date: 2007-06-28
forum: General Help
---

### Post by gcsoares on 2007-06-28
Hi, this days ago I had a problem and acidentally killed my xfdesktop and some more programs, the result is that I didn't have any menu or comand line in the tty7 to open a new program...           I tryed to open xfdesktop from tty1 and it says "cannot open display"...     

How can I use a command in one tty and open the program in another one???          same usar logged in both...

---

### Post by Rui Pais on 2007-06-28
hi,
as far as i know you can't.

But the situation you describe is usually solved by enter on a tty1->6:
```
sudo /etc/init.d/gdm restart
```

that kill anything related to X server and restart a new one.

---

