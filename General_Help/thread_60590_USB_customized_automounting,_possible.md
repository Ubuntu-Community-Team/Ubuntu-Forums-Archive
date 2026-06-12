---
title: "USB customized automounting, possible?"
date: 2005-08-28
forum: General Help
---

### Post by lucifeer on 2005-08-28
Well I noticed that when plugging in my Playstation Portable that it gets automounted and a window pops up and shows me all the files on it.
Now I'd want to change this abit, as it seams I need some special arguments for getting the psp-mount to fully work:
[http://ubuntuforums.org/showthread.php?t=58380&highlight=PSP](http://ubuntuforums.org/showthread.php?t=58380&highlight=PSP)
Now Im not sure what's automaticly mounting it, but Im guessing it's udev somehow. 
And the question is, can I somehow tell the automounter too use special flags for either usb-units or acording to usb-units "ProductID" ?

Also the automounter mounts all vfat-drives using "utf-8" wich apparantly isn't recomended for use with fat-drives:> 
sdb: assuming drive cache: write through
 /dev/scsi/host2/bus0/target0/lun0: unknown partition table
Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 0
usb-storage: device scan complete
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
usb 1-2: USB disconnect, address 2 Any solutions for what's best to use instead? On my harddrives I changed too "iso8859-15" for the time being

---

### Post by ichnation on 2006-05-01
mount /dev/sda1 /media/usb0/ -t vfat  -o uni_xlate=1

---

