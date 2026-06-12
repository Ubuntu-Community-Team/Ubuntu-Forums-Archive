---
title: "Failed to open $Secure: Input/output error on NTFS HDD"
date: 2022-08-29
forum: General Help
---

### Post by wr300000 on 2022-08-29
I'm using Ubuntu 22.04 LTS 64bit on Dell E6430.
I connected Seagate HDD thru USB port, drive name can be found but could not be mounted.
Once I run $sudo ntfsfix -n /dev/sdb1 , the response is below messages
Mounting volume... Failed to open $Secure: Input/output error
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
Failed to open $Secure: Input/output error
Remount failed: Input/output error

Could anyone suggest on this please ?

---

### Post by TheFu on 2022-08-30
> **wr300000 said:**
> I'm using Ubuntu 21.10 LTS 63bit on Dell E6430.
 

Support for 21.10 ended in July.
Move to 22.04.  After that, someone may be able to help.  Doing anything on 21.10 is a waste of time.

---

### Post by Holger_Gehrke on 2022-08-30
'ntfsfix' is very limited in what it can do. If it encounters an error that goes beyond what it can repair (and that's most possible errors) it just sets a flag for the file system so that Windows will run chkdsk on the file system the next time it's used. Never use NTFS unless you have access to a Windows machine or it's data you can do without.

Holger

PS: 6**3** bits ? ? ? That's a bit unusual ...

---

