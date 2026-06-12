---
title: "[SOLVED] Black screen"
date: 2008-02-21
forum: General Help
---

### Post by Arkas on 2008-02-21
First may I explain what i have done.

I installed Ubuntu server thinking it was what i needed, after realising with some help, I actually needed Ubuntu desktop.

So now when i install Ubuntu desktop it goes fine right up untill it say remove cd disk, then boots and goes blank.( i do get the Ubuntu logo screen )

I have tried to start in Safe mode and when it boots up I only see the desktop but its frozen.

So then i hit ESC before it loads and put in the command ( dpkg-reconfigure -phigh xserver-xorg ).
It tells me i dont have xserver -xorg.

I dont  know how to  re install !

I seem to think it may be the video card ( old PCI card) drivers or in conflick with Ubuntu server.
How do I get rid of Ubuntu server?

Please help
______________

---

### Post by Crafty Kisses on 2008-02-21
> **Arkas said:**
> First may I explain what i have done.

I installed Ubuntu server thinking it was what i needed, after realising with some help, I actually needed Ubuntu desktop.

So now when i install Ubuntu desktop it goes fine right up untill it say remove cd disk, then boots and goes blank.( i do get the Ubuntu logo screen )

I have tried to start in Safe mode and when it boots up I only see the desktop but its frozen.

So then i hit ESC before it loads and put in the command ( dpkg-reconfigure -phigh xserver-xorg ).
It tells me i dont have xserver -xorg.

I dont  know how to  re install !

I seem to think it may be the video card ( old PCI card) drivers or in conflick with Ubuntu server.
How do I get rid of Ubuntu server?

Please help
______________


Hmmm, when it's booting up, you might want to try to boot into verbose mode, you can do that by doing the following:
```
Ctrl+Alt+F2
``` From there you can see if there is any errors going on.

---

### Post by GuDoN on 2008-02-21
Are you running any graphics card mate?

Could you give me the model and make please?

---

### Post by Arkas on 2008-02-21
Thankyou very much for your assistance, i have decided to wipe the hdd clean and start again.

---

