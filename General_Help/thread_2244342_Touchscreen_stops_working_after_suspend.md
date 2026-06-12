---
title: "Touchscreen stops working after suspend?"
date: 2014-09-15
forum: General Help
---

### Post by alex258 on 2014-09-15
I have an acer aspire v7 ultrabook and ubuntu 14 works great out of the box. The only problem is the touch screen stops working after the lid is closed(suspended) and resumed. only seems to resume working after a restart.
Does anyone have any suggestions?

---

### Post by alex258 on 2014-09-18
Still need help...Seems randoms as to if the touchscreen will work.

---

### Post by shinto-cc on 2015-04-29
I have a similar problem on my Asus X202E with its Atmel maXTouch Digitizer, running Ubuntu 14.04.  The touchscreen will often (but not always) stop working after resuming from suspend.  What I do to resolve this on a case-by-case basis is to run:

```
sudo /sbin/rmmod hid_multitouch ; sudo /sbin/modprobe hid_multitouch
```

YMMV (Your Module May Vary).

Personally, I gave my user passwordless [FONT=courier new]sudo[/FONT] to [FONT=courier new]/sbin/rmmod[/FONT] and /sbin/[FONT=courier new]modprobe[/FONT], wrapped the rmmod/modprobe commands in a script with a few other things that don't survive suspend intact (like mapping the useless Asus "VIVO key" on the keyboard to function as a mouse button middle-click), and launch that with a keyboard shortcut sequence when I resume from suspend.  It sounds a little convoluted, but has worked for me every time.

I hope this helps.

---

