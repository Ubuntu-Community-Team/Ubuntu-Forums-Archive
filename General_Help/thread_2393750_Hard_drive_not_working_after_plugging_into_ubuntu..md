---
title: "Hard drive not working after plugging into ubuntu."
date: 2018-06-07
forum: General Help
---

### Post by coffeenight on 2018-06-07
I am unable to access my hard drive after I plugged it into a laptop  with freshly installed ubuntu. Following was the error message


[I]Error  mounting /dev.sdb1 at /media/tanya/Seagate Backup Plus Drive:  Command-line mount -t "ntfs" -o  "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1"  "/media/tanya/Seagate Backup Plus Drive" exited with non-zero exit  status 13:Error reading bootsector: Input/output error
 Failed to sync device /dev/sdb1: Input/output error
Failed to mount '/dev/sdb1':Input/output error
NTFS  is either inconsistent, or there is a hardware fault, or it's a  SoftRAID/FAKERAID hardware. In the first case run chkdsk /f on Windows
then  reboot into Windows twice. The usage of the /f parameter is very  important! If the device is a SoftRAID/FakeRAID then first activate it  and mount a different device under the /dev/mapper/ directory, (e.g.  /dev/mapper/nvidia_eahaabcc1).Please see the 'dmraid' documentation
for more details.[/I]

The hard drive was perfectly fine before this but now I am unable to access it. Please help.

---

### Post by Autodave on 2018-06-07
I am confused here. Are there now 2 HDs in your laptop? If so, what is on each of them?

---

### Post by coffeenight on 2018-06-07
Oh no. I plugged in an external 1tb hard drive in my laptop. That's when  I encountered the error. After the above error, I am unable to access  my external hard drive in any other computer. This hard drive was  perfectly fine before this.

---

### Post by #&amp;thj^% on 2018-06-07
Do you have a Windows install to check with? To view if files show there.

---

### Post by coffeenight on 2018-06-07
Yes, I am not able to access it in windows as well. I mean it's showing  something is connected in windows and I can safely remove it as well.  But I can't access anything.

---

### Post by #&amp;thj^% on 2018-06-07
> **coffeenight said:**
> Yes, I am not able to access it in windows as well. I mean it's showing  something is connected in windows and I can safely remove it as well.  But I can't access anything.

Gosh I'm sorry to hear this. :(
One more thought for me but from the **Windows machine** have you tried a repair with "chkdsk " it might need a extra option added to "chkdsk" like "/f" but I just don't know for sure but a chkdsk should give you some more information.
And possibly a fix. Fingers Crossed. :)

---

### Post by dragonfly41 on 2018-06-07
From Windows you can run testdisk (win version) to inspect your external drive.

Also from Windows you can install R-Linux (win version) to inspect files in your external drive (ext4 format).

---

