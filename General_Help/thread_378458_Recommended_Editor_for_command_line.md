---
title: "Recommended Editor for command line"
date: 2007-03-07
forum: General Help
---

### Post by jonnymccullagh on 2007-03-07
Hi,
I made a mess of my /etc/fstab file and I cannot log in to KDE or Gnome (as I kind of redirected my home folder).
Anyway, I need to undo the damage and have tried logging in to Ubuntu (Recovery Mode) however I need a recommendation for editing this file. I have heard of vi, pico, nano but do not know which to use - or how to use them.
Can someone recommend one? and a few starter commands (e.g. moving around the file, save, quit, edit).
Thanks in advance,
jonny

---

### Post by taurus on 2007-03-07
From the recovery mode, do

```
nano -Bw /etc/fstab
```
Use the arrow keys to move around.

To save and exit, try <Ctrl>o then <Ctrl>x.

---

### Post by jonnymccullagh on 2007-03-07
Perfect - nano is very easy to use!
thankyou

---

