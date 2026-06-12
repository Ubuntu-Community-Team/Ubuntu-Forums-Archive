---
title: "Mounting &quot;Data&quot; Partition"
date: 2008-01-26
forum: General Help
---

### Post by Graham1 on 2008-01-26
Hi

Having converted my FAT32 partition to NTFS, it has now mounted to media (i.e /media/DATA) instead of /mnt/data. Is it possible to mount back onto /mnt ? (i.e /mnt/data). If so, how do I go about doing this? 

Btw, there is quite alot of data on this partition, so will I need to move off first?

:)

---

### Post by taurus on 2008-01-26
```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo umount /media/DATA
sudo mount -t ntfs-3g **/dev/sda1** /mnt/data
df -h
```
Replace **/dev/sda1** with the actual partition of that ntfs filesystem.

---

### Post by Graham1 on 2008-01-27
Hi taurus

That seemed to do the trick whilst in the current session but as soon as I reboot, it goes back to /media/DATA. Any ideas how to correct this?

:)

---

### Post by Graham1 on 2008-01-27
If this helps, here's the contents of my fstab:-

"# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=98968f1e-bc92-4720-b080-34055fe654d7 /               ext3    defaults,errors=remount-ro 0       1

# /dev/hda6
# UUID=460A-D4FB  /mnt/data       vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/hda5
UUID=4c83e721-d255-4ec3-bda0-3a383be4af67 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0"

As you can see, my old FAT33 partition used to be on hda6 but I wasn't sure whether I could just change this to hda7 and change vfat to ? (ntfs or ntfs-3g). Also, wasn't sure about the UUID... bit so just commented out.

:)

---

### Post by Graham1 on 2008-01-27
Bump ;)

:)

---

### Post by taurus on 2008-01-27
Can you post

```
sudo fdisk -l
ls -la /dev/disk/by-uuid
```

---

### Post by Graham1 on 2008-01-27
Disk /dev/hda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x030d030d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6374    51199123+  83  Linux [COLOR="Red"]< Ubuntu, Ext3[/COLOR]
/dev/hda2            6375       12750    51215220   83  Linux [COLOR="Red"]< Spare[/COLOR]
/dev/hda3           12751       19125    51207187+  17  Hidden HPFS/NTFS [COLOR="Red"]< Windows XP, NTFS[/COLOR]
/dev/hda4           19126       30515    91490175    f  W95 Ext'd (LBA)
/dev/hda5           19126       19138      104391    b  W95 FAT32 [COLOR="Red"]< XOSL, FAT32 (Boot Loader)[/COLOR]
/dev/hda6           19139       19393     2048256   82  Linux swap / Solaris
/dev/hda7           19394       30515    89337433+   7  HPFS/NTFS [COLOR="Red"]< Data, NTFS [/COLOR]



total 0
drwxr-xr-x 2 root root 160 2008-01-27 23:21 .
drwxr-xr-x 6 root root 120 2008-01-27 22:12 ..
lrwxrwxrwx 1 root root  10 2008-01-27 23:21 0826-002F -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-01-27 22:12 2028CEBF28CE92E8 -> ../../hda3
lrwxrwxrwx 1 root root  10 2008-01-27 22:12 479A-7E47 -> ../../hda5
lrwxrwxrwx 1 root root  10 2008-01-27 22:12 501C3D301D777184 -> ../../hda7
lrwxrwxrwx 1 root root  10 2008-01-27 22:12 7ff28fd2-5637-40c4-b780-b7f8c5916a5c -> ../../hda2
lrwxrwxrwx 1 root root  10 2008-01-27 22:12 98968f1e-bc92-4720-b080-34055fe654d7 -> ../../hda1

---

### Post by taurus on 2008-01-27
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line at the end for /dev/hda7, ntfs filesystem.

```
UUID=501C3D301D777184   /mnt/data   ntfs-3g   defaults   0   0
```
By the way, is the swap partition even working on your machine because I don't even see /dev/hda6 from /dev/disk/by-uuid?

```
free
```

---

### Post by Graham1 on 2008-01-27
Hi taurus

Below is the results from "free":-            

 total       used       free     shared    buffers     cached
Mem:       1035636     737624     298012          0      24472     400516
-/+ buffers/cache:     312636     723000
Swap:            0          0          0

I guess not going by the 0's

:)

---

### Post by taurus on 2008-01-27
What happens when you run this command from a terminal?

```
sudo swapon /dev/hda6
```
If there is no error message, check your swap again.

```
free
```

---

### Post by Graham1 on 2008-01-27
Hi

Results from "sudo swapon /dev/hda6" below:-             

 total       used       free     shared    buffers     cached
Mem:       1035636     596448     439188          0      12404     338380
-/+ buffers/cache:     245664     789972
Swap:      2048252          0    2048252

Will my "swap" file remain active now even when I reset my computer?

:)

---

### Post by Graham1 on 2008-01-27
Just a quick question :). How do I get "Data" to appear under Places in Nautilus?

:)

---

### Post by taurus on 2008-01-27
Now, you need to edit /etc/fstab again and replace these two lines

```

# /dev/hda5
UUID=4c83e721-d255-4ec3-bda0-3a383be4af67 none swap sw 0 0

```
with these two new lines so that swap will be activated everytime you boot Ubuntu.

```

#/dev/hda6--swap
/dev/hda6   none   swap   sw   0   0
```

And for your question about nautilus, you probably have to mount it to /media/data instead of /mnt/data.  And if you decide to change the mount point from /mnt/data to /media/data, you need to create the new mount point or it won't be mounted next time you boot Ubuntu.

```
sudo mkdir /media/data
```

---

### Post by Graham1 on 2008-01-27
Does it matter whether I mount to Media or Mnt? I've always thought that "Media" was for removable drives (maybe it is) and "Mnt" for fixed disks.

Many thanks for your help with this taurus :D.

:)

Btw, how do I award you "thanks" points?

---

### Post by taurus on 2008-01-27
If you want a nice little icon on your desktop for the drive, then you should mount it to /media.  And if you want to access it, just double click on the icon and it will open the drive up for you to use.  Quite handy for beginners.

Doesn't really matter where you mount it.  It's up to individual though.

---

### Post by Graham1 on 2008-01-27
Sorry, another quick question :).

Am I right in saying that the name displayed on the desktop icon is the label? (not the "Data" that I used to mount). If so, is it easy to change from "DATA" to "Data"?

:)

---

### Post by taurus on 2008-01-27
Yes, the name that you see below the icon is the label.  If you want to change it, you can do it in Linux but it may be easier for you if you do it from windows.

---

### Post by Graham1 on 2008-01-27
> **taurus said:**
> Yes, the name that you see below the icon is the label.  If you want to change it, you can do it in Linux but it may be easier for you if you do it from windows.

Doing so in Windows won't loose any data on this partition when I enter back into Ubuntu? Will it just appear renamed?

:)

---

### Post by taurus on 2008-01-27
As long as you don't delete anything, format the partition, or change it, it should be fine when you boot back into Ubuntu.  But if you are a little nervous about doing it, then just live with DATA instead of Data, I guess.

---

### Post by Graham1 on 2008-01-27
Done. Thanks again and I'll let you have a rest now (untill my next problem).

Cheers

:)

---

