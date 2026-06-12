---
title: "External Harddisk converted to UDF Volume. How to reverse?"
date: 2014-07-20
forum: General Help
---

### Post by sandeep13 on 2014-07-20
I was trying to mount an image file over a usb. From one of forums thread I used this solution:
sudo dd if=/path/to/downloaded.img of=/dev/sdb

I copied the image file from an external HD to my local machine. I didn't unmount the ext HD.
After executing the command my ext HD converted to UDF volume and the image was mounted onto it.

Now I would like to use my ext HD as normal HD. But I am not able to turn it back from UDF volume.
It was a 2TB ext HD having around 1TB of data. Every time I connects it to system it gets mounted as UDF volume. I am not able to access it on window system also. 

Is there some way I can get my data back.

---

### Post by oldfred on 2014-07-20
UDF does not use standard partitions and you totally overwrote the first part of drive with the image.
Do you know exact partition layout before? If so you may be able to manually add partition data to partition table.

If you only had one partition it probably cannot be recovered except using tools that scan drive like photorec or         For NTFS - GetDataBack often recommended
    
Was drive MBR and not gpt partitioned? 

If and only if MBR:
You may be able to zero out current partition table as it has random data written in that area and then use testdisk to restore partitions. But if your data was in first 1GB of drive that is gone.

Do not use dd to copy image to a hard drive, best only if a smaller flash drive.

This will delete both MBR boot code in first 446 and partition table which is approx rest of first sector of hard drive. Be absolutely sure you use correct drive or you then damage another drive. Example shows sdb, but again check that drive is sdb.

       dd if=/dev/zero of=/dev/sdb bs=512 count=1

[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)

      Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Drive will then show as totally unpartitioned or blank drive.

 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

