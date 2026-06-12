---
title: "MD on top of LVM, raid not starting/mounting on boot"
date: 2017-03-22
forum: General Help
---

### Post by omega@omegacs.net on 2017-03-22
I've swapped the usual roles of mdadm and lvm2, building a RAID-5 out of volumes managed by LVM (I know what I'm doing and I have my reasons), but the array is not starting or mounting on boot.  I have my suspicions as to why this is happening, but I know nothing about the modern Linux boot sequence and thus don't know a) how lvm-on-md normally starts, or b) how to convince mdadm to scan a second time and/or autodetect after lvm starts but before filesystems are mounted.  In particular this is a pain because I have several services (plex, crashplan) that start at boot that either require files on, or themselves exist on, the raid that doesn't mount.  Manual intervention after each boot is getting old...

Can anybody give me any pointers?

Thanks!

---

