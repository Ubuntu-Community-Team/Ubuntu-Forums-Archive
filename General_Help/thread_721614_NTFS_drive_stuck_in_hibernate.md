---
title: "NTFS drive stuck in hibernate"
date: 2008-03-11
forum: General Help
---

### Post by Alarindris on 2008-03-11
Been having a heck of a time trying to get my NTFS drive mounted.

```
sudo ntfsfix /dev/sda1
```

returns

```
Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
Remount failed : No such file or directory

```

```
sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force
```

returns (and this is the problem)

```
Hibernated non-system partition, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, so mounting could be done safely.
```

fstab shows 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=2e87ebfa-7c7d-4224-8315-089956dd5e7b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=8C84D1A984D19654 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=8444ABB144ABA500 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=613ba121-cd5f-4a4a-ba26-9320495e5918 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#/dev/sda1 	/media/windows  ntfs-fuse auto,gid=1001,umask=0002 0 0
```

You can see in fstab I tried fuse, but no luck.

What is "properly shutting down windows?"  I've gone back in, shut down, restarted, logged off and then shut down... tried all that.  Hibernation has always been disabled on my PC and I've never knowingly used it. I've gone so far as to disabling the drive in windows, didn't help either.  Note that it functions properly in XP.

Also, when I look in /dev sda1 is 34.5 MB when it's actually a 500GB drive, no other partitions.

Help meh!

Thanks in advance to any responses.

---

### Post by Alarindris on 2008-03-11
Just logged in and out of windows again to see if that worked, still no luck.  Any insight?  This is the only thing I have to get working and I'll be ms free!

---

### Post by sammywham on 2008-03-11
try installing ntfs configuration tool from add/remove and enable and disable internal
what does it say?

---

### Post by Alarindris on 2008-03-11
Tried that too, I get the exact same error message "in hibernate, restart windows etc."

---

### Post by sammywham on 2008-03-11
never mind have you changed any of the shut down options on windows?

---

### Post by Alarindris on 2008-03-11
Shutdown options... not even aware of any.  Haven't changed them in any case.  BTW, the XP install is fresh, I only reinstalled it to *try* and get my drive back.  XP is up to date though.

---

### Post by sammywham on 2008-03-11
it looks like you have errors in the mount of your ext3 filesystem drive

---

### Post by Alarindris on 2008-03-11
Hm ok.  How did you come to that conclusion?  And what would my next step be?

---

### Post by sammywham on 2008-03-11
UUID=2e87ebfa-7c7d-4224-8315-089956dd5e7b /               ext3    defaults,errors=remount-ro 0       1 
is shown above and It doesnt look good

---

### Post by sammywham on 2008-03-11
In Windows can you see the 500 gigs?

---

### Post by sammywham on 2008-03-11
if you can back up files on that drive 
Also install gparted and see if you can see the 500 gigs perhaps unallocated

---

### Post by Alarindris on 2008-03-11
yep, i can see the 500GB in windows.  So you're saying back it up and wipe it out?

---

### Post by Alarindris on 2008-03-11
yep, i can see the 500GB in windows.  that line is not an error, not sure what you're talking about.

---

### Post by sammywham on 2008-03-11
mabye can you mount the drive with the windows installation in linux

---

