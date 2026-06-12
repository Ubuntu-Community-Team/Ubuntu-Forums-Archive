---
title: "How do we turn off the &quot;100 gb media&quot;-like names in hardy?"
date: 2008-04-29
forum: General Help
---

### Post by descentspb on 2008-04-29
This is annoying, it was better when the drives had their unique names!

---

### Post by Julius on 2008-04-29
> **descentspb said:**
> This is annoying, it was better when the drives had their unique names!

That's because those volumes don't have names. They are ntfs volumes, right? Those are the ones that dont have names on my computer the osx86 ones have their name on nautilus. 
Go to windows and change the volumes names there, luckily that will do the trick

---

### Post by descentspb on 2008-04-29
No, in Hardy all of the mounted media have their sizes instead of names (even the ext3 partitions). When i boot up into gutsy it's ok. Maybe those partitions do not have any names, but in gutsy it was convinient, that the names originated from the name of the corresponding mountpoint.

---

### Post by jespdj on 2008-04-29
I'm running Hardy on a Lenovo T61 laptop. It also has a Windows XP (NTFS) partition, which does have a volume name.

I see the volume name, and not "X GB media".

---

### Post by descentspb on 2008-04-29
Well, i can not check it now, but it seems that NTFS volumes have their real names in Hardy. But the others, ext3 volumes are called in the "X GB media" way, despite the names of the mount points.

---

### Post by kpkeerthi on 2008-04-29
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
Works for non-USB partitions too.

---

### Post by descentspb on 2008-04-29
Thanks! I'll try that. But, fairly, it seems like a nautilus option was added to hardy. This is a workaround, what you suggested, but i would like to simply turn it off.

---

### Post by Julius on 2008-04-29
> **descentspb said:**
> Well, i can not check it now, but it seems that NTFS volumes have their real names in Hardy. But the others, ext3 volumes are called in the "X GB media" way, despite the names of the mount points.

Really?

I have two ext3 partitions, one mounts at / and the other at /home

Nautilus shows other 4 partitions: leopard, data (both HFS, I think) and xxxGB media and yyyGB media. Which are the name-less NTFS partitions. Even on windows they dont have a name, although windows assigns drive letters to them. But it doesnt show the extra ext3 partition, because it's already at /home. Perhaps it is because it is not mounted automatically? 

I'm not sure if you can put a name to the partition using gparted, maybe you can!

---

### Post by Julius on 2008-04-29
What he suggested is not a workaround really. Nautilus will show the volume name as per the file system specifications, if there's no name it will just identify the volume by its size. If you want a name to be displayed, then set a name to the volume. It's not workaround or "make-up" thing, since any other operating system capable of recognizing those volumes will also see the name change.

---

### Post by descentspb on 2008-04-29
> **Julius said:**
> What he suggested is not a workaround really. Nautilus will show the volume name as per the file system specifications, if there's no name it will just identify the volume by its size. If you want a name to be displayed, then set a name to the volume. It's not workaround or "make-up" thing, since any other operating system capable of recognizing those volumes will also see the name change.

Ok, let's assume this is not a workaround, whatever. The situation is the following:
i have a nameless ext3 partition, which mounts in /media/ultra. In Gutsy nautilus calls the partition ultra (or whatever i set in /etc/fstab). But in Hardy it is called "350 gb media" and is still mounted into /media/ultra. As soon as i usually access this partition through /media/ultra (using all other software), I want it to be called "ultra" regardless of it being nameless. So i just want this feature back and i was asking of how to get this option turned on again, not how to give a name to a partition, though maybe it is even a nicer decision.

---

### Post by Julius on 2008-04-29
places > computer
right click on the volume > properties

and change the name there?

---

### Post by descentspb on 2008-04-29
> **Julius said:**
> places > computer
right click on the volume > properties

and change the name there?

No, this allows you only to change the mountpoint, not the paritition name. Just the same as editing /etc/fstab

---

### Post by verbage on 2008-04-29
We talked about this a few days ago.  It seems to be a known bug, but has been assigned a low priority.  Check out the following thread for more details:

[http://ubuntuforums.org/showthread.php?t=766167]("http://ubuntuforums.org/showthread.php?t=766167")

---

### Post by Julius on 2008-04-29
Not sure why it is considered a bug, it clearly isn't. It's more like a discussion about what people prefer. Perhaps the best way would be to mimic Mac OS X. OS X reads the volume names, and when there's no volume name set, it just says "Untitled". If there are more than one, it says "Untiled" "Untitled 2" and so on. 
Windows does the same thing too, it will display "Local disk" if there's no volume name set, although on windows you have the drive letters.

If you really want the [100gb media] gone, label the partition. It's hardly a workaround since that's the way it works now, instead of sda, sdb, etc. Although in that link you provided, apparently people want something like "100gb media (sda)".

---

### Post by funnypanks on 2008-04-29
> **kpkeerthi said:**
> [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
Works for non-USB partitions too.

worked perfectly...remember to reboot. remounting doesnt work.

---

### Post by verbage on 2008-04-29
Well, it is a bug according to Ubuntu's very own documentation.  See the following link about "DesktopVolumesRepresentation" where they explicitly spell out what *they* want the behavior to be.  And since what happens is not the prescribed behavior *they* prefer, well, it's considered a bug.  Here's the "DesktopVolumesRepresentation" link:

[https://wiki.ubuntu.com/DesktopVolumesRepresentation]("https://wiki.ubuntu.com/DesktopVolumesRepresentation")

---

### Post by dnairb on 2008-04-29
In terminal, type:

```
sudo blkid
```

If the drives/partitions have names or labels, it should ouptut something like:

> /dev/hda2: UUID="dff9fd76-7280-4cae-a449-84f6fd37c5d9" SEC_TYPE="ext2" TYPE="ext3" LABEL="Home"

If no label is specified, use:

```
sudo e2label /dev/**whatever** **label**
```

Where /dev/**whatever** is /dev/sda1, /dev/sda2 or whatever the partition is, and **label** is the name you wish to give it. **sudo** is necessary to label the root partition, I believe.

Then remount the partition or reboot.

---

