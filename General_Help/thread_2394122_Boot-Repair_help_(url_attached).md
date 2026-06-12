---
title: "Boot-Repair help (url attached)"
date: 2018-06-12
forum: General Help
---

### Post by pk2peter on 2018-06-12
Hi all,

I had my ubuntu installed in a separate HDD.
Now I delete my Linux partition in Windows 10. (bad mistake)

Tried a lot of things to repair grub, and windows repair (changing my Bios to UEIT(?) mode)

In short, I got a url from boot-repair which is:

[http://paste.ubuntu.com/p/SfxxG7RyYX/](http://paste.ubuntu.com/p/SfxxG7RyYX/)

Could you guys please help with me on this? or should I take my comp to a professional?

---

### Post by dragonfly41 on 2018-06-12
Don't despair. You have some options to try.

If you have a Ubuntu LiveUSB you can use that (in **Try** mode .. _definitely not_ Install mode) to run and try Ubuntu gparted to recover the ext4 Ubuntu partition deleted from Windows.   If you do not use **Try** mode you may overwrite your deleted partition. You are warned.

Or

If you only have Windows, install testdisk in Windows 10 and run that try to look for the deleted Ubuntu partition.

But you need to read up on testdisk site about recovering deleted Linux partition.

If you do your research on recovery there should be no need take your computer to a recovery shop.

Another option I have tried from within Windows is to install R-Linux on Windows .. [https://www.r-studio.com/free-linux-recovery/](https://www.r-studio.com/free-linux-recovery/)

---

