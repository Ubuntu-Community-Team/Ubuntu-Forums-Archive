---
title: "Grub loader, Ubuntu &amp; M$ Windiz XP"
date: 2006-07-06
forum: General Help
---

### Post by MikeTaylor on 2006-07-06
OK, i have an old PC, with a bios that only likes hard drives <32gb. Thankfully, Ubuntu is friendly, and sees these drives for what they really are. So i have 5gb NTFS at the beggining of my HD, then a 6GB root file system, then 27gb ext2 /home and finally a 2gb swap. My plan was to share the ext2 filesystem between the operating systems.
I installed windows XP (ye, i know, but i have a weird printer...)
I partitioned etc and installed ubuntu
grub boots fine, ubuntu boots fine, but windows doesn't. I get an error, then a 0x00000007B error, after i see the windows logo, and then the blue screen lol typical. I know this is to do with the boot bit, but i am rather a noob with grub. Any help would be appreciated.
By the way, windows worked fine before i installed grub. I tryed repartitioning the disks, and installing most of the base system, then rebooting, and windows was ok. I assume that when i reinstall windows, i will loose my Grub? Also, the windows installer only sees a 32gb hard drive...
MiKe

---

