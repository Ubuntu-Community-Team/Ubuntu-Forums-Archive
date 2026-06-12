---
title: "No console after logging out from KDE"
date: 2006-11-13
forum: General Help
---

### Post by jonnybecker on 2006-11-13
Hi,

my OS: Edgy

I'm having a strange problem. I just installed Edgy and now I'm having a strange problem. There is no console after logging out from the console on KDE using this command: sudo /etc/init.d/kdm stop. All I see is also a black screen
Console-login also isn't possible. All I see here is also a black screen and after a while it switches back to the graphical login screen.

What is wrong? 

Cheers
Jonny

---

### Post by harty83 on 2006-11-13
Try pressing ctrl-f1 or ctrl-f2 and see if that will give you a login prompt.  Then sudo /etc/init.d/kdm start

edit: Oops I meant ctrl-alt-f1 or f2

---

### Post by taurus on 2006-11-13
```
<Ctrl><Alt>F2
```

---

### Post by jonnybecker on 2006-11-14
Thank you for your help. Works like a charm. :-D 

Jonny

---

