---
title: "&gt;.&lt; Goofy Usb Problem!"
date: 2008-01-25
forum: General Help
---

### Post by LdrJagMan on 2008-01-25
ok i have a sandisk cruzer 2.0gb u3 that will NOT mount under Ubuntu 7.04... but a few days ago it did mount... and then yesterday it diden't... i have searched all over this forum for a solution and i havent got it... the biggest resent thing i have done is ran: sudo apt-get autoremove...but that may not be it...
What solution i am looking for is my flashdrive to mount without a second thought when i plug it in... and have device manager pop up and say I can see my Ultmat3 partition of the drive...

and before you ask heres the desmg | tail

[  195.228000] sdb: Write Protect is off
[  195.228000] sdb: Mode Sense: 03 00 00 00
[  195.228000] sdb: assuming drive cache: write through
[  195.236000] SCSI device sdb: 3999744 512-byte hdwr sectors (2048 MB)
[  195.236000] sdb: Write Protect is off
[  195.236000] sdb: Mode Sense: 03 00 00 00
[  195.236000] sdb: assuming drive cache: write through
[  195.236000]  sdb: unknown partition table
[  195.244000] sd 2:0:0:0: Attached scsi removable disk sdb
[  195.244000] sd 2:0:0:0: Attached scsi generic sg2 type 0

I wish for help...

---

### Post by LdrJagMan on 2008-01-25
Bump for some veiws

---

### Post by LdrJagMan on 2008-01-25
People of ubuntu forums... problem has moved to defcon 3. i repete defcon 3!
any USB storage device wont mount!!!!

---

### Post by dcstar on 2008-01-25
> **LdrJagMan said:**
> ok i have a sandisk cruzer 2.0gb u3 that will NOT mount under Ubuntu 7.04... but a few days ago it did mount... and then yesterday it diden't... i have searched all over this forum for a solution and i havent got it... the biggest resent thing i have done is ran: sudo apt-get autoremove...but that may not be it...
What solution i am looking for is my flashdrive to mount without a second thought when i plug it in... and have device manager pop up and say I can see my Ultmat3 partition of the drive...

and before you ask heres the desmg | tail

[  195.228000] sdb: Write Protect is off
[  195.228000] sdb: Mode Sense: 03 00 00 00
[  195.228000] sdb: assuming drive cache: write through
[  195.236000] SCSI device sdb: 3999744 512-byte hdwr sectors (2048 MB)
[  195.236000] sdb: Write Protect is off
[  195.236000] sdb: Mode Sense: 03 00 00 00
[  195.236000] sdb: assuming drive cache: write through
[  195.236000] ** sdb: unknown partition table**
[  195.244000] sd 2:0:0:0: Attached scsi removable disk sdb
[  195.244000] sd 2:0:0:0: Attached scsi generic sg2 type 0

I wish for help...

You need to run an** fsck** on it, it is either corrupted or the partition has been deleted.

---

### Post by LdrJagMan on 2008-01-29
!!!! my support for vfat is GONE!! it thinks that all drives connected to it HAS to be ext 2 or 3... 
****!

---

