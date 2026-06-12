---
title: "unreadable usb key"
date: 2014-11-03
forum: General Help
---

### Post by azen0r on 2014-11-03
Hello,
Returning from holiday during which I transfered most of my pictures from camera to an usb key to be able to take new ones, I'm very annoyed because I can't read the usb key anymore.
The key is 8Go, Fat32, the transfer was made with a Windows 8 computer and I've been able to see the pictures on the TV of the hotel a few days ago. Since that, the key has only traveled by plane (I can't see any other noticeable fact).

I can't read the key with my ubuntu, nor XP and Vista. My own TV is also unable to read it.

when I plug, **dmesg **now reads :
```
$ dmesg
[  436.960100] usb 2-3: new high-speed USB device number 10 using ehci_hcd
[  437.122003] scsi12 : usb-storage 2-3:1.0
[  438.121849] scsi 12:0:0:0: Direct-Access              USB MEMORY BAR   1000 PQ: 0 ANSI: 0 CCS
[  438.123335] sd 12:0:0:0: Attached scsi generic sg2 type 0
[  438.127416] sd 12:0:0:0: [sdb] Attached SCSI removable disk
```

though the first times I also had those two lines :
```
Failed to get diagnostic page [...]
Failed to bind enclosure -19
```I don't have them since I rebooted

**lsusb** : 
```
$ lsusb
[...]
Bus 002 Device 010: ID 090c:3000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
```

When I plug, a /dev/sdb also appears which I'm unable to mount

Is there anything I can try to recover my pictures ? Tank you

---

### Post by flaymond on 2014-11-03
Hello! This happen when you use your USB too boot your computer? If so, this is happened because of your USB became a 'bootable' drive. Just think its a Microsoft Windows installer CD...you can't view the files...but you can install the OS into your PC. (its like closed sources). So, to fix your problen, try try Disk Image Writer..and reformat back..your drive (I believe now it is Hidden NSTF format) will become like your old 'USB' back....

Tips: Disk Image Writer is pre-installed

---

