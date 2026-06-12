---
title: "some problems in booting, Unable to resolve 'UUID=***&quot;"
date: 2008-01-29
forum: General Help
---

### Post by chineseli on 2008-01-29
ubuntu stops in booting progress, but ctrl+d can ignore it, 

the /var/log/checkfs    says:

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
430:4e/52, 431:54/65, 432:4c/6d, 433:44/6f, 434:52/76, 435:20/65, 436:69/20
, 437:73/64, 438:20/69, 439:6d/73, 440:69/6b, 442:73/20, 443:69/6f
, 444:6e/72, 445:67/20, 446:ff/6f, 447:0d/74, 448:0a/68, 449:44/65
, 450:69/72, 451:73/20, 452:6b/6d, 453:20/65, 454:65/64, 455:72/69
, 456:72/61, 457:6f/2e, 458:72/ff, 459:ff/0d, 460:0d/0a, 461:0a/44
, 462:50/69, 463:72/73, 464:65/6b, 465:73/20, 466:73/65, 467:20/72
, 468:61/72, 469:6e/6f, 470:79/72, 471:20/ff, 472:6b/0d, 473:65/0a
, 474:79/50, 475:20/72, 476:74/65, 477:6f/73, 478:20/73, 479:72/20
, 480:65/61, 481:73/6e, 482:74/79, 483:61/20, 484:72/6b, 485:74/65
, 486:0d/79, 487:0a/20, 488:00/74, 489:00/6f, 490:00/20, 491:00/72
, 492:00/65, 493:00/73, 494:00/74, 495:00/61, 496:00/72, 497:00/74
, 498:00/0d, 499:00/0a, 506:bf/cb, 507:cc/d8
Not automatically fixing this.
/dev/sda3: 3301 files, 1083766/1278928 clusters
fsck.ext3: Unable to resolve 'UUID=acbf2c3d-8022-46fe-a608-c5691b18a13a'

fsck.ext3: Unable to resolve 'UUID=4525b139-e70b-4858-878f-40a72eee5361'

fsck died with exit status 8


I remember I changed my partition before the problem happened, I know it must be related to the partition change, but I don't know how to deal with it . 

further more , what's UUID, I guess it may be some kind of identification number of hard wares,  How the number is determined or generated?  what's the advantages of using these numbers other than something like sda1 ?

I'm a fresh linux-er and not a English native speaker, please forgive my poor English and my boring question.

Thank you for you help.

---

### Post by kpkeerthi on 2008-01-29
Can you post the output of ```
cat /etc/fstab
```? I think you partitions are configured with UUIDs instead of device names and a couple of those are incorrect.

Please use [code] tags to post the output here.

---

### Post by chineseli on 2008-01-29
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda12
UUID=8086257b-346c-469a-83f1-c494cc10fea3 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1
UUID=FA8072B38072764B /media/sda1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda9
UUID=acbf2c3d-8022-46fe-a608-c5691b18a13a /media/sda10 ext3 defaults 0 2
# /dev/sda10
UUID=4525b139-e70b-4858-878f-40a72eee5361 /media/sda11 ext3 defaults 0 2
# /dev/sda3
UUID=C082-4956 /media/sda3 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=CE08DB9708DB7D41 /media/sda5 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda6
UUID=44B8F52CB8F51D5C /media/sda6 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda7
UUID=5C6437EE6437CA12 /media/sda7 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda11
UUID=a38fa30e-8286-4044-87de-e780fed40394 none swap sw 0 0
# /dev/sda8
UUID=17d6197a-8bea-4b63-a893-0c73ca1c8f1c none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

