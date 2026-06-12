---
title: "Dual boot problem - might destroy GRUB?"
date: 2007-04-06
forum: General Help
---

### Post by Onyx_47 on 2007-04-06
I can't start WinXP anymore. I get BSoD saying UNMOUNTABLE_DISK_VOLUME. I had this issue before and fixing it is easy. I have to go to recovery console and use fixboot and fixmbr.

The problem lies within second command, fixmbr. It will, if I'm right, write a new MBR. The problem is, as far as I know a part of GRUB is stored inside MBR... I'll let you  guess the probable outcome...

Offcourse, there's a slim chance everything will be fine in the end. A SLIM chance.

As I'm still pretty much a noob, could someone explain to me a procedure of recovering GRUB after eventual malfunction? Without using a floppy if possible, my floppy drive is dead. I can boot from USB disk thought.

Thanks in advance.

---

### Post by rabid9797 on 2007-04-06
doing fixmbr will indeed overwrite grub, and you will have to reinstall grub, or use a utility like supergrub, in order to get back into ubuntu.

im not exactly sure on how to recover grub, i know it can be done from a live cd, but you'll have to wait for someone with more experience to tell you that cause i just don't know

---

### Post by spankymasterc on 2007-04-06
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

this shows you how to install grub from live cd :D -::cheers::-

---

### Post by Onyx_47 on 2007-04-06
Thanks. Guess I'll be holding my fingers crossed tommorow hoping that Windows don't mess everything up...

---

### Post by spankymasterc on 2007-04-06
That is windows for you lol winblows would be a better name :D

---

