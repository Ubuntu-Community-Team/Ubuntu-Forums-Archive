---
title: "I have an entry for the hard disk in 'by-uuid'"
date: 2014-09-26
forum: General Help
---

### Post by sim085 on 2014-09-26
Hello,

 I am not sure if this is correct. I have two hard drives on the PC. When I do ls -l /dev/disk/by-uuid I get an entry for each partition on one drive, i.e. - for sda1 and sda2 (but not an entry for the drive itself; sda) and I get an entry for the other drive sdb!! Given I have no partition on sdb. sdb is the hard drive itself and not a partition. Why do I have an entry for sdb here?

Is this normal? If yes why don't I have an entry for sda as well?

---

### Post by oldos2er on 2014-09-26
Can you please show the full output for **ls -l /dev/disk/by-uuid** ?

---

### Post by sim085 on 2014-09-26
```

root@data:~# ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 9 Sep 26 14:08 1d30e230-d903-44ed-8044-492b35de09d9 -> ../../sda0
lrwxrwxrwx 1 root root 9 Sep 26 14:09 4ce5c868-fb6c-4f35-a218-401d85l1676b -> ../../sda1
lrwxrwxrwx 1 root root 9 Sep 26 14:09 e2038fa4-f4e8-48c5-b9de-8a3yyd784ffc -> ../../sdb

```

---

### Post by sim085 on 2014-09-26
All I want to know if this line is normal given that it is the actual hard disk rather than the partition:
```

lrwxrwxrwx 1 root root 9 Sep 26 14:09 e2038fa4-f4e8-48c5-b9de-8a3yyd784ffc -> ../../sdb
```

??

Is there a way to delete this?

---

### Post by yancek on 2014-09-26
When I run the command, I only see partitions.  Interesting that you have /sda0, never seen that before.

---

### Post by sim085 on 2014-09-26
Is it safe to delete the odd one out? Or is there a way to refresh this list?

---

### Post by oldfred on 2014-09-26
Did you format a drive not a partition? Which will lead to major issues.

I have not seen sda0 either.

---

### Post by sim085 on 2014-09-26
> **oldfred said:**
> Did you format a drive not a partition? Which will lead to major issues.

Yes I did! :-| ... but I than re-partitioned and formatted partition. At that point I had sdb and sdb1. Given that I saw sdb1 I deleted the partition hoping it would have removed both sdb and sdb1. However only sdb1 was removed. What are the major issues? Is there a way to fix this?

---

### Post by oldfred on 2014-09-26
I think as long as you have partitions, you will be ok. Not sure how a formatted drive is configured, but those that have those are not able to mount them or really use them. And there is no way then to convert to partitions without losing all data or backup and restore is required.
A formatted drive seems to have random data in the partition table locations, so it looks like a corrupted partition table to any standard partition tools. And almost all utilities require partitions to mount, edit, format or use your data.

---

### Post by sim085 on 2014-09-27
> **oldfred said:**
> I think as long as you have partitions, you will be ok. Not sure how a formatted drive is configured, but those that have those are not able to mount them or really use them. And there is no way then to convert to partitions without losing all data or backup and restore is required.
A formatted drive seems to have random data in the partition table locations, so it looks like a corrupted partition table to any standard partition tools. And almost all utilities require partitions to mount, edit, format or use your data.

I do not mind loosing data on that drive as I am just starting to mount this. When I was formatting to ext4 by mistake I entered /dev/sdb rather than /dev/sdb1. 
```

mkfs.ext4 /dev/sdb # by mistake

```

I realized my mistake and re-created the partition and format this. When I mounted the drive (which I managed) all worked fine. However I could see an entry in the by-uuid folder for /dev/sdb. 

So there is no way to clean this folder? Let us say I remove this drive because I no longer needed? Would I remain with entries in by-uuid folder? 
When I deleted the partition sdb1 the entry in by-uuid for this was removed! I would like to remove the entry for sdb but there is no option to delete drive.

---

### Post by oldfred on 2014-09-27
Not sure where a formatted drive stores that information. But probably in the first part of drive.
Rather than spending the time to zero entire drive you could just zero out first 1MB and see if that works.

Double check that drive is mounted where you think it is before as this erases MBR & partition table and first 1MB of drive.

 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Change sdX to sdb, or sdc whatever your drive is.
      
 dd if=/dev/zero of=/dev/sdX bs=512 count=2

---

### Post by sim085 on 2014-09-27
> **oldfred said:**
>  
 dd if=/dev/zero of=/dev/sdX bs=512 count=2

It does not seem to have worked. After creating a new partition (that covers all the drive) I still have two entries for the drive. One for the partition (sdb1) and one for the drive (sdb). So this uuid information is read directly from the hard disk? Is this why format all drive would solve?

---

### Post by sim085 on 2014-09-27
So just to give a better description of what is happening...

If I create a partition (sdb1) and I use the given command (dd if=/dev/zero of=/dev/sdX bs=512 count=2), then after restart the partition I created disapears from the list in /dev/disk/by-uuid. However the entry for sdb does not disappear! It remains there.

I was wondering from where does /dev/disk/by-uuid get populated? 
Does it make a difference if this hard disk I am using once had Windows installed?

---

### Post by oldfred on 2014-09-27
Is this a gpt partitioned drive? That stores data differently.

And I would expect the dd to erase your partition table as that is in the MBR and the dd command fully erases the MBR which includes both boot code and partition table if MBR partitioned. 

I know that partition table is in MBR, but that is tiny so UUID is not stored in MBR, but the 4 partitions. So each partition has its own data store with added info, but do not know details.

---

### Post by sim085 on 2014-09-29
I had to format all the drive using the following command to get rid of that entry from by-uuid

```

/dev/disk/by-uuid# dd if=/dev/zero of=/dev/sda iflag=nocache oflag=direct bs=4096

```

---

### Post by oldfred on 2014-09-29
If you used sda, that would be your first drive? Hope that was the only drive then.

---

