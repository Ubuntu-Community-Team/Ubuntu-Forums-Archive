---
title: "mount floppy after using fdformat"
date: 2006-12-29
forum: General Help
---

### Post by moonhk on 2006-12-29
how to mount floppy after using fdformat ? 
root@hex:/# mount -t vfat /dev/fd0 /mnt/floppy
mount: wrong fs type, bad option, bad superblock on /dev/fd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@hex:/#

---

### Post by Sef on 2006-12-29
What Ubuntu version are you running?

---

### Post by moonhk on 2006-12-29
Here is my version
moonhk@hex:~$ uname -a
Linux hex 2.6.15-27-server #1 SMP Fri Dec 8 18:43:54 UTC 2006 i686 GNU/Linux
moonhk@hex:~$

---

