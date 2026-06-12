---
title: "CDROM Drives Not mounting after Fresh Install 14.04"
date: 2015-01-30
forum: General Help
---

### Post by Glenn_Morrissey on 2015-01-30
Hi

I am trying to get my internal cd/dvd reader/writer, /dev/sr0, and my usb cd/dvd reader/writer, /dev/sr1, to mount after a fresh install, without success. Whether it be music, or data discs [CD or DVD] doesn't seem to matter, it just won't mount them using the mount command (except the ubuntu install cd, which it will mount, read-only). If I plug in my external CD/DVD Drive I get the following dmesg | tail output:
```

glenn@Asus:~$ dmesg | tail
[ 1755.174697] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1755.174701] usb 1-6: Product: MT1887 
[ 1755.174704] usb 1-6: Manufacturer: MediaTek Inc
[ 1755.174707] usb 1-6: SerialNumber: S15T6YMF300S7C 
[ 1755.179729] usb-storage 1-6:1.0: USB Mass Storage device detected
[ 1755.180025] scsi10 : usb-storage 1-6:1.0
[ 1756.183840] scsi 10:0:0:0: CD-ROM            TS8XDVDS TRANSCEND        TW00 PQ: 0 ANSI: 0
[ 1756.219826] sr1: scsi3-mmc drive: 62x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[ 1756.220130] sr 10:0:0:0: Attached scsi CD-ROM sr1
[ 1756.220304] sr 10:0:0:0: Attached scsi generic sg2 type 5

```
When I try and mount the drive with blank media:
```

glenn@Asus:~$ sudo mount -t /dev/sr1 /media/cdrom
[sudo] password for glenn: 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
...

```
I get the mount help. If I try and mount my ubuntu install dvd...

```

 glenn@Asus:~$ sudo mount -t iso9660 /dev/sr1 /media/cdrommount: block device /dev/sr1 is write-protected, mounting read-only
glenn@Asus:~$

```
Thats Ok, but if I try and mount an audio CD, I just get the mount help output.
If I try and mount a blank CD, again, I get the mount help. 
Again, after inserting the blank CD, I get the following in dmesg | tail

```

glenn@Asus:~$ dmesg | tail[ 2096.886265] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2096.886273] usb 1-6: Product: MT1887 
[ 2096.886280] usb 1-6: Manufacturer: MediaTek Inc
[ 2096.886287] usb 1-6: SerialNumber: S15T6YMF300S7C 
[ 2096.891832] usb-storage 1-6:1.0: USB Mass Storage device detected
[ 2096.892025] scsi11 : usb-storage 1-6:1.0
[ 2097.895873] scsi 11:0:0:0: CD-ROM            TS8XDVDS TRANSCEND        TW00 PQ: 0 ANSI: 0
[ 2097.933864] sr2: scsi3-mmc drive: 8x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[ 2097.934137] sr 11:0:0:0: Attached scsi CD-ROM sr2
[ 2097.934358] sr 11:0:0:0: Attached scsi generic sg2 type 5
glenn@Asus:~$ 

```

Before I reistalled, automount would work, that is, I would put in a cd or a dvd and a dialog box would open asking me what I wanted to do. Now nothing appears. 

I can mount other things manually using mount, such as my Seagate HDD, which I have an entry in /etc/fstab for, and I can mount usb flash drives as well, but no joy with either of the Optical drives, internal or external.

Oh, here is the output from lsusb:

```

Bus 001 Device 009: ID 0e8d:1806 MediaTek Inc. Samsung SE-208AB Slim Portable DVD Writer

```

And the output from wodim --devices

```

glenn@Asus:~$ wodim --devices
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
glenn@Asus:~$

```

Can someone please tell me where I am going wrong?

Glenn.

---

### Post by mc4man on 2015-01-30
> **Glenn_Morrissey said:**
> 
Can someone please tell me where I am going wrong?


You don't mount the device, just the filesystem on it. So blank media has nothing to mount & audio cd's can't be mounted, the representative contents are viewed or accessed by location,  - ex.'s 
 cdda://sr0/  ;  cdda://sr1/  ;  cdda://sr2/  ect.

When inserted you usually should get some indication of the disc in your filemanager or a pop up asking what to do. The popup is dependent in 14.04 on some gnome3 nonsense that the automount option should apply to all removable media,  even those that don't 'mount',   by default that is enabled.
To check anyway, should return true - 
```
gsettings get org.gnome.desktop.media-handling automount
```

---

### Post by Glenn_Morrissey on 2015-02-06
I think there is something screwy with my hardware. After some boots, it autoounts on demand, after some boots it doesn't, and I have to mount manually using the mount command, even after:
```
.
glenn@Asus:~$ gsettings get org.gnome.desktop.media-handling automount
true
glenn@Asus:~$

```
I thought initially that I has screwed up something, so I did a fresh reinstall of Ubuntu Gnome 14.04, and automount works sometimes, but sometimes it does not.

---

### Post by mc4man on 2015-02-06
Does seem hardware related. For example - 
Audio cd's don't need to be 'mounted' to be playable. Also in regards to audio cd's the 'mounting' of them thru automount only enables autoplay via a chosen app, nothing more.
Example in screen
automount is disabled so audio cd is visible in nautilus but not mounted. Meanwhile audacious is playing the cd..

(- that was one of the points of my bug that wasn't grasped, I'd like to disable automount of volumes, usb drives ect. but keep automount/autoplay of optical media like audio cd's, dvd's. That was the way it was in the past but no more.

---

