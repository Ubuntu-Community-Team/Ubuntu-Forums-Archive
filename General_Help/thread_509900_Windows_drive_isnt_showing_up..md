---
title: "Windows drive isnt showing up."
date: 2007-07-26
forum: General Help
---

### Post by Albertahawk on 2007-07-26
Hmmm, I had an extra (empty) NTFS hard drive on my computer that I wasnt using so i decided to install windows to it to dual boot, but it seems that nither GRUB nor Ubuntu picks up on the drive now.

Ubuntu HD: 40Gb Master
Windows XP: 10Gb Slave

It was seeing it before I installed windows, so, what do I have to do to make it show up?

---

### Post by HermanAB on 2007-07-26
Hmm, run 'mount' or 'df' to see what you have, then look at 'ls /dev' to see what else is picked up.  Then mount whatever isn't mounted manually - assuming it is sdb:
$ sudo mkdir /mnt/windoze
$ sudo mount -t ntfs /dev/sdb /mnt/windoze

For more info see 'man mount' and 'man fstab'.

Cheers,

Herman

---

### Post by Albertahawk on 2007-07-26
Did that, its mounted, although I cant unmount it, even from root.

NTFS config isnt showing "internal devices" as an option, only external now. It needs to be unmounted to show internal, I do believe.

---