### Post by sudodus on 2014-11-03
As long as you see the device (as you describe: /dev/usb also appears which I'm unable to mount), it is possible to use ***PhotoRec*** to recover files from it. Even if the file system is destroyed, but the data (zeroes and ones) are still there, PhotoRec can identify the beginning of the file data and save it (until it finds the beginning of the next batch of file data). The file names will be gone, but I think you will be able to recover your pictures, or at least most of them.

PhotoRec is free software and available directly from

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

and also possible to install into Ubuntu.

It is also possible, that you can repair the FAT32 file system. In Windows, you can try with

```
chkdsk /f
```

from a terminal window (alias 'dos-prompt' alias cmd ) or the corresponding graphical user interface.

-o-

chkdsk is OK to run, but do ***not*** format the pendrive !!!

---

### Post by coldraven on 2014-11-03
+1 for PhotoRec,  it comes with the Testdisk utility so install it like this
```
sudo apt-get install testdisk
```

then run PhotoRec as root and select the USB drive with the arrow keys
```
sudo photorec
```

---

### Post by Bucky Ball on 2014-11-03
> **InterProg said:**
> Hello! This happen when you use your USB too boot your computer?


??? Please read posts carefully. This has nothing to do with booting from the USB. The USB has, or had, photos on it and won't mount in a running install. :-k

If they reformat the drive (worse thing OP could possibly do) they will completely erase anything that might be on the drive, including the photos they are about to attempt to retrieve using testdisk and photorec.

---

### Post by azen0r on 2014-11-03
Thank you for your replies.

@InterProg : this is not a bootable usb key at all, just a fat32 volume to store data. Does your proposition still apply ?

@sudodus&coldraven : I made a little mistake, it is not /dev/usb but /dev/sdb that appear when I plug the usb key. Anyway I tried photorec but it does not show the media /dev/sdb in the interface. I also tried to force photorec into /dev/sdb, unsuccessfully :
```
$ sudo photorec /dev/sdb 
Unable to open file or device /dev/sdb
```

As for windows behaviour when I plug the key, it creates a I: disk in the explorer but asks "Insert a disk into I: drive" when I open it. fdisk returns
```
>chkdsk I:
Cannot open volume for direct access.
```

any further idea?
thankyou

---

### Post by Bucky Ball on 2014-11-03
Hang on. When you plug it in you see /dev/sdb? Open gparted and click the drop down list in the top right corner and select sdb. Are there partitions on it? If there are, take note of sdb* the partitions are (sdb1 for instance) and then:
```

sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
```

Go to a file manager and navigate to the /mnt directory. There should be a mount point 'sdb1' in there. Double click. Files there?

---

### Post by sudodus on 2014-11-03
OK, /dev/sdb is a normal 'name' for a pendrive. The advice still applies (in principle). But it worries me that PhotoRec does not list it. I checked in my computer, and it should be listed (alongside the other drives). It looks like this for me

```
PhotoRec 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

  PhotoRec is free software, and
comes with ABSOLUTELY NO WARRANTY.

Select a media (use Arrow keys, then press Enter):
 Disk /dev/sda - 320 GB / 298 GiB (RO) - SAMSUNG HD322HJ
 Disk /dev/sdb - 60 GB / 55 GiB (RO) - OCZ-AGILITY3
 Disk /dev/sdc - 1000 GB / 931 GiB (RO) - WDC WD1003FBYZ-010FB0[COLOR=#0000cd]
>Disk /dev/sdd - 8004 MB / 7633 MiB (RO) - SanDisk Ultra[/COLOR]

```

Check what happens if you un-plug and re-plug the pendrive and then try again with

```
sudo photorec
```

You can also try in another USB port.

If you can't make PhotoRec list the pendrive, you have a bigger problem. Then I think it is not a software problem (broken file system), but it might be a hardware problem, that the pendrive's hardware is failing.

---

### Post by azen0r on 2014-11-03
I confirm that neither gparted nor photorec list my device. they see only sda, my hard drive...
*sigh*

---

### Post by Bucky Ball on 2014-11-03
It was unmounted correctly if used prior to this in a Windows machine? Shot in the dark, but plug it into a Win machine if you have one and 'safely remove'.

---

### Post by sudodus on 2014-11-03
I'm sorry, but I have no remedy for that problem. Maybe someone else, who has more insight into the internal system of flash memory.

---

### Post by azen0r on 2014-11-03
@Bucky Ball : Windows is also unable to read the usb key, with its own error messages (see my previous posts). The very last system where the key was used is a TV, so I cannot tell if the unmount was correct, but I think no arm can be done by readonly, otherwise it would be a shame to the tv manufacturer...

@sudodus : thank you for your help, let's wait a couple of days more hopping to get help from a flash wizard...

---

### Post by tripp98 on 2014-11-03
open a terminal
sudo tail -f /var/log/syslog

plug in usb device.  you will get some scrolling text.  it may assist in telling you what has gone wrong with ur usb drive.

---

### Post by Bucky Ball on 2014-11-03
Not sure a 'flash wizard' can help if the dongle is dead, and it sure sounds like it might be if you can't boot it on any OS. :-k

---

### Post by azen0r on 2014-11-04
Hello, here is the output :

```
sudo tail -f /var/log/syslog
Nov  4 09:54:18 jb-ubuntu kernel: [10174.804116] usb 2-1: new high-speed USB device number 6 using ehci_hcd
Nov  4 09:54:18 jb-ubuntu mtp-probe: checking bus 2, device 6: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1"
Nov  4 09:54:18 jb-ubuntu kernel: [10174.968520] scsi8 : usb-storage 2-1:1.0
Nov  4 09:54:18 jb-ubuntu mtp-probe: bus: 2, device: 6 was not an MTP device
Nov  4 09:54:19 jb-ubuntu kernel: [10175.969342] scsi 8:0:0:0: Direct-Access              USB MEMORY BAR   1000 PQ: 0 ANSI: 0 CCS
Nov  4 09:54:19 jb-ubuntu kernel: [10175.970505] sd 8:0:0:0: Attached scsi generic sg3 type 0
Nov  4 09:54:19 jb-ubuntu kernel: [10175.974438] sd 8:0:0:0: [sdc] Attached SCSI removable disk
```

What does it tell ? :?

---

### Post by sotiris2 on 2014-11-04
Does now gparted or photorec list a device named sd**c** ? There is no error but it says it is attached as sd**c** probably because you already have another device as sdb.

---

