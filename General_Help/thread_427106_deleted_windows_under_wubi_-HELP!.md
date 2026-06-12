---
title: "deleted windows under wubi -HELP!"
date: 2007-04-29
forum: General Help
---

### Post by ineksuyu on 2007-04-29
Hi,

I was trying to mount my external NTFS usd drive, and somehow I managed (!) to put my whole hard drive in the trash can of ubuntu!


Since ubuntu is also installed under windows, now I can't boot. I tried to repair windows with a windows CD, and realised that everything is now under "C:\.Trash-alf128\WINDOWS". Is there any way that I can recover my system at all?

When I try "cd .Trash-alf128", it says "access is denied". 

Any help will be extremely appreciated.


Huseyin:confused:

---

### Post by tuxcantfly on 2007-05-01
boot using an ubuntu 7.04 live cd

make sure the disks are unmounted

then in a terminal:

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/ntfs
sudo fdisk -l | grep NTFS
```

then something like this will show up:

```
/dev/sda1   *           1       12158    97659103+   7  HPFS/NTFS
```

take that first bit (/dev/sda1 in my case) and substitute it in here:

```
sudo ntfs-3g /dev/sda1 /media/ntfs
```

then navigate to /media/ntfs and all your files will be accessible with read/write support, just cut-paste the files back to where they should be

---

