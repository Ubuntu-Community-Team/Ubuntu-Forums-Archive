---
title: "Shutdown problems"
date: 2008-05-06
forum: General Help
---

### Post by crow_se on 2008-05-06
Hello all
since my freezing problems with 7.10 and 8.04 I have reverted to 7.04.
I installed this 2 days ago using wubi.
Today, with no changes to the system I have suddenly started having 
shutdown problems. I select shutdown from the panel, I get a black screen with Ubuntu in the middle, and this changes to a black screen with the
following text :

Unmounting temporary filesystems    [ok]
Deactivating swap                   [fail]
Unmounting local filesystems
  can't link lock file /etc/mtab~ : read-only file system
        (use -n flag to override)              [fail]

followed by the following 3 lines :
/etc/init.d/rc:2:/etc/rc6.d/S60mountroot: input/output error
/etc/init.d/rc:2:/etc/rc6.d/S90reboot: input/output error
/etc/init.d/rc:2:/etc/rc6.d/S99killntfsrg: input/output error

and the system just hangs. I have to power off to shut down.

Can anyone help ?
TIA
Stuart

---

### Post by RJARRRPCGP on 2008-05-09
You may have bad sectors on your hard disk drive. Sorry. :(

Go to [http://www.hddguru.com](http://www.hddguru.com) and get MHDD, then make a boot CD, get the MHDD 4.6 ISO.
Then when MHDD is booted, type "scan" and then press the F4 key to scan the hard disk drive for defects. 

You may be required to replace the hard disk drive, because you gotten I/O errors.

---

