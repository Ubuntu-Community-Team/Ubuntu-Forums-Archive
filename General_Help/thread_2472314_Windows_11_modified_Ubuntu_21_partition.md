---
title: "Windows 11 modified Ubuntu 21 partition"
date: 2022-02-23
forum: General Help
---

### Post by correoparaangel on 2022-02-23
Hello, first of all I want to greet the members of this forum with a big hug, since I am new, or almost, since I had a registered user, but I don't remember when.
I have Ubuntu for quite some time, having been through different linux distributions.
In my CPU I updated in the Windows partition from 10 to 11, having had Ubuntu 21 in another partition of the same disk, the issue is that at the beginning windows left the ubuntu partition as "not allocated" or "does not exist", I tried different programs to try to recover the partition table like rescatux, testdisk from Ubuntu live and the like from windows, the closest to repair was testdisk, which left the EXT4 partition labeled linux, but I couldn't go any further, rescued the data to an external hard disk, so everything is there, although it seems to have disappeared just like GRUB, I don't know what to try before reinstalling everything again.
If anyone has any idea how to modify those bytes to even show the linux partition, grub would be easy to create, I attach two images and send a hug again.


Angel

---

### Post by Impavidus on 2022-02-24
I see you have an msdos (aka mbr) partition table, not the modern gpt. It's a known bug in Windows 8 and higher that it can destroy Linux partitions on MBR partitioned hard drives during Windows installation. I've never used testdisk, but usually it can recover the entire partition in these cases, provided it wasn't overwritten. If you can't, photorec may be able to recover files, but it will also find old versions and won't recover filenames, so it will be a lot of work to sort it out.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

