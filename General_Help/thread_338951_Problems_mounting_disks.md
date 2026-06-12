---
title: "Problems mounting disks"
date: 2007-01-15
forum: General Help
---

### Post by samden on 2007-01-15
I have a dual-boot OSX / Xubuntu dapper iMac G3 500Mhz. I have a 20GB hard drive with a 9GB OSX partition, 7.5GB Xubuntu partition, and 1.5GB shared hfs+ partition.

I am having problems mounting my shared partion, cds and USB pen drives.

Shared partition:
This will work fine now, after a lot of tinkering(!), except I cannot get it to mount at startup. Every time I start up I must enter "sudo mount /dev/hda12" to mount the partition.

/etc/fstab

Code:
```
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda13      /               ext3    defaults,errors=remount-ro 0       1
/dev/hda14      none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda12      /mnt/share      hfsplus  user,noauto   0       0
```CDs and USB pen drives:
These I can access only as root. If I attempt to mount a pen drive or cd through thunar normally, I get the error:

"Error: could not execute pmount."

If I open thunar as root through a terminal, I can mount these drives without any problems.

If anyone has any suggestions to try I would be very grateful.

PS: I have had a duplicate thread running in the PPC section for a few days with no response, in case you have read this before. I have moved to this section for a wider audience. Thanks.

---

### Post by samden on 2007-01-15
OK, I don't know what I've done now, but now neither my cd drive nor my flash drive show up in Thunar (file manager) at all. Normally they appear as little disk icons in Thunar and on the desktop, now they don't exist.

My cd drive shows up in the /media folder, and when I add the "mount devices" button to the panel it shows up in this as well.

My USB drive does not show up anywhere at all. Now this is very frustrating - formerly I could access it through roundabout means, now I cannot find it at all, and I need it for my work.

I have reinstalled Firefox and made a few changes using bum to speed things up, not sure what I might have done that would have upset it. I was mainly following instructions on [http://ubuntuforums.org/showthread.php?t=62650&highlight=ubuntu+low+ram+computers](http://ubuntuforums.org/showthread.php?t=62650&highlight=ubuntu+low+ram+computers) :-?

---

### Post by samden on 2007-01-15
Further analysis:

"lsusb" shows the flash drive is recognised (at Bus 001 Device 005: ID 0457:0151)

"dmesg | tail" shows a number of things, unfortunately I am not posting this from the machine in question so cannot copy and paste. Basically it:
-Recognises the drive as sdb
-outputs at the end
```
sdb: sdb1
sd 1:0:0:0: Attached scsi removable disk sdb
sd 1:0:0:0: Attached scsi generic sg0 type 0
usb-storage: device scan complete
```

sudo mount /dev/sdb /media/usb         &
sudo mount -t auto /dev/sdb /media/usb           both return:
```
mount: you must specify the filesystem type
```

sudo mount -t FAT /dev/sdb /media/usb           returns:
```
mount: unknown filesystem type 'FAT'
```
This is the same when specifying filesystems "FAT32", "fat", or "fat32" instead of "FAT"

EDIT:
sudo mount /dev/sdb1 /media/usb 
worked and mounted the drive. So this seems ok now.

But still neither my cd drive or usb stick show up on the desktop or in the sidebar in Thunar, I must just find them in the /media directory. I am not sure what this is about. Something still is fishy, but at least I can access the data on my usb drive for now.

The usb drive is owned by root and I don't have read/write access to it still unless I open Thunar as root, so this still needs to be solved.

I have selected "Enable access to external storage devices automatically" in the user settings for myself, but this does not seem to change anything.

---

### Post by jackocleebrown on 2007-01-15
Hi Samden,

Not Xubuntu user so I'm afraid I can't help with your Thunar problem... but I believe that the reason you are having to "sudo mount /dev/hda12" every boot is because of the "noauto" option in fstab, try replacing it with "auto".

Hope you get some answers to the rest of your troubles!

Jack.

---

### Post by samden on 2007-01-18
Thanks for that, now my shared drive and cd drive are automounting!

So now:
- Shared partition is automounting and working fine.
- CDs are automounting, just not showing up on desktop.

Remaining issues:
- Getting USB drive to mount automatically on insertion
- Changing permissions of USB drive to user rather than root
- Getting drives to show up in Thunar and on the desktop

If anyone has any thoughts on these issues I would be grateful.

---

### Post by samden on 2007-01-18
What configuration files control how Ubuntu deals with USB drives? If I know what files could be involved, I can then try and work out whether the settings are correct or not.

---

### Post by samden on 2007-01-29
Problem solved!

I had tried to use xdm instead of gdm as my login manager - I did not realise that gdm was automounting everything for me. Switched back to gdm and everything is now fine! :D

---

