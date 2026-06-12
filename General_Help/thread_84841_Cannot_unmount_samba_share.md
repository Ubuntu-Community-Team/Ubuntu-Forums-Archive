---
title: "Cannot unmount samba share"
date: 2005-11-01
forum: General Help
---

### Post by zigford on 2005-11-01
My setup.

1 Gentoo server 192.168.0.36 with share called "common"
2 Ubuntu desktop with share mounted with the following:

mount -t smbfs //192.168.0.36/common /mnt/common

This works.  It has always worked and will always work.

The problem:
When, on the rare occasion I decide to restart my Gentoo server or the samba service, I loose connectivy (obviously) on my ubuntu desktop.

But even when I start the server back up or start samba back up on the server I get nothing on Ubuntu.  This does not phase me.  I can just unmount my share and mount it again.

WRONG

Nomatter what I do, I cannot unmount my share, I always get 
harrisj@henry:~$ sudo umount /mnt/common
umount: /mnt/common: device is busy
umount: /mnt/common: device is busy

I know for a fact that /mnt/common is not busy. I have killed everything. gnome
gdm
nautilus
blah
blah
blah

The only way I have ever gotten it to unmount without rebooting is:

sudo init 1
umount /mnt/common
init 2

Does anyone know of an easy way to unmount a dead samba share???

Please. I would be your best friend I promise.

---

### Post by cbkm on 2005-11-01
Can you not either do:
```

$ sudo umount -f /mnt/common

```

or possibly the worse option of:
```

$ sudo umount -l /mnt/common

```

Read the manpage to discover what the options do, needless to say -l isn't a particulary good solution.

---

### Post by zigford on 2005-11-01
[QUOTE=cbkm]Can you not either do:
```

$ sudo umount -f /mnt/common

```

or possibly the worse option of:
```

$ sudo umount -l /mnt/common

```

Read the manpage to discover what the options do, needless to say -l isn't a particulary good solution.[/QUOTE]

Damn you boy your goooood.

sudo umount -l

Did the trick. How did you figure that one out?

Cheers anyway.

---

### Post by Schmots on 2005-11-01
Man pages, there your friend

Smile have a nice day

---

### Post by Zxaos on 2005-11-27
Will using the lazy unmount cause any problems? The manpages say that it will clean up once it's not busy, but in this situation it *never* becomes unbusy.

---

### Post by barabara on 2006-04-21
"umount -l" is THE command.

It shouldn't be -l for lazy, but -l for "leading" or "luxurious".

Well, by the way, using SuSE 9.3 fully patched, and still having that kind of problem is really disappointing: 
developers should consider that problem a **top priority** - any automated process, or a PHP page for instance accessing such a busy (while actually not) FS would be locked for a while, then falling into a irrecoverable-hard-to-fix error. 

How come in 2006 the OS is still not able to auto-detect that the mounted FS is not answering and, thus, should automatically perform a kind of "umount -l" remount?

---

