---
title: "flash disk permission problem!!!!!"
date: 2007-02-09
forum: General Help
---

### Post by i_pod25 on 2007-02-09
when i insert my flash disk into the usb port thing and i try to delete or save a file on to it...it wont let me and says i dont have permission to do so....



can someone please help me


thanx

---

### Post by Paerez on 2007-02-09
It may be formatted in NTFS. The easiest way to fix it is to copy everything off, format it to FAT32, and then copy stuff back. Then it will work seamlessly in Windows, Mac, and Ubuntu and all other linux.

---

### Post by DagMan on 2007-02-09
Edit:  If that isn't the case, that it's NTFS... this is what I did.

I made an entry in the fstab file to define a folder specifically where the usbstick will mount.  In my case the folder is /media/usbstick

Then with mounted I did this
```
sudo chown user:user /media/usbstick
``` to make it owned by me and not the root user.
'user' is my username so substitute your username there.

If you haven't added an entry to define where external media mounts, a folder is created inside of /media and likely it even called usbstick or usbdrive.  Try that though, without explicitly telling it where to mount something... just let it mount and then do that to the folder that is created
```
sudo chown yourusername:yourusername /media/NameOfFolder
```

If that doesn't do anything or does do something but isn't permanent, perhaps if you post the output of the following commands then someone can be more helpful.


```
cat /etc/fstab
```

then with the stick mounted:
```
mount
```

---

### Post by i_pod25 on 2007-02-09
> **Paerez said:**
> It may be formatted in NTFS. The easiest way to fix it is to copy everything off, format it to FAT32, and then copy stuff back. Then it will work seamlessly in Windows, Mac, and Ubuntu and all other linux.

how do  reformat it?

---

### Post by DagMan on 2007-02-09
```
sudo apt-get install gparted
```
insert the usbstick
```
sudo gparted
```
now find the USB stick in the drop down menu.  sda or sdb or something.  You'lle be looking at a graphical representation of the hard drive or usb drive depending  upon what you selected from the drop down menu.  Make sure you feel comfortable that you're looking at your usbstick.
right click on the graphical representation of the stick and select to unmount it.  If this doesn't work then try unmounting it at the desktop.

Now you can look at the options to format it.  Fat32 will allow you to store files for both windows and linux.

I've had to mess around with mine before and delete the partition then format while making sure it was unmounted as it would remount when the partitioner was done.  Just be careful that you have selected and are looking at your usb disk and not your hard drive.


I don't know if windows will let you select fat32, it's been a long time for me, but if so then you'de format it in windows by mounting it and then in my computer right clicking and selecting format.  After that perhaps it will let you select the filesystem type so you aren't stuck with NTFS

---

### Post by i_pod25 on 2007-02-09
> **DagMan said:**
> ```
sudo apt-get install gparted
```
insert the usbstick
```
sudo gparted
```
now find the USB stick in the drop down menu.  sda or sdb or something.  You'lle be looking at a graphical representation of the hard drive or usb drive depending  upon what you selected from the drop down menu.  Make sure you feel comfortable that you're looking at your usbstick.
right click on the graphical representation of the stick and select to unmount it.  If this doesn't work then try unmounting it at the desktop.

Now you can look at the options to format it.  Fat32 will allow you to store files for both windows and linux.

"I've had to mess around with mine before and delete the partition then format while making sure it was unmounted as it would remount when the partitioner was done.  Just be careful that you have selected and are looking at your usb disk and not your hard drive.


I don't know if windows will let you select fat32, it's been a long time for me, but if so then you'de format it in windows by mounting it and then in my computer right clicking and selecting format.  After that perhaps it will let you select the filesystem type so you aren't stuck with NTFS


i tried and it came up with this 

"The following operation could not be applied to disk:

Format /dev/sda1 as fat32

See the details for more information"

---

