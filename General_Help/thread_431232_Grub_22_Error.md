---
title: "Grub 22 Error"
date: 2007-05-02
forum: General Help
---

### Post by nerdman978 on 2007-05-02
I just deleted my Ubuntu linux partition on my laptop. Don't worry, I plan to use it on a virtual machine on Windows so I can still toy around with Ubuntu. Upon deleting the partition, I shut down my computer and restarted. After the Dell "LOADING" screen I always get it tried to load the grub bootloader and failed or something. And now all I get is the error message. So I write to you now from the Knoppix Live CD (it was all I could think of). Also, I used a Live CD's installer to delete the partition because thats the only way I know how to get to a partitioner. Please help.

---

### Post by confused57 on 2007-05-02
> **nerdman978 said:**
> I just deleted my Ubuntu linux partition on my laptop. Don't worry, I plan to use it on a virtual machine on Windows so I can still toy around with Ubuntu. Upon deleting the partition, I shut down my computer and restarted. After the Dell "LOADING" screen I always get it tried to load the grub bootloader and failed or something. And now all I get is the error message. So I write to you now from the Knoppix Live CD (it was all I could think of). Also, I used a Live CD's installer to delete the partition because thats the only way I know how to get to a partitioner. Please help.
You need to restore the Window's IPL code to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you have access to another pc, you could burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If you don't have access to another pc, you could always reinstall Ubuntu, download & burn a copy of the SGD, which can restore your Window's mbr.

---

