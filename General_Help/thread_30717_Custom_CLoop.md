---
title: "Custom CLoop"
date: 2005-04-29
forum: General Help
---

### Post by Teh Ethan on 2005-04-29
So I'm trying to customize the live FS (so I can fit it on my 495mb memstick), but I can't  mount the dang CLoop (copied it to my hdd first).

[SHELL]
root@ubuntu:/ # mount /hd/filesystem.cloop -o loop /loop -t /*tried EXT2/3, Reiser, VFAT, JFS, XFS, NTFS, ISO9660 for FS types*/
mount: wrong fs type, bad option, bad superblock on /dev/loop3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
root@ubuntu:/ # dmesg | tail
/*Just says I got the FS wrong*/
[/SHELL]

How do I get this to work (and if it's as easy as just putting in a different FS type that I didn't think of, what's the type)?

---

