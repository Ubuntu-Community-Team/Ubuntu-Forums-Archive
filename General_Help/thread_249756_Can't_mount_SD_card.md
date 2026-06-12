---
title: "Can't mount SD card"
date: 2006-09-03
forum: General Help
---

### Post by konradsa on 2006-09-03
The strange thing first: It works when the card is installed when booting the machine. And it used to work before, so a recent upgrade must have broken it. But I am not sure when it happened, since I did not use SD for a while, it may not work anymore since my Dapper upgrade. Anyways, it used to work automatically, not anymore. If I try to mount manually, this happens:

```
konradsa@ubuntu:~$ sudo pmount /dev/mmcblk0p1
mount: wrong fs type, bad option, bad superblock on /dev/mmcblk0p1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/mmcblk0p1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

konradsa@ubuntu:~$ dmesg | tail
[17214946.212000] XFS: SB read failed
[17214946.248000] JFS: nTxBlock = 8021, nTxLock = 64172
[17214946.256000] mmcblk0: error 1 sending read/write command
[17214946.256000] end_request: I/O error, dev mmcblk0, sector 165
[17214946.256000] mmcblk0: error 1 sending read/write command
[17214946.256000] end_request: I/O error, dev mmcblk0, sector 221
[17214946.268000] mmcblk0: error 1 sending read/write command
[17214946.268000] end_request: I/O error, dev mmcblk0, sector 165
[17214946.268000] mmcblk0: error 1 sending read/write command
[17214946.268000] end_request: I/O error, dev mmcblk0, sector 221
```

Any ideas anybody?

-- Sascha

---

### Post by CameronCalver on 2006-09-03
yes try sudo gedit /etc/fstab and put this in a new line
/dev/mmcblk0p1 /media/sdcard  vfat umasak=0000   0     0

then sudo mkdir /media/sdcard

then sudo mount /media/sdcard

---

### Post by konradsa on 2006-09-03
Ok, I followed your instructions, but the problem seems to persist:

```
konradsa@ubuntu:~$ sudo mount /media/sdcard
mount: /dev/mmcblk0p1: can't read superblock
konradsa@ubuntu:~$ dmesg | tail
[30844.988000] FAT: unable to read boot sector
[30865.704000] mmcblk0: error 1 sending read/write command
[30865.704000] end_request: I/O error, dev mmcblk0, sector 101
[30865.704000] FAT: unable to read boot sector
[30896.760000] mmcblk0: error 1 sending read/write command
[30896.760000] end_request: I/O error, dev mmcblk0, sector 101
[30896.760000] FAT: unable to read boot sector
[30898.260000] mmcblk0: error 1 sending read/write command
[30898.260000] end_request: I/O error, dev mmcblk0, sector 101
[30898.260000] FAT: unable to read boot sector

```

---

### Post by yopnono on 2006-09-03
Try to do a format on the sd card, use the disktool

---

### Post by konradsa on 2006-09-03
> **yopnono said:**
> Try to do a format on the sd card, use the disktool


Hi,

Thanks for the idea. But I don't think that's the problem, since the card mounts just fine when plugged in upon boot, and it has worked just like that before.

---

### Post by yopnono on 2006-09-03
Maybe not, but I know I had a usb memory stick that was working fine in xp and breezy, but I could not mount it or use it in any way in dapper.

After a format it did work fine in xp,breezy,dapper.

---

### Post by konradsa on 2006-09-03
> **yopnono said:**
> Maybe not, but I know I had a usb memory stick that was working fine in xp and breezy, but I could not mount it or use it in any way in dapper.

After a format it did work fine in xp,breezy,dapper.


Ok, maybe it is worth a try. How do I format SD cards with Ubuntu? I have never done that before.

Thanks!!!
Sascha

---

### Post by CameronCalver on 2006-09-04
read this
> **yopnono said:**
> Try to do a format on the sd card, use the disktool

---

### Post by konradsa on 2006-09-04
> **CameronCalver said:**
> read this

Das hatte ich schon gesehen, aber auf der bash passiert nix wenn ich disktool eingebe, und Synaptic kennt es auch nicht.

---

### Post by yopnono on 2006-09-04
> **konradsa said:**
> Das hatte ich schon gesehen, aber auf der bash passiert nix wenn ich disktool eingebe, und Synaptic kennt es auch nicht.

Ok. I don't speak you language but... i guess that you say that you can't find this disktool?

