---
title: "ubuntu cant mount hard disk after it was read by mac"
date: 2012-11-10
forum: General Help
---

### Post by graissedeloup on 2012-11-10
Hi all
I m on Ubuntu 11.04. I just lent my hard drive My book 2T to a friend on his mac which could read it, (and didnt formate it) but now my laptop can t mount it. (HPFS/NTFS)
i join the capture of the disk software.
Does anyone know how to do? thanks a lot!!
guilhem

---

### Post by ggeminii on 2012-11-10
What happens when you try to mount it?
What error messages do you get?
try mounting it using terminal:
***sudo mount /dev/sdc1 /mnt***.
Since partition is NTFS boot in windows and run chkdsk on the disk.

---

### Post by graissedeloup on 2012-11-11
thanks for helping me !

when i try to mount it:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

and i checked again: the disk is perfectly read on a mac computer, but no more om my linux one! 
no windows computer here... 
i tried 

sudo ntfsfix /dev/sdb
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.

really lost :confused::confused:

---

### Post by graissedeloup on 2012-11-11
actually i found my solution here:
[http://girliemangalo.wordpress.com/2011/09/](http://girliemangalo.wordpress.com/2011/09/)
thanks again :))

---

