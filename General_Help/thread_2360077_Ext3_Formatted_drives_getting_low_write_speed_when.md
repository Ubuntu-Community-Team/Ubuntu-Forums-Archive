---
title: "Ext3 Formatted drives getting low write speed when writing on Windows"
date: 2017-05-01
forum: General Help
---

### Post by jmweathers on 2017-05-01
The small company that I work for has recently switched from formatting drives NTFS to Ext3, due to specifications in the industry we are in. Our main system, however, has to be running Windows. We are currently running Paragon ExtFS in order to read and write to the drives. However, the drives we have reformatted from NTFS are getting incredibly low write speeds (15-20 MB/s). We also recently bought some pre-formatted drives, formatted Ext3 and partitioned the same way that we have ours, and they write much faster, closer to 80-90 MB/s. 

We are formatting drives in Ubuntu 16.04 LTS, using fdisk to create a DOS partition table and formatting with mke2fs.

Does anyone have any idea what might be causing this? If any more information from the system is needed, I can supply.

---

### Post by TheFu on 2017-05-01
What is the performance under Ubuntu?  Some bonnie++ tables would be nice.  
Also, what are the drive models being used? Please clarify which performance goes with which drives under Ubuntu.

For performance issues under non-Ubuntu software, you should work with that project or company.

BTW, most people switched away from EXT3 to EXT4 (or xfs or ZFS) about 10 yrs ago.

---

