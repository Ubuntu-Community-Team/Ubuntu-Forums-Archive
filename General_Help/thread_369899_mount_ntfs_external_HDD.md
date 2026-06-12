---
title: "mount ntfs external HDD"
date: 2007-02-25
forum: General Help
---

### Post by jude999 on 2007-02-25
Hi all, I need a little help here.
I feel a little lost as I have been through most of the topics here that talk about mounting an external HDD.

I bought a 120G USB drive yesterday, coudn't format it on my Ubuntu machine so I did it with my WinXP machine at work. It is now ntfs formatted and works on windows.
I tried to mount it on my ubuntu with no luck.

In gparted it shows as /dev/sda as unallocated 
I have installed ntfs-3g
I have edited my fstab with /dev/sda     /mnt/usbdisk     ntfs-3g     defaults,locale=en_US.utf8   0    0

I also tried anything esle I could think of.... nothing.

Any thoughts?

---

### Post by yabbadabbadont on 2007-02-25
With the drive plugged in, run "sudo fdisk -l".  I would almost be willing to bet that the ntfs partition on the drive is really /dev/sda1.  ;)

---

### Post by xmastree on 2007-02-25
If it's a USB drive, you shouldn't need to alter fstab. Also, why not format it FAT32?

---

### Post by jude999 on 2007-02-25
did that many many times, and I forgot to state this in my 1st post: the external hdd is not showing up:

```
simon@simon:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4687    37648296   83  Linux
/dev/hda2            4688        4864     1421752+   5  Extended
/dev/hda5            4688        4864     1421721   82  Linux swap / Solaris

Disk /dev/sdb: 4072 MB, 4072669184 bytes
128 heads, 32 sectors/track, 1942 cylinders
Units = cylinders of 4096 * 512 = 2097152 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1942     3977200    c  W95 FAT32 (LBA)

```

sdb1 is my psp that happens to be plugged in right now

---

### Post by yabbadabbadont on 2007-02-25
With the external drive plugged in (I assume it was when you ran fdisk...), please run "dmesg" and post the output here.

---

### Post by jude999 on 2007-02-25
> **xmastree said:**
> If it's a USB drive, you shouldn't need to alter fstab. Also, why not format it FAT32?

I should have done that, but when I formatted it I didn't think about it. I already transfered over 40G of data on it and don't want to go through that again.

If it really does not work, I will reformat to fat32 (can you do this on windows? gparted refuses to format my drive.)

---

### Post by jude999 on 2007-02-25
> **yabbadabbadont said:**
> With the external drive plugged in (I assume it was when you ran fdisk...), please run "dmesg" and post the output here.

it's full of error. I have just copied the few last lines, the original is huge and repetitive:

```
[17182235.808000] sdb: assuming drive cache: write through
[17182235.808000]  sdb: sdb1
[17182235.812000] sd 2:0:0:0: Attached scsi removable disk sdb
[17182235.812000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[17182236.620000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17182779.288000] sd 0:0:0:0: SCSI error: return code = 0x10070000
[17182779.288000] end_request: I/O error, dev sda, sector 0
[17182779.288000] Buffer I/O error on device sda, logical block 0
[17182779.292000] sd 0:0:0:0: SCSI error: return code = 0x10070000
[17182779.292000] end_request: I/O error, dev sda, sector 0
[17182779.292000] Buffer I/O error on device sda, logical block 0
[17182779.304000] sd 0:0:0:0: SCSI error: return code = 0x10070000
[17182779.304000] end_request: I/O error, dev sda, sector 0
[17182779.304000] Buffer I/O error on device sda, logical block 0
[17182779.324000] sd 0:0:0:0: SCSI error: return code = 0x10070000
[17182779.324000] end_request: I/O error, dev sda, sector 8
[17182779.324000] Buffer I/O error on device sda, logical block 1
[17182779.328000] sd 0:0:0:0: SCSI error: return code = 0x10070000
[17182779.328000] end_request: I/O error, dev sda, sector 16
[17182779.328000] Buffer I/O error on device sda, logical block 2
[17182779.328000] sd 0:0:0:0: SCSI error: return code = 0x10070000
[17182779.328000] end_request: I/O error, dev sda, sector 24
[17182779.328000] Buffer I/O error on device sda, logical block 3
[17182779.332000] sd 0:0:0:0: SCSI error: return code = 0x10070000
[17182779.332000] end_request: I/O error, dev sda, sector 0
[17182779.332000] Buffer I/O error on device sda, logical block 0

```

