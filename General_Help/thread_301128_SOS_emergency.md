---
title: "SOS: emergency"
date: 2006-11-16
forum: General Help
---

### Post by bg11 on 2006-11-16
Hi, 

I recently tried to follow a ubuntu tutorial on partition labels ([how to fstab]("http://ubuntuforums.org/showthread.php?t=283131")), I ran the mke2fs -j command on an USB hard drive partition to give it a label.  But this made my data, all 100GB of it, on that partition disappear! :( 

So, google pointed to a program called testdisk to help recover the data.  I've ran it and get the following output:

```

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63 
Current partition structure: 
     Partition                  Start        End    Size in sectors 
 1 * HPFS - NTFS              0   1  1  2562 254 63   41174532 
 2 E extended LBA         12749   0  1 38912 254 63  420324660 
 3 P FAT32 LBA             2563   0  1 12748 254 63  163638090
Invalid NTFS boot 
 5 L HPFS - NTFS          12749   1  1 25497 254 63  204812622 
 5 L HPFS - NTFS          12749   1  1 25497 254 63  204812622 
   X extended             25498   0  1 38912 254 63  215511975 
Invalid NTFS boot 
 6 L HPFS - NTFS          25498   1  1 38912 254 63  215511912 
 6 L HPFS - NTFS          25498   1  1 38912 254 63  215511912

```

Partition 5 is the one I ran mke2fs on, I'm not sure how to proceed though, I've found the wiki for testdisk a little confusing :confused: .  I think I have to edit the partition table parameters for partition 5, if this is correct then how do I go about this?

I am a noob so go easy guys.

---

### Post by bg11 on 2006-11-18
Bump.

---

### Post by koenn on 2006-11-18
the mk2fs command you ran is meant to format and label a partition. So you've formatted that partition, and therefore your data is gone.

testdisk seems to me a tool te fix partition tables, not to recover data from a partition. 

look at this thread with a similar problem. No promises, no guarantees. You may have lost those files forever.
[http://www.ubuntuforums.org/showthread.php?t=302022](http://www.ubuntuforums.org/showthread.php?t=302022)

---