### Post by i_pod25 on 2007-02-09
when i try to change the premission, it says its on a "read only disk" :(  i dunno wat that means.....

---

### Post by DagMan on 2007-02-09
> when i try to change the premission, it says its on a "read only disk"  i dunno wat that means.....
Do you mean when partitioning or when trying to change partitions like in my first post?  Also, don't these sticks sometimes have a write protect switch on them... maybe it could be that.



I've just tried it out again on one of mine in gparted.  It was a pain.

Inevitably I think it went down like this:
I had to mount the stick, start gparted, select the stick, right click and select to unmount (inside gparted, not the desktop), delete the partition.  Close gparted, remove the stick, reinsert the stick, start gparted again, select the stick, and create a fat32 partition... actually I first made it a linux-swap filesystem but likely this and all the following wasn't necissary, then closed gparted, then pulled the stick out again then reinserted it again, the started gparted again then selected the usbstick again, then right clicked and selected swap-off (I think it said that it already was off) then converted it to fat32.

The danger I guess would be deleting the partition and then still being unable to create a filesystem.

I'd feel weary about using those instructions if I was someone else even though I feel fine that if I screw around long enough I'll get it right so long as I don't touch my hard drive (which has 10 partitions so it's pretty obvious when I look at it for me personally).  If you don't feel comfortable trying that, then I'm fairly certain that there is a much, much simpler way to do this at the command line, if all else fails, and someone may come along with the answer.

---

### Post by i_pod25 on 2007-02-10
> **DagMan said:**
> Do you mean when partitioning or when trying to change partitions like in my first post?  Also, don't these sticks sometimes have a write protect switch on them... maybe it could be that.



I've just tried it out again on one of mine in gparted.  It was a pain.

Inevitably I think it went down like this:
I had to mount the stick, start gparted, select the stick, right click and select to unmount (inside gparted, not the desktop), delete the partition.  Close gparted, remove the stick, reinsert the stick, start gparted again, select the stick, and create a fat32 partition... actually I first made it a linux-swap filesystem but likely this and all the following wasn't necissary, then closed gparted, then pulled the stick out again then reinserted it again, the started gparted again then selected the usbstick again, then right clicked and selected swap-off (I think it said that it already was off) then converted it to fat32.

The danger I guess would be deleting the partition and then still being unable to create a filesystem.

I'd feel weary about using those instructions if I was someone else even though I feel fine that if I screw around long enough I'll get it right so long as I don't touch my hard drive (which has 10 partitions so it's pretty obvious when I look at it for me personally).  If you don't feel comfortable trying that, then I'm fairly certain that there is a much, much simpler way to do this at the command line, if all else fails, and someone may come along with the answer.



:S:S:S

everytime i try to change it to fat 32  it comes up with this :S

"The following operation could not be applied to disk:

Format /dev/sda1 as fat32"




please help someone....anyone...

---

### Post by i_pod25 on 2007-02-10
bump......

---

### Post by DagMan on 2007-02-10
Perhaps trying just a regular fat filesystem instead of fat32.  Success with this will depend upon the size of the storage device.  fat32 has a minimum size of 260 megabytes so if you have a 256 or smaller stick you should use a fat filesystem.

If that isn't the problem then using the fdisk utility at the command line will be the way to go.  I recommend reading the fdisk manual or googling for a simpler guide and perhaps you can find one for just your same issue.  For a really short and incomplete summary... This would be with the stick unmounted.
type
fdisk device
for example 'fdisk /dev/sda'
if /dev/sda is what your usbstick is.  On my computer it's sdb.
at the fdisk prompt type m for help
if you list the filesystem types, fat16 is the 'fat' filesystem if you have a disk less than 260 megabytes and would be using that.

Since you reckon this stick was formatted with NTFS, I'm guessing that you have access to a windows computer.  Have you tried looking to see what the ability is with windows with this?  It might create a fat or fat32 filesystem with an easier point and click interface since they are Windows filesystems afterall.  I don't myself know what XP's support for this is.

---

