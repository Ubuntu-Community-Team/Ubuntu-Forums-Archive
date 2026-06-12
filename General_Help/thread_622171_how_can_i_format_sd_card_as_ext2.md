---
title: "how can i format sd card as ext2?"
date: 2007-11-24
forum: General Help
---

### Post by anubix on 2007-11-24
Hello friends!

I run a linksys wrt54g with dd-wrt firmware.
I have an sd card mod installed.
I need to format the card with an ext2 format.
I have a usb card reader and (obviously) ubuntu.

from what i can tell, i need to:
(sudo su)
umount /media/usbdisk
fdisk /media/usbdisk
(this is where i get stuck)
mkefs.ext2 /media/usbdisk

obviously this isn't working, i can successfully unmount, but when i fdisk it spits out:
You will not be able to write the partition table.
Unable to read /media/usbdisk

what am i doing wrong?
all the information I found referred to /dev/mmcda* which i don't see... am I not looking in the right place?

---

### Post by Pumalite on 2007-11-24
Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it with your card plugged.

---

### Post by rsambuca on 2007-11-24
> **Pumalite said:**
> Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it with your card plugged.

You don't really need the liveCD for this task.  You can just use the regular version on Ubuntu:

sudo apt-get install gparted

---

### Post by Rizado on 2007-11-24
In case /media/usbdisk is the place the card is mounted om run:
```
mount | grep /media/usbdisk
```

Output should be something like this:
```
/dev/sdd1 on /media/usbdisk type vfat (rw,nosuid,nodev,noatime,flush,uid=1000,utf8,shortname=lower)
```

In my case the device path is **/dev/sdd1**

So to format my card to ext2 I'd run:
```
sudo umount /dev/sdd1
sudo mkfs.ext2 -L YOURCHOICEOFLABEL /dev/sdd1
```
Change YOURCHOICEOFLABEL to whatever you want, this is the name the drive will be identified with. When you insert the card it should be mounted on "/media/YOURCHOICEOFLABEL"
It will also be accessible through "/dev/disk/by-label/YOURCHOICEOFLABEL" so you can always be sure you use the right partition no matter how many drives you have connected.

**Make sure you don't copy these commands straight of, it will format /dev/sdd1 and if that's not the drive well then you've lost some data.**

---

### Post by netron on 2008-01-19
i used gparted to format my sd card as vfat.

my card automounts when i plug in my usb card reader, and i can copy files to it.

however, when i unmount the card, unlpug, plug back in and re- automount, the card
shows up as having no files on it - even though i went to the console and used the "cp" copmmand to copy some files across.

( and did an ls to list the files. and then pico somefile.txt to open one of them..)

the bizarre thing is that the sd card seems to be blanking itself anytime i unmount it?!!!

anyone have any idea whats going on?

heres' some info ,if this helps:  (partial output of "mount"):

/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)


thats my sd card.

>/media/disk$ ls -a
.  ..  notes.txt  Result08.txt

>/media/disk$ pico notes.txt

opens up ok. i edit the file. save it.  then "more" the file again.  yes  - my changes have been written to it.

right click on the sd card icon on my desktop -> unmount volume

it unmounts. icon dissapears.

unplug my card reader.

plug in again.  card remounts.  

nautilus pops up automatically , showing me the contents of /media/disk

and the file i just saved and edited (notes.txt) is no longer there!

---

### Post by netron on 2008-01-19
copied a lot of photos over to the card. (theres nothing else on it , as i bought it yesterday)

df -h output:  (after copying):

/dev/sdb1             953M  276M  677M  29% /media/disk

which tells me:  953meg total,  276meg in files,  677meg remaining.  (its a 1 gig card)

ls /media/disk confirms that i have my image files on the card.


unmount card.  remount.

df -h 

/dev/sdb1             953M   32M  921M   4% /media/disk

my 276meg of files has dissappeared!

bizarre.

---

