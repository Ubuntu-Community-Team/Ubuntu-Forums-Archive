---
title: "How to recover from failed SSD"
date: 2023-10-17
forum: General Help
---

### Post by sotires on 2023-10-17
Firing up my computer after a long period away, I got a "no valid media" message. So I removed the drive and connected it as an external drive on another computer, and it doesn't show up. I also connected it as a second internal drive. "Files" can't see the drive, but "Disks" sees it as an unknown volume on /dev/sda. 

Does anyone have any ideas on what I can do to repair the system, or to at least recover the files
Thanks

---

### Post by Autodave on 2023-10-17
If you can't connect to it, you can't recover files.  That's why backups are REALLY important.

---

### Post by TheFu on 2023-10-17
> **Autodave said:**
> If you can't connect to it, you can't recover files.  That's why backups are REALLY important.

+1.

Generally when an SSD fails, that's it. It will never work again.  All storage devices are going to fail. Hopefully, it will be after we are done using them for important things, but often, it isn't.  I've seen SSDs fail in less than 1 month, after 2.5 yrs and after 5+ yrs.  While modern SSD failures are generally lower than spinning HDD storage, they aren't perfect and still fail.  Learn and use the "3-2-1 backup" method. Google that term to see everyone recommends it.

[LIST]
[*]3 copies of the data
[*]2 backups (not the primary place)
[*]1 backup needs to be remote
[/LIST]

When I have excellent backups, I sleep better. Honest. It is a huge weight lifted NOT to worry about data loss.  Over the decades, I've had lots of failures. Sometimes without any backups. Since around 2003, I haven't lost anything. Oddly, this wasn't when I finally got **backup religion**.  That took until 2008.  Since then, I've had lots of storage failures. They've been inconvenient, but not bad.  Usually I just order a replacement HDD after a failure and for about 4 days while I wait for the replacement disk to arrive, I have trouble sleeping.  So much better to know I have excellent backups.  Especially since 2-4TB HDDs are so cheap these days.

---

### Post by MAFoElffen on 2023-10-17
+3 --
Just seeing the title: "How to recover from failed SSD" = Replace drive and restore from backup. My condolences.

But you said, that
> but "Disks" sees it as an unknown volume on /dev/sda. 
Which means that the drive is active, but the partitions and/or filsystem within that partition is broken...

What does "[testdisk]("https://www.cgsecurity.org/wiki/TestDisk")" say? My second choice would be PhotoRec, which is at the same link...

But lesson learned. If you had current backup's, then I would say, 
```

Test the disk from SMART
    |_ If Bad 
        |_ Replace Disk
        |_ Restore from Backup
    |_ If good go on
        |_ List partition table
            |_ If valid, test repair filesystem
            |_ If good. Success.
            |_ If fail
               |_ Reformat Partition
               |_ Restore from Backup
            |_ If bad
                |_Repartition Drive
                |_ Reformat partition
                |_ Restore from Backup

```
Which all that would be so much faster than using the low-level tools I recommended above.

See in that flow chart, how many times a backup would be needed? In your case, substitute, "Install Fresh and start over..."

---

