---
title: "Ubuntu 7: accessing NTFS partition without Win on it"
date: 2007-04-27
forum: General Help
---

### Post by TheRomania on 2007-04-27
Hello. Recently I made some changes to my OS and now I have just Ubuntu 7. Before I used Win XP and had the following config. ATA HDD one partition with Win and the 2nd HDD an SATA with 2 partitions NTFS. All my files are stored on the SATA partitioned as described. Now, that I use Ubuntu as the only OS on the ATA HDD, how can I access my files stored on the SATA 2 partitions NTFS.? Please help.

---

### Post by taurus on 2007-04-27
You just need to mount it before you can access it.  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by TheRomania on 2007-04-27
> **taurus said:**
> You just need to mount it before you can access it.  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

will I loose data from the SATA NTFS 2 partition HDD? I have around 300 and something GB. One more thing. Without Windows just Ubuntu, after I mount it, can I use it as NTFS for storage ONLY for alot of time?

---

### Post by taurus on 2007-04-27
It depends on what you want to do with that harddrive.  If you use ntfs driver that comes with Ubuntu, then you can only read from that harddrive.  But if you want to write to it, then you need to install ntfs-3g.  

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

So, it's up to you whether you want to read-only or read/write to that ntfs drive.

---

### Post by TheRomania on 2007-04-27
> **taurus said:**
> It depends on what you want to do with that harddrive.  If you use ntfs driver that comes with Ubuntu, then you can only read from that harddrive.  But if you want to write to it, then you need to install ntfs-3g.  

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

So, it's up to you whether you want to read-only or read/write to that ntfs drive.

Oh, I see. I understand now. Thank you _taurus_.

---

