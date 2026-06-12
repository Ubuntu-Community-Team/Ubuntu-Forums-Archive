---
title: "[SOLVED] &amp;quot;Kernel panic - not syncing&amp;quot;"
date: 2008-01-08
forum: General Help
---

### Post by TeeAhr1 on 2008-01-08
Kubuntu 7.10.  My sister's machine, so I'm not sure if it was an update she installed or what.  I tried recovery mode, no joy.  Here's the message:

```
[   17.302871] VFS: Cannot open root device "UUID=(long string of numbers)" or unknown-block(0,0)
[   17.302926] Please append a correct "root=" boot option; here are the available partitions:
[   17.302982] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)
```

And she dies.  I booted the live CD, and when I tried to mount /dev/sda1 in Dolphin I got a message to the effect of "refused to UUID 999" or something like that (sorry, didn't write it down).  I went to the shell and did a sudo mount and that did work.  I ran fsck /dev/sda1 and it came up clean.  That's what I know, if there's any further info I can provide please ask.  Any help is greatly appreciated.

best-
pd.

---

### Post by dcstar on 2008-01-08
> **TeeAhr1 said:**
> Kubuntu 7.10.  My sister's machine, so I'm not sure if it was an update she installed or what.  I tried recovery mode, no joy.  Here's the message:

```
[   17.302871] VFS: Cannot open root device "UUID=(long string of numbers)" or unknown-block(0,0)
[   17.302926] Please append a correct "root=" boot option; here are the available partitions:
[   17.302982] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)
```

And she dies.  I booted the live CD, and when I tried to mount /dev/sda1 in Dolphin I got a message to the effect of "refused to UUID 999" or something like that (sorry, didn't write it down).  I went to the shell and did a sudo mount and that did work.  I ran fsck /dev/sda1 and it came up clean.  That's what I know, if there's any further info I can provide please ask.  Any help is greatly appreciated.

best-
pd.

Something has probably changed the UUID of the boot partition, using the Live CD mount the partition and edit the /boot/grub/menu.lst file to use /dev/sda1 instead of the UUID.

---

### Post by TeeAhr1 on 2008-01-08
As in, "kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sda1"?  Same message, except now the first line is "VFS: Cannot open root device "sda1" or unknown-block(0,0)".  Is my syntax wrong?

EDIT: I checked in /dev/disk/by-uuid/ and the uuid matches the grub entry.

---

### Post by TeeAhr1 on 2008-01-09
*bump*

---

### Post by artinla on 2008-01-09
boot off the livecd, open the terminal and type:

e2fsck -fp /dev/sda1 (or whatever drive is not working properly)

It could be just an inconsistent filesystem.  Happens to me sometimes.

---

### Post by TeeAhr1 on 2008-01-09
SOLVED.  chrooted into the file system and rebuilt initramfs.  See this post: [http://ubuntuforums.org/showpost.php?p=1711279&postcount=2](http://ubuntuforums.org/showpost.php?p=1711279&postcount=2)

---