System - Administration - Disks

EDIT:

from terminal 
```
sudo disks-admin
```

---

### Post by konradsa on 2006-09-04
> **yopnono said:**
> Ok. I don't speak you language but... i guess that you say that you can't find this disktool?

System - Administration - Disks

EDIT:

from terminal 
```
sudo disks-admin
```

Wow,

I am really sorry, I meant to write in English, but I guess I was thinking in German. Ok, I checked the disks-admin, and the card does not show up in the storage list on the left. I also tried the Gnome partition editor, there it shows up as unalloctaed space, but the attempt to create an msdos partition results in "Error while setting new disklabel". Here is dmesg | tail: 
```

[17244741.700000] mmcblk0: error 1 sending read/write command
[17244741.700000] end_request: I/O error, dev mmcblk0, sector 105
[17244741.700000] mmcblk0: error 1 sending read/write command
[17244741.700000] end_request: I/O error, dev mmcblk0, sector 106
[17244741.700000] mmcblk0: error 1 sending read/write command
[17244741.700000] end_request: I/O error, dev mmcblk0, sector 107
[17244741.700000] mmcblk0: error 1 sending read/write command
[17244741.700000] end_request: I/O error, dev mmcblk0, sector 108
[17244741.700000] mmcblk0: error 1 sending read/write command
[17244741.700000] end_request: I/O error, dev mmcblk0, sector 101
```

---

### Post by yopnono on 2006-09-04
Ok. Have you tried to use this in terminal.
```
sudo umount /your/device
```
then this.
```
mkfs.vfat -c /your/device
```

---

### Post by konradsa on 2006-09-04
> **yopnono said:**
> Ok. Have you tried to use this in terminal.
```
sudo umount /your/device
```
then this.
```
mkfs.vfat -c /your/device
```

Ok, the result of that is:

```
konradsa@ubuntu:~$ sudo mkfs.vfat -c /dev/mmcblk0
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: bad blocks before data-area: cannot make fs
```

dmesg:

```
[17252168.848000] mmcblk0: error 1 sending read/write command
[17252168.848000] end_request: I/O error, dev mmcblk0, sector 104
[17252168.852000] mmcblk0: error 1 sending read/write command
[17252168.852000] end_request: I/O error, dev mmcblk0, sector 103
[17252168.852000] mmcblk0: error 1 sending read/write command
[17252168.852000] end_request: I/O error, dev mmcblk0, sector 102
[17252168.852000] mmcblk0: error 1 sending read/write command
[17252168.852000] end_request: I/O error, dev mmcblk0, sector 101
[17252171.356000] mmcblk0: error 1 sending read/write command
[17252171.356000] end_request: I/O error, dev mmcblk0, sector 0
```

P.S.: I also tried sudo mkfs.vfat -c /dev/mmcblk0p1, same result. And I just reformated the card in my camera, to no avail.

---

### Post by yopnono on 2006-09-04
humm. according to your log the device is defect, but it seems to work in your camera, and if it's mounted at boot. So I really don't know then. It might be the drivers in dapper.

Have you tried to do a check-disk in IE windows, just to see if you get any errors then.

Try to use this switch.
```

mkfs.vfat -Ic /dev/your_device

```

---

### Post by konradsa on 2006-09-04
> **yopnono said:**
> humm. according to your log the device is defect, but it seems to work in your camera, and if it's mounted at boot. So I really don't know then. It might be the drivers in dapper.

I really appreciate you trying to help me though. I am also starting to suspect it's the Dapper drivers and they will hopefully fix it soon.

> **yopnono said:**
> 
Have you tried to do a check-disk in IE windows, just to see if you get any errors then.

Sorry, how does that work exactly? You mean running checkdisk in Windows?

---

### Post by yopnono on 2006-09-04
In xp/2000/NT

chkdsk

win9x scandisk


Try this 
```
mkfs.vfat -Ic /dev/your_device
```

---

### Post by whitehawk_hu on 2007-05-13
Hey!

Same problem here with Feisty. It seems like the plugged in device is connected for milliseconds again and again, I don't think it's mechanical.

I have 3 cards, one is not working in my built in laptop Texas Instruments reader. The thing is, that it works perfectly with my Hama usb SD card reader. I tried formatting, but it of course ad no use.. (I format every flash I buy ASAP anyway).

