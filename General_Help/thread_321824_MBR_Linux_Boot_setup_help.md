---
title: "MBR Linux Boot setup help"
date: 2006-12-19
forum: General Help
---

### Post by srgess on 2006-12-19
Due to grub Error 22 i got tired of grub and want to boot linux with mbr but im not sure how to do it, if you did it with mbr can you help me i dont know what to put into the boot mbr setup, there picture of my hard drive setup.

Hard Drive setup: 
[http://img182.imageshack.us/img182/3521/partitionqx8.jpg](http://img182.imageshack.us/img182/3521/partitionqx8.jpg)

Disk 0 and 1 are IDE drive
Disk 2 is SATA Drive

There my question in this picture of boot loader text:
[http://img263.imageshack.us/img263/6506/bootpp6.jpg](http://img263.imageshack.us/img263/6506/bootpp6.jpg)

---

### Post by budgie9 on 2006-12-19
I don't know if this will work for you and others.
A friend of mine had the same sort of set up, where his main, primary drive is IDE and the second drive a SATA. He removed the connection to the SATA drive, and the install to the IDE drive went fine. Saying this, he was not using Ubuntu, but Suse 10.1.
Perhaps it may be worth trying for you, it could be the SATA drive is getting in the way, but to be honest we don't understand why it should be. He then re-installed the SATA drive and the boot worked.
As I say it may or may not work, but is it worth trying?

---

