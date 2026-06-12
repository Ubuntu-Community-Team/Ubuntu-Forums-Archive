---
title: "Ubuntu will not shutdown or start up after black screen"
date: 2013-01-27
forum: General Help
---

### Post by Ninjex on 2013-01-27
Basically anytime I try and shutdown Ubuntu by any means, it will not.

I held the escape key, while it is trying to shutdown to see that it always gets stuck at something similar to the following:
Stopping process winbid daemon winbid

Also, recently after I updated to a 3.6.2 kernel, when my laptop goes black screen, it will not come back up. I tried moving the mouse, hitting every key, and clicking with the mouse.

```
:~$ uname -a
Linux Ninjex 3.6.2-030602-generic #201210121823 SMP Fri Oct 12 22:31:22 UTC 2012 i686 athlon i386 GNU/Linux

```Any help would be very much appreciated!
If you need me to post additional information, I will follow through.

As a side note, I have recently done a apt-get purge compiz and apt-get purge unity, and re-installed both because my desktop effects from compiz have stopped working, and still are not working after the reinstall.

Thanks in advance,
- Ninjex

---

### Post by MoebusNet on 2013-01-27
As a genuine, certified non-expert, the only thing I can think of is to see if running 'fsck' from a Live-CD or Live-USB boot might correct any file system errors caused by your changes, You can run it from 'GParted' on the Live-CD/USB. You should not run 'fsck' from a mounted drive, since that can cause corruption.

---

### Post by Ninjex on 2013-01-27
I was going to test this out. I tried running init 1, so I could unmount my SDA partition to run fsck on it. However, running init 1 makes the graphics on my screen spread horizontally and becomes frozen, it is hard to explain.

I am thinking that it may be best just to re-install Ubuntu again as a dual boot, and then copy the /home/user and everything behind it to the newly installed os and afterwards, delete the other partition and free the space and add it over to the new one.

---

