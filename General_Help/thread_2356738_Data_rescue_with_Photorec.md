---
title: "Data rescue with Photorec"
date: 2017-03-26
forum: General Help
---

### Post by ATSC on 2017-03-26
Hello peeps :p

I'm trying to rescue data from my external harddisk - the disk has one partition that fills almost the entire disk. In Photorec, I'm being asked whether the rescue job should be performed on one partition or the entire disc. Which option is the right one for me?


cheers

---

### Post by sudodus on 2017-03-26
Depending of the kind of damage, that you suspect, and how important the data are, you might consider cloning the drive to another drive with ***ddrescue*** and do the repair work on the cloned copy. (This is particularly important if the drive is failing (physically)).

There is more structure in the partition, particularly if you know the file system, so I would suggest that you select partition for ***photorec***. You will find out if the partition and file system can be identified (depends on how severely the drive is damaged).

The following link may give you some more tips and links,

[Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

---

### Post by ATSC on 2017-03-26
Thanks for your advice! There's nothing broken here - I'm trying to rescue data that I've **moved** from the external hd to my main hd (I installed the OS over it ](*,)) . The external hd has 1 TB - cloning that one would require some effort... :-|

---

### Post by dragonfly41 on 2017-03-26
> [COLOR=#000000]The external hd has 1 TB - cloning that one would require some effort... [/COLOR][COLOR=#000000]
Recovery will require *considerable effort requiring* the computer to run overnight even days.
You cannot stop and resume.

Do understand that you need somewhere to *save* any recovered files. Another 1 TB drive possibly.

Try to define filters in photorec so that you limit the types of files you are recovering.[/COLOR]

---

