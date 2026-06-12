---
title: "Unable to read external hard disk"
date: 2013-01-19
forum: General Help
---

### Post by m_dk29 on 2013-01-19
I am unable to read my external SATA that is in hard drive enclosure. Formatted to EXT3. It's connected via USB. When i try to access, iam receiving below error.

I tried fsck but it's going on for 15hrs with no result and i had to terminate it. I hear the disk spin randomly when using fsck

Help me resolve the issue.
> 
Error mounting /dev/sdb1 at /media/xxxxx/SAMSUNG 1.5TB: Command-line `mount -t "ext3" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/xxxx/SAMSUNG 1.5TB"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
dmesg output

> 
$ dmesg | tail
[17081.968093] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[17081.968096] sd 11:0:0:0: [sdb]  
[17081.968098] Sense Key : Medium Error [current] 
[17081.968103] sd 11:0:0:0: [sdb]  
[17081.968107] Add. Sense: Unrecovered read error
[17081.968110] sd 11:0:0:0: [sdb] CDB: 
[17081.968112] Read(10): 28 00 00 00 28 18 00 00 08 00
[17081.968123] end_request: critical target error, dev sdb, sector 10264
[17081.968174] EXT3-fs error (device sdb1): ext3_get_inode_loc: unable to read inode block - inode=8, block=1027
[17081.969193] EXT3-fs (sdb1): error: no journal found


---

### Post by dabl on 2013-01-19
dmesg is showing that the ext3 filesystem is broken.  If "e2fsck -pvy" cannot repair it, then you are done with it.

The hard drive itself may or may not be failing.  Running the smartmon long test should answer that question.

---

