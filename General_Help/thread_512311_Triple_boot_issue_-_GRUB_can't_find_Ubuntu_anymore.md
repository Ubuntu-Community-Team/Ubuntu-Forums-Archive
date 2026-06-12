---
title: "Triple boot issue - GRUB can't find Ubuntu anymore"
date: 2007-07-29
forum: General Help
---

### Post by spacepirates on 2007-07-29
I just installed LinuxMint, and during the installation formatted my /boot ext3 partition. I have my harddrive partitioned into two XFS partitions (Ubuntu and LinuxMint), a NTFS (Windows XP), SWAP, and an ext3 (/boot).

GRUB doesn't see Ubuntu anymore, and i don't know how to configure it. I've searched the forums, but I can't find out how (there are just too many topics to sift through...).

Can someone please point me in the right direction, or tell me how to configure GRUB to see Ubuntu?

I don't think i can directly access my /boot partition from LinuxMint (what i am running now). I can see LinuxMint's GRUB boot entry, but not ubuntu's.

Thanks!

---

### Post by Elegorod on 2007-07-29
Grub boot entries are stored in file /boot/grub/menu.lst
I have such boot entry for Ubuntu:
```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=09d99998-8464-4de5-96db-d1d5d82e0691 ro quiet splash locale=ru_RU
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

```
You can add this to the end of the file, but make some changes:
(hd0,5) - set partition number
root=/dev/hda6 - set partition number also
locale=ru_RU - your locale
/boot/vmlinuz-2.6.20-16-generic and /boot/initrd.img-2.6.20-16-generic - path to such files

---

### Post by spacepirates on 2007-07-29
I've been trying to configure GRUB to find Ubuntu, but it still can't. I reinstalled GRUB through the command line but that didn't change anything.

is there a way to install GRUB to the /boot partition and have it automatically find the OSs, like in an Ubuntu install?

---

### Post by dabl on 2007-07-29
Two suggestions:

1. Remember the rule "Last Linux Wins" -- the /boot/grub/menu.lst file installed by the last Linux you installed (in its own filesystem) is the one that is functional for booting.

2. Here's some tools: [http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

:)

---