---

### Post by yabbadabbadont on 2007-02-25
If it isn't already, make sure that the drive is jumpered as Master.

---

### Post by jude999 on 2007-02-25
> **yabbadabbadont said:**
> If it isn't already, make sure that the drive is jumpered as Master.
now you lost me :S 
what does that mean?

---

### Post by yabbadabbadont on 2007-02-25
It is too hard (for me) to explain in words.  It would be easy to show you, but that isn't an option here.  :)  Sorry.  It may not have even made a difference anyway.

---

### Post by jude999 on 2007-02-25
thanks anyway... i hope someone can help here...

---

### Post by xmastree on 2007-02-25
> **yabbadabbadont said:**
> If it isn't already, make sure that the drive is jumpered as Master.

> **jude999 said:**
> now you lost me :S 
what does that mean?

> **jude999 said:**
> thanks anyway... i hope someone can help here...

The external drive should have a link, between the power connector and the IDE cable. That selects whether it's master or slave (if you have two drives on one cable, one must be master and one must be slave).

There's a picture of one here:
[http://hardware.adslzone.net/images/tutorials/1/image041.jpg](http://hardware.adslzone.net/images/tutorials/1/image041.jpg)

That might well be the problem. I have one of those IDE/USB adaptors, and that won't work if the drive is set to slave.

Is it a 3.5" drive, externally powered. Or a 2.5" (laptop size) which draws power from the USB port?

---

### Post by jude999 on 2007-02-25
Is it a 3.5" drive, externally powered. Or a 2.5" (laptop size) which draws power from the USB port?[/QUOTE]

it's a 2.5". do they also have those master/slave thingies?

---

### Post by xmastree on 2007-02-25
> **jude999 said:**
> it's a 2.5". do they also have those master/slave thingies? Hmm :k not sure. I'm looking at one here, which works fine with my ubuntu laptop, and it does have four pins separate from the main 40, but they're devoid of any markings.

So, next question. Is the XP you used to format it on a different computer, or are you dual booting?

It could be that the ubuntu computer's USB port doesn't have enough power to drive the disk. My laptop doesn't, so I have to use a powered hub.

---

### Post by jude999 on 2007-02-25
> **xmastree said:**
> 
So, next question. Is the XP you used to format it on a different computer, or are you dual booting?
Other computer, i'm not dual booting.
> It could be that the ubuntu computer's USB port doesn't have enough power to drive the disk. My laptop doesn't, so I have to use a powered hub.
I used another similar external drive (though only 30G) in the pas that worked fine (it was fat32).

And I do see this one in gparted but is says "unallocated"
When I try to format it with gparted it tells me "error while setting new disklabel"

---

### Post by Kenja on 2007-03-01
This thread worked for me.  I also have an external HDD with NTFS format.

[http://ubuntuforums.org/showthread.php?t=357508&highlight=mount+external+hdd](http://ubuntuforums.org/showthread.php?t=357508&highlight=mount+external+hdd)

```
sudo mkdir /media/sdb1
sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o nls=utf8,umask=0222 df -h
```

---

### Post by jude999 on 2007-03-01
Thanks. I tried it already, didn't work. Since that I formatted to Fat32, but I can still not mount it. Anyway, I gave up for now, I might look a little more into that this weekend.

---

### Post by Kenja on 2007-03-02
> **jude999 said:**
> Thanks. I tried it already, didn't work. Since that I formatted to Fat32, but I can still not mount it. Anyway, I gave up for now, I might look a little more into that this weekend.

If you cut & pasted from that thread it wouldn't have worked.  It would have entered...

```
sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o nls=utf8,umask=0222
df -h
```

instead of...

```
sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o nls=utf8,umask=0222 df -h
```

---

