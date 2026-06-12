---
title: "Refining USB HD automount"
date: 2008-03-15
forum: General Help
---

### Post by Crusty Juggler on 2008-03-15
I've been working on bringing my two external FAT32 USB drives back from various states of non-functionality and I've mostly been successful, but it's a little ugly.  

I've made sda1 and sdb1 directories in /media to facilitate automounting, and these are persistent in my Places sidebar on the file browser.  When I plug one of my drives in, it automounts on the desktop correctly as STORAGE but also opens up a "sda1 - File Browser" instead of "STORAGE - File Browser," like it is mounted twice.  

The other drive does not automount when plugged in, but if I browse sdb1, it works.  Additionally, this drive has a * under the boot column in fdisk -l.

Maybe I'm being too picky, but I would like both of these drives to automount correctly when plugged in with STORAGE and SEA_DISK on the Desktop rather than having to go through the browser and finding sda1 and sdb1 or having one mount twice.  My wife uses this computer and is going to act like she is incapable of figuring that out.  

And, yes, I have the right boxes ticked under Removable Media! :lolflag:

---

### Post by chewearn on 2008-03-15
Set the disk label to STORAGE, if you want the disk to mount under /media/STORAGE.

---

### Post by ibuclaw on 2008-03-15
Creating an fstab line for your device could probably fix that.

fstab, in easy to understand terms, is Linux's way of handling Storage Devices plugged in your system consistently. ie: your root partition is always the root partition because of it.

So how do we go about adding it? enter in this in the command line.
```
 sudo gedit /etc/fstab & 
```

and entering something like this at the bottom of your text file:
```
 /dev/sda1 /media/sda1    vfat    defaults,umask=007,gid=46 0       1 
```

To walk you through it:
   /dev/sda1 = Your device location.
   /media/sda1 = Your mount point.
   vfat = Your partition format.
   defaults,umask... = Ubuntu's default settings to give you read/write acces to your NTFS partition, so why not have the same for you FAT partition too?
and finally 0 1 is to do with loading/unmounting/testing at boot/shutdown time. (Or something like that).

NOTE: change the upper code in accordance to your device setup.

For more info type in
```
 man fstab 
```
in the Terminal.

But since I presume that these devices are going to be in and out your computer day in day out, I suggest having LABEL=STORAGE instead of /dev/sda1. So that fstab line is consistant with that one device, and not just any odd device that may take the place of the /dev location.

Hope this sheds some light on the situation.

Iain

---

