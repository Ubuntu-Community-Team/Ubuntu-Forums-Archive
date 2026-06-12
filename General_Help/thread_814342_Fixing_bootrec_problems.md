---
title: "Fixing bootrec problems"
date: 2008-05-31
forum: General Help
---

### Post by fearful on 2008-05-31
I'm having problems getting back to my Vista partition as default. I'm trying to fix my bootrec. I have an HP DV6000 series and I started my computer through the recovery partition and used the command ' bootrec.exe /FixMBR ' in the command prompt. Now the computer loads the Recovery Partition as my default OS and can't really do anything. If I use the Ubuntu live CD it says that my Vista Partition cannot be mounted because it wasn't shutdowned properly. Please help I really need to get back to my Vista.

---

### Post by lswest on 2008-05-31
if you run ```
bootrec /fixboot
``` it should add the right entries to the vista bootloader again so it starts the OS first and not the recovery partition.

---

### Post by fearful on 2008-05-31
I have tried that too and no luck still booting the HP Recovery partition as default :(

---

### Post by lswest on 2008-05-31
try running a chkdsk /f on the vista partition from the recovery partition.  There may be an error on the disk.

---

### Post by fearful on 2008-05-31
Here's what it says

> This type of file system is NTFS.
Cannot lock current drive.
Windows cannot run disk checking on this volume because it is riht protected.

---

### Post by fearful on 2008-05-31
When I do ' chkdsk /c ' which is where my vista files is it says that it is being used by another process 'chkdsk' maybe this is the problem?

---

### Post by fearful on 2008-05-31
Whats weird too is that when I run the Ubuntu Live CD it says that on my 129 GB partition (Vista) only 3200 MB are in use which is not true...

---

### Post by lswest on 2008-06-01
It seems to me your Vista partition is corrupted, or it was messed up during a hard reboot.  does ```
chkdsk /r C:
``` work for you in the recovery console of the vista recovery partition? (last time we left out the drive argument)

---

