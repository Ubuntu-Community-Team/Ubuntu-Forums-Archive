---
title: "Finding dev to mount"
date: 2007-07-07
forum: General Help
---

### Post by carpetn on 2007-07-07
I have two related questions. Running Feisty Fawn on Lenovo 3000 N100 Dual boot with XP SP2.

First, I inserted a flash drive into my USB slot, but it is not showing up in my file browser. I assume I have to manually mount it, but the question is, how do I identify which dev it is that I should mount? 

 ("Removable Drives and Media Preferences" under System -> Preferences should be mounting it, I think, since the three options under Removable Storage (Mount removable drives when hot-plugged/Mount removable media when inserted/Browse removable media when inserted) are all checked.)

Second, how do I access my NTFS and FAT32 partitions? THey don't seem to be showing up anywhere that I can see.

Thanks.

carpetn

---

### Post by dreadlord_chris on 2007-07-07
> **carpetn said:**
> I have two related questions. Running Feisty Fawn on Lenovo 3000 N100 Dual boot with XP SP2.

First, I inserted a flash drive into my USB slot, but it is not showing up in my file browser. I assume I have to manually mount it, but the question is, how do I identify which dev it is that I should mount? 

 ("Removable Drives and Media Preferences" under System -> Preferences should be mounting it, I think, since the three options under Removable Storage (Mount removable drives when hot-plugged/Mount removable media when inserted/Browse removable media when inserted) are all checked.)

Second, how do I access my NTFS and FAT32 partitions? THey don't seem to be showing up anywhere that I can see.

Thanks.

carpetn

with the USB drive connected, paste the output from the following:
```

sudo fdisk -l

```

---

### Post by carpetn on 2007-07-08
I had tried 'fdisk -l' yesterday, but without 'sudo', since it hadn't struck me that one would need to be root to get that--and it was giving me some info (just the part below starting with "Disk /dev/sdb...").

I did successfully mount the USB drive on the guess that the relevant dev was /dev/sdb. And my question about finding the Windows partitions is also answered by the full "fdisk -l" report. 

What remains them is why Feisty doesn't automatically mount the USB drive (and the Windows drives), given that I have "Mount removable drives when hot-plugged/Mount removable media when inserted" selected under System -> Preferences.

Thanks for the help.


eric@lenovo-1:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        2869     2562367+   c  W95 FAT32 (LBA)
/dev/sda3            9094        9729     5108670   12  Compaq diagnostics
/dev/sda4            2870        9093    49994280    5  Extended
/dev/sda5   *        2870        8833    47905798+  83  Linux
/dev/sda6            8834        9093     2088418+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 262 MB, 262144000 bytes
32 heads, 33 sectors/track, 484 cylinders
Units = cylinders of 1056 * 512 = 540672 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         485      255984    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(254, 31, 33) logical=(484, 27, 5)

---

### Post by dreadlord_chris on 2007-07-08
> **carpetn said:**
> What remains them is why Feisty doesn't automatically mount the USB drive (and the Windows drives), given that I have "Mount removable drives when hot-plugged/Mount removable media when inserted" selected under System -> Preferences.

Thanks for the help.


paste the contents of **/etc/fstab** and I can help you get the Windows partitions to mount automatically at boot.

The USB drive someone else will need to chime in on...

---

### Post by carpetn on 2007-07-09
> **dreadlord_chris said:**
> paste the contents of **/etc/fstab** and I can help you get the Windows partitions to mount automatically at boot.

The USB drive someone else will need to chime in on...

Thanks. Here's the fstab file:
Does this have to be edited by hand or does Gnome have a GUI app to change these setting?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=66f75c8b-13d0-4896-b4ff-a45752169a56 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=b011a167-537d-413d-b942-b4dfcb176a2d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by dreadlord_chris on 2007-07-09
You'll need to edit it by hand.
I need you to paste the output of this command too:
```

ls -l /dev/disc/by-uuid/

```

---

