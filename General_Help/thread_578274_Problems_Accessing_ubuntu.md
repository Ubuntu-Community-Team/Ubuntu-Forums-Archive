---
title: "Problems Accessing ubuntu"
date: 2007-10-17
forum: General Help
---

### Post by McTricks on 2007-10-17
I have Ubuntu and Windows installed. For complicated reasons, I had to re-install windows. But now, i can't load into Ubuntu. Normally, I would just re-install Ubuntu, but at the moment it there is very important info on the partition. Is there any way to access Ubuntu, or at least just access the partition?

---

### Post by arkara on 2007-10-17
you must first boot from a live cd
then get on a terminal

and type.
grub
then find /boot/grub/stage1 You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.
then type Type "root (hd?,?)". this is acording to the above line replace the ? with the numbers that your computer gives you
then type Type "setup (hd?,?)"
type "quit" and reboot your system this will do the job

---