```

and I just found the command ls -l /dev/disk/by-uuid/  ,the output of this in the terminal is :
```
lrwxrwxrwx 1 root root 10 2008-01-30 03:15 17d6197a-8bea-4b63-a893-0c73ca1c8f1c -> ../../sda8
lrwxrwxrwx 1 root root 11 2008-01-30 03:15 4368793e-5590-4575-8c0a-19c6e53d95dd -> ../../sda10
lrwxrwxrwx 1 root root 10 2008-01-30 03:15 44B8F52CB8F51D5C -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-01-30 03:15 48f9110a-aba3-40c9-92e0-5bd75e1c3ff5 -> ../../sda9
lrwxrwxrwx 1 root root 10 2008-01-30 03:15 5C6437EE6437CA12 -> ../../sda7
lrwxrwxrwx 1 root root 11 2008-01-30 03:15 8086257b-346c-469a-83f1-c494cc10fea3 -> ../../sda12
lrwxrwxrwx 1 root root 11 2008-01-30 03:15 a38fa30e-8286-4044-87de-e780fed40394 -> ../../sda11
lrwxrwxrwx 1 root root 10 2008-01-30 03:15 C082-4956 -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-01-30 03:15 CE08DB9708DB7D41 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-01-30 03:15 FA8072B38072764B -> ../../sda1
```  

is it the situation that I should use the uuids show by the command to substitue the uuids in fstab file ?


furthermore , I want to the what are the uuid used for?

---

### Post by chrisccoulson on 2008-01-29
You have a couple of incorrect UUID's in your fstab. I've highlighted the two lines that need changing (and included correct UUID):
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda12
UUID=8086257b-346c-469a-83f1-c494cc10fea3 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1
UUID=FA8072B38072764B /media/sda1 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda9
[COLOR="Red"]UUID=4368793e-5590-4575-8c0a-19c6e53d95dd /media/sda10 ext3 defaults 0 2[/COLOR]
# /dev/sda10
[COLOR="Red"]UUID=a38fa30e-8286-4044-87de-e780fed40394 /media/sda11 ext3 defaults 0 2[/COLOR]
# /dev/sda3
UUID=C082-4956 /media/sda3 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda5
UUID=CE08DB9708DB7D41 /media/sda5 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda6
UUID=44B8F52CB8F51D5C /media/sda6 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda7
UUID=5C6437EE6437CA12 /media/sda7 ntfs defaults,umask=007,gid=46 0 1
# /dev/sda11
UUID=a38fa30e-8286-4044-87de-e780fed40394 none swap sw 0 0
# /dev/sda8
UUID=17d6197a-8bea-4b63-a893-0c73ca1c8f1c none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
```

---

### Post by chineseli on 2008-01-29
thank you so much!

---

### Post by tact on 2008-01-29
> **chineseli said:**
> ...further more , what's UUID, I guess it may be some kind of identification number of hard wares,  How the number is determined or generated?  what's the advantages of using these numbers other than something like sda1 ?

I'm a fresh linux-er and not a English native speaker, please forgive my poor English and my boring question.

Thank you for you help.

Hey there... forgive this if my reply is a boring answer..  :)

UUID's are almost as you guessed...they are identifying numbers.  They identify HDD partitions, so they are not strictly hardware identifiers (you create and delete partitions).  They are supposed to be unique numbers.  They are created by pretty much any disk partitioning software (linux or windows) at the time a partition is formatted.   i.e. if you reformat a partition - it will get a new UUID.

Advantage of using UUID over something like "sda1"...  I guess there may be a few advantages but one is that using UUID to identify partitions means that you no longer have to worry about the (sometimes weird) re- ordering of drive partitions as sometimes happens if you add a new drive to a system and are using the hda and sda method.

In the move from ubuntu "edgy" to "feisty" there was a change in how ubuntu handled drive numbering (all drives, even IDE, were numbered using the sata codes sda, sdb, sdc etc  No more hda at all).   That solved some parts of the problem.  It was also to do with the pseudo sata driver performing better - ???? - maybe, maybe not.  :)

In Gutsy and onwards seems ubuntu is using UUIDs.  THis is jsut another step in referring to partitions even more explicitly.  i.e.  Referring to partitions via a unique number (UUID) should ensure that there is never any confusion even if drives are added or removed from a system.   It seems a good move.  

There are tools to find out the UUID of a partition, and even to manually change the UUID of a partition if ever it were needed (like after cloning a drive - UUIDs are also cloned and its not good to have duplicated UUID's ... means they are no longer unique.)

Hope that explains some of it...

---