### Post by carpetn on 2007-07-09
> **dreadlord_chris said:**
> You'll need to edit it by hand.
I need you to paste the output of this command too:
```

ls -l /dev/disc/by-uuid/

```


Strange:
eric@lenovo-1:~$ ls -l /dev/disc/by-uuid/
ls: /dev/disc/by-uuid/: No such file or directory


Thanks. Ooops. I do have /dev/disk...

eric@lenovo-1:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2007-07-09 08:27 20F0-B94A -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-07-09 08:27 66f75c8b-13d0-4896-b4ff-a45752169a56 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-07-09 08:27 6A6455B8645587A9 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-07-09 08:27 b011a167-537d-413d-b942-b4dfcb176a2d -> ../../sda6
lrwxrwxrwx 1 root root 10 2007-07-09 08:27 F0B8-105B -> ../../sda2
eric@lenovo-1:~$ 

I didn't know whether having the USB flashdrive plugged in mattered, so I checked the command with it plugged in and the output was the same--or at least appeared the same short of doing a character-by-character comparison.


Thanks again.

---

### Post by dreadlord_chris on 2007-07-09
> **carpetn said:**
> Strange:
eric@lenovo-1:~$ ls -l /dev/disc/by-uuid/
ls: /dev/disc/by-uuid/: No such file or directory


Thanks. Ooops. I do have /dev/disk...

eric@lenovo-1:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2007-07-09 08:27 20F0-B94A -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-07-09 08:27 66f75c8b-13d0-4896-b4ff-a45752169a56 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-07-09 08:27 6A6455B8645587A9 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-07-09 08:27 b011a167-537d-413d-b942-b4dfcb176a2d -> ../../sda6
lrwxrwxrwx 1 root root 10 2007-07-09 08:27 F0B8-105B -> ../../sda2
eric@lenovo-1:~$ 

I didn't know whether having the USB flashdrive plugged in mattered, so I checked the command with it plugged in and the output was the same--or at least appeared the same short of doing a character-by-character comparison.


Thanks again.

oops, sorry about the disk thing...
anyway, what we'll do now is set it up to have your Windows partitions automaticaly mount at boot.
Since one of the partitions is formatted NTFS (sda1) for the moment you will only be able to mount it **read-only** - more on this later.

1. create the mount points for the partitions - I'll call them WindowsFAT & WindowsNTFS, you call them what you want:
```

sudo mkdir /media/WindowsFAT
sudo mkdir /media/WindowsNTFS

```

2. open fstab as *root* to add new mounts:
```

gdesu gedit /etc/fstab

```

3. add the following lines to the bottom of fstab
```

# /dev/sda2
UUID=F0B8-105B /media/WindowsFAT vfat defaults  0 2
# /dev/sda1
UUID=6A6455B8645587A9 /media/WindowsNTFS ntfs defaults  0 2

```
save the file...

Now we'll test it:
```

sudo mount -a

```

if there's no errors from that - you should now have both Windows partitions mounted. The NTFS partition will be mounted **read-only** though. If you would like write access to it you will need to install the **ntfs-3g** package - and change the fstab line from *ntfs* to *ntfs-3g*

---

### Post by marsbt on 2007-07-09
For your USB drive, before plugging it in, use the following command in a terminal and see how the system recognizes the USB disk. It should see it some like /dev/sdc1 or /dev/sdd1 etc.
> ~$ sudo tail -f /var/log/syslog

Plug in the USB disk and see how it recognizes it (the terminal will show you upcoming messages). Then use the following command to mount it

> ~$ pmount /dev/sdc1 (change /dev/sdc1 to as show by log messages). You also might need to install pmount (and pumount to uninstall it)

---

### Post by Rui Pais on 2007-07-09
you can check if your usb drive is been detected and if so what /dev/xxx is been assign you can plug it, wait a few seconds and type:
```
dmesg | tail
``` 

If you are at Gnome, you should check too if you have gnome-volume-manager running.

---

### Post by dreadlord_chris on 2007-07-09
hmmmm....

---

