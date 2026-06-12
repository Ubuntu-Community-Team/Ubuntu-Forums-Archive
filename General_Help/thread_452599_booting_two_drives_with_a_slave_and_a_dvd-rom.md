---
title: "booting two drives with a slave and a dvd-rom?"
date: 2007-05-23
forum: General Help
---

### Post by mr32123 on 2007-05-23
I recently got into Ubuntu, I'm not an expert but the beginner's forum didnt seem the right place to post this.

Is there a way I can set up my computer (the interface is IDE) so that I can have my Windows HD and the Storage HD as a master and slave and then hook up my Ubuntu HD as a master or slave on the same cable as my DVD drive?

---

### Post by vtel57 on 2007-05-23
Sure. Why not? You should have two IDE busses... IDE0 and IDE1. Place your Windows drive on IDE0 as master and Storage drive on IDE0 as slave. Place your Ubuntu drive on IDE1 as master and CDROM on IDE1 as slave. You must (I'm sure you know this) manipulate the jumpers on the backs of the hardware to achieve this set up. When you're done, you'll have:

hda1 - Windows

hda2 - Storage

hdb1 - Ubuntu

hdb2 - CDROM

Your entries in GRUB should look like this:

Windows (hd0,0)

Ubuntu (hd1,0)

Luck!

---

