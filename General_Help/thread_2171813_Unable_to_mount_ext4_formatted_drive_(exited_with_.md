---
title: "Unable to mount ext4 formatted drive (exited with non-zero exit status 32)"
date: 2013-09-01
forum: General Help
---

### Post by Razor512 on 2013-09-01
Hi, I have a 2TB hard drive that was formatted to ext4 for use in a NAS (single drive)

the drive works fine in the NAS, but when connected to a PC running ubuntu, I get this error message

> 
Unable to access “2.0 TB Volume”


Error mounting /dev/sdc1 at /media/ubuntu-gnome/db689d7d-a84e-42ce-b03d-43a5d9ba4c06: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdc1" "/media/ubuntu-gnome/db689d7d-a84e-42ce-b03d-43a5d9ba4c06"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so








gparted can see the drive and when scanned for errors, it finds nothing.

I don't want to copy a large amount of data through the NAS as it transfers very slowly when dealing with small files (eg a 2 hour transfer on the PC will take 12-24 hours on the NAS depending on the files)

I am running a live USB version on the system I want to copy the data to.

the dmesg command gives this output

> [  883.929948] 0 pages in swap cache
[  883.929949] Swap cache stats: add 0, delete 0, find 0/0
[  883.929950] Free swap  = 0kB
[  883.929951] Total swap = 0kB
[  883.950233] 3342320 pages RAM
[  883.950235] 3113986 pages HighMem
[  883.950236] 232835 pages reserved
[  883.950236] 675807 pages shared
[  883.950237] 213942 pages non-shared
[ 1182.117671] EXT4-fs (sdc1): bad block size 65536



---

### Post by TheFu on 2013-09-01
Some NAS devices are known to screw with the code and not write compatible file systems.  If you shared the exact NAS vendor, model and release, someone might be able to help more.

---

### Post by Razor512 on 2013-09-02
Sorry for the late reply, I am using a WNDR4700 which is basically netgears router a hard drive tray (I mainly use it for bulk storage and DLNA (works okay for larger files (40MB/s write speeds and 80-90MB/s read speeds)

but those speeds drop to around 5MB/s when dealing with lots of tiny files (eg if I backup a system by booting into ubuntu and then copying the contents of the entire partition windows is on, to a folder on the router)

(Since I have a bunch of those types of backups, I mainly want to transfer the to a proper NAS for long term storage, and dedicate the 4700 to more of media. (the small file performance is just crap on the router and theres about 1.5TB of data worth of backups)

I have been meaning to clear the drive up by first copying everything to my true NAS (old PC used as a proper NAS, but nothing seems to want to mount the drive)

---

