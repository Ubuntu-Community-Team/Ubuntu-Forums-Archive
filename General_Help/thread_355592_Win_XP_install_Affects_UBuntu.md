---
title: "Win XP install Affects UBuntu ?"
date: 2007-02-07
forum: General Help
---

### Post by tworthenn on 2007-02-07
I had a dual boot Win 2K and Ubuntu system. I installed Win XP over the Win 2K and ubuntu will no longer boot up from the hard drive or even from a veriifed CD-ROM.
Symptoms:
First part of ubuntu boot process goes so far,  then the screen goes black and the hard drive is doing something. Similar symptoms with the CD verson. I even got as far as the ubuntu desktop..once.
Win XP boots and runs fine.
System is over two years old. Any ideas ?
Thanks in advance
Tom Worthen
San Diego

---

### Post by toGoq on 2007-02-07
You need to reinstall GRUB, 'cause the XP-install has overwritten it.
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by tworthenn on 2007-02-07
Thanks any way but Grub works fine. When I boot from a UBUNTU CD the same thing happens: gets about half way thru then goes dark.

---

### Post by toGoq on 2007-02-08
As far as I know: if you install windows after Ubuntu or other Linux, windows would mess up your Master Boot Record. Hence the Grub restore.
What about reinstalling Ubuntu using the alternate CD? I had some problems too (and so other people) with the Live CD.
If you have some data you need to back-up (before reinstalling Ubuntu), maybe you might like to use Knoppix to do it. You can also create a separate partition for your /home -if you didn't do that in the first place. In the future when something may go wrong and you need to reinstall Ubuntu again, then you can keep your old /home and no data will be lost.
Good luck, anyway.

---