Oh I was on a happening and I asked my friends to give me their cards and none worked, about (3 had SD), so I don't think it's the cards defect.

---

### Post by Freaky_Llama on 2007-05-16
I had this issue in Feisty 7.04 as well. My laptop has a built in Card reader, and a day after I installed it, the card reader worked and automounted it. The card I used was a SANDisk SD Card adapter for my Micro SD card from my cell phone. The Micro card is 1GB in size. Feisty had no issues mounting or reading from it (except what was actually a folder from my phone and Windoze perspective was now a single file in Feisty). Now last night, I tried a SD Card that was NOT a SANDisk card, 512MB in size, and it did the same thing described above, showing up/disappearing from /dev/mmcblk0 AND /dev/mmcblk0p1 . Attempting a mount at the right time gave the bad Superblock errors. I immediately rebooted and went into Vista and was able to read the disk and copy things over to a USB key that works in Feisty. 

I wish I could eliminate it by brand, but a 2GB SANDisk card doesn't work as I just tried now. And also, I just tried a Kingston MicroSD adapter and it works. It mounted (although it said unable to mount) and it put an icon on the desktop. It also is showing a folder structure whereas before it didn't. 

Its definetly some wierd behavior. I tried the 2GB, and here's what I got:

```
[ 2639.516000] ReiserFS: mmcblk0p1: warning: sh-2006: read_super_block: bread failed (dev mmcblk0p1, block 128, size 512)
[ 2639.516000] ReiserFS: mmcblk0p1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on mmcblk0p1

```

UPDATE: The 2GB is working now for some reason. I did absolutely nothing but umount the other card after I posted the error messages.
After more testing, it seems that dmesg shows that it detects an sd card, but nothing happens after that. whatever is supposed to mount it checks all the available FS types and tries to mount it, and when it hits Reiser, it gives the detailed errors (I use Reiser for Ubuntu). Other times, when it works, it's giving the same errors, but it still mounts and can read from the card (in the case of the 2GB card)

```
[ 3598.680000] ReiserFS: mmcblk0p1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on mmcblk0p1
[ 3598.712000] mmcblk0: error 1 sending read/write command
[ 3598.712000] end_request: I/O error, dev mmcblk0, sector 249
[ 3598.712000] mmcblk0: error 1 sending read/write command
[ 3598.712000] end_request: I/O error, dev mmcblk0, sector 313
[ 3598.712000] mmcblk0: error 1 sending read/write command
[ 3598.712000] end_request: I/O error, dev mmcblk0, sector 369
[ 3599.516000] tifm_7xx1: sd card detected in socket 1
[ 3599.624000] mmcblk0: mmc1:8000 SD02G 1985024KiB 
[ 3599.624000]  mmcblk0: p1
[ 3599.792000] UDF-fs: No partition found (1)
[ 3599.900000] Unable to identify CD-ROM format.

```

-Then, its mounted, complete with an icon on the desktop and a folder window open.

---

### Post by tgbrowning on 2007-06-28
Try as I might, I can only get a 16 meg SD card to mount properly. No problem with that, or unmounting. Works fine, can pull it out and lose the entry. Reinsert it, and it shows up with an icaon.  Can write to it, or read from it.

Working with a 1 or 2 gig SD card is flaky. Sometimes it will mount and other times, it won't.  When it does mount, I don't have the ability to write to it.  

Here's what my fstab entry looks like:

/dev/mmcblk0p1  /media/sdcard vfat -rw 0 0

Any ideas?

Browning>>>

---

### Post by trogo on 2007-07-02
I haven't tested it yet but i think the solution could be this!!!

[HTML]http://ubuntulinuxtipstricks.blogspot.com/2007/04/texas-instruments-sdmmc-card-reader.html[/HTML]

It says it will work just for sd or mmc cards, but it's enough for me! I'll try it tomorrow and post results for all!!

---

### Post by tgbrowning on 2007-07-02
Got mine working -- apparently you should NOT be working with fstab at all. It appears that, under Dapper anyway, that the Texas Instruments chip set used by SanDisk in their readers (and lots of other) is not supported. You have to find a reader that doesn't use TI chips.

Which I did, for about 15 bucks.

It's a GE distrobution of an other company, something like JohnsonProducts. Do a search for GE and see my report on it.

---

### Post by trogo on 2007-07-03
The solution i posted before solved the problem for me! Follow it and let me know!!!!!

---

