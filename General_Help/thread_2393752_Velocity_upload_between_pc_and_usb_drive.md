---
title: "Velocity upload between pc and usb drive"
date: 2018-06-07
forum: General Help
---

### Post by sed_faster on 2018-06-07
Hello folks,

What do you think about this velocity upload the simple archive to a usb drive on my pc:
```
$ rsync --info=progress2 Downloads/AutoCAD_2016_Win_64bit_dlm.sfx.exe /media/eno/KINGSTON/
  1,979,152,984 100%    2.00MB/s    0:15:42 (xfr#1, to-chk=0/1)
```

Info about my system:

```

$ uname -a
Linux xx 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic

```

Thanks

---

### Post by sudodus on 2018-06-07
What USB drive is it? What USB port is it?

After using a USB pendrive for some time, it will get slow. When the speed is reduced to half, I wipe the whole device with mkusb in order to get back [almost] the original speed. See this link,

[Pendrive lifetime](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

### Post by sed_faster on 2018-07-02
Hello,

I tried copy the same files on windows SO and the velocity it were very more faster! Right now, I use this command to send the iso file to usb drive and the velocity it is only 657.571 kB/s. Is it slower, right?
```

rsync --info-progress2 source destination

```

The pc is: [http://www.toshiba.pt/discontinued-products/satellite-l650-11f/](http://www.toshiba.pt/discontinued-products/satellite-l650-11f/)
and the system are:
```

Linux 4.4.0-112-generic Lubuntu 16.04

```

Thanks

---

### Post by sudodus on 2018-07-02
The rsync commands that you show are very slow even for USB 2.

Please tell us the speed, when you copy with Windows (for a comparison).

What USB drive is it? Please specify the brand name and model.

What file system is there on the USB drive (FAT32, NTFS, exFAT, ext4 ...)?

---

