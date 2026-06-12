---
title: "Ubuntu Disk image / backup with Macrium"
date: 2017-06-03
forum: General Help
---

### Post by anspectrum on 2017-06-03
Hello,

I've finally shifted from 12.04 to 16.04.:)

I always keep my laptop in dual boot. Right now its Win7 + Ubuntu. Since Ubuntu does not have a very good disk image (backup) utility, I use windows based Macrium Reflect to take disk image. Its fast and only takes image of whats actually written on the disk and not the whole partition.

My current Ubuntu (16.04) partition used space is 5.9GB (partition size is 70GB) and since I've installed / tweaked all the necessary packages as per my liking, this is high time to take disk image. The problem is that when I open up Macrium it is showing me disk used space as 30.x GB. And if I start taking backup then it shows that its going to take whole 30GB as backup. This is of course not right. Now I know this query might be little off for Ubuntu forums, but I am hoping that someone can point to something that can help in resolving this issue. Is there a way to see / correct Ubuntu used partition sizes ( or may be file indexing) that might be wrongly seen by other programs.

Thanks.

---

### Post by paul_h on 2017-06-03
Macrium Reflect is essentially a MS Windows application and, although used in some mixed environments, it appears to have limitations with some Linux file systems.

I have dual booted Ubuntu and Windows (all versions back to XP) and have always found Clonezilla to be a reliable means of cloning and restoring complete hard disks. Clonezilla has saved my skin on several occasions, with my own dual-booted  and single Ubuntu systems and when I have been helping others with their Windows machines.

---

### Post by VMC on 2017-06-03
I agree Clonezilla is flawless. If you leave defaults it will validate the partition that was just cloned. It has never failed, and I've used it for years.

---

### Post by LastDino on 2017-06-03
If you don't mind, "fsarchiver" is also a good option

[https://ubuntuforums.org/showthread.php?t=2221842](https://ubuntuforums.org/showthread.php?t=2221842)

[http://www.fsarchiver.org/quickstart/](http://www.fsarchiver.org/quickstart/)

Haven't had a problem with any of my backups since then

---

### Post by VMC on 2017-06-03
> **LastDino said:**
> If you don't mind, "fsarchiver" is also a good option

[https://ubuntuforums.org/showthread.php?t=2221842](https://ubuntuforums.org/showthread.php?t=2221842)

[http://www.fsarchiver.org/quickstart/](http://www.fsarchiver.org/quickstart/)

Haven't had a problem with any of my backups since then

Yes, indeed! I was going to mention fsarchiver, but thought the op wanted a cloned partition. 
In the past fsarchiver had errors on backup, not anymore. The great thing about fsarchiver is
you can backup a filesystem on a partition and restore to a smaller partition. CZ can't do that.

---

### Post by LastDino on 2017-06-03
Also, you actually don't need to unmount the partition for fsarchiver to work. Very useful if you're taking backups from live/online machines

---

### Post by Mark Phelps on 2017-06-03
I use both Macrium Reflect and Clonezilla,and although MR will take image backups of Linux partitions, I prefer to use Clonezilla -- as I know from experience that it will work correctly.

---

### Post by anspectrum on 2017-06-04
Thanks for all the replies and suggestions.

I know about Clonezilla and did use it some years back but can't remember the functionalities now. However, I do remember that Clonezilla needs to be executed (run) as a standalone utility from boot (like using USB stick or DVD) and secondly Clonezilla does not image only written sectors rather takes image of whole partition. Is that correct?

Infact, my intention of posting this query was to inquire about a possible procedure to make Ubuntu partition clean where data is not written so that other programs do not see wrong used space. On side note, I have tried another program called Paragon, and it did show me correct used size of Ubuntu partition, though I am not going to use it.

---

### Post by VMC on 2017-06-04
No. Clonezilla clones only used sectors on partition image. Also you can install partclone (that's what CZ uses), and then clone another unmounted partition. Something like this:

**CLONE**
```
sudo ./partclone.ext4 -z 10485760 -N -c -s /dev/sdaX -o - | pigz -c --fast -b 1024 -p 16 > /*folder-location*/ubuntu.gz; cat /*folder-location*/ubuntu.gz | pigz -d -c|sudo ./partclone.chkimg -N -s -
```

**RESTORE**
```
 zcat /*folder-location*/ubuntu.gz | sudo ./partclone.ext4 -N -r -o /dev/sda?
```

"pigz" speeds cloning up, specially if you have multiple cores.

---

### Post by anspectrum on 2017-06-05
@VMC, you rock.

I didn't know that Clonezilla (partclone) only images used blocks. I guess I am too rusty to learn and explore these amazing products.

I've used partclone as suggested by @VMC to image the partition and although it takes more time (around 1.3GB per minute) as compared to Macrium, I would take it as acceptable. I think partclone is going to be in my bag of tools for life now. Bye bye MR, welcome partclone.

---

