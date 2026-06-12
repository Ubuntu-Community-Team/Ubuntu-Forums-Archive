---
title: "Kubuntu: Prompting for password when mounting encrypted USB"
date: 2007-05-30
forum: General Help
---

### Post by shomati_sen on 2007-05-30
Hi,

I was using Ubuntu till last weekend when I finally switched to making KDE my desktop and installed kubuntu-desktop. Everything is much better now except for one thing. When I mounted an encrypted (done using luks and cryptsetup) USB drive, I'd be prompted automatically for a password on the encrypted drives. Now, nothing happens and I have to manually do cryptsetup to provide the password. 

Is there a way for me to get the Gnome behavior under KDE ?

Thanks,

Shomati

---

### Post by AlterEgo on 2008-03-30
In Hardy (and in KDE4), you do get prompted for a password, just like in Gnome.
However, this functionality does not work properly (in my hands at least).

As a workaround, I used this (in German, but quite understandable if you just look at the code):
[http://www.ubuntu-forum.de/artikel/25850/Automount-luks-udev.html](http://www.ubuntu-forum.de/artikel/25850/Automount-luks-udev.html)

---

