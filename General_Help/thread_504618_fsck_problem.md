---
title: "fsck problem"
date: 2007-07-19
forum: General Help
---

### Post by ittiam on 2007-07-19
Every time on boot fsck fails on the boot sector
But it does not stop or anything just says cannot fix it automatically and proceeds to load without any problems. But this comes up every time. How do i fix this?

```
There are differences between boot sector and its backup.
Differences: (offsetriginal/backup)
65:01/00, 430:4e/52, 431:54/65, 432:4c/6d, 433:44/6f, 434:52/76, 435:20/65
, 436:69/20, 437:73/64, 438:20/69, 439:6d/73, 440:69/6b, 442:73/20
, 443:69/6f, 444:6e/72, 445:67/20, 446:ff/6f, 447:0d/74, 448:0a/68
, 449:44/65, 450:69/72, 451:73/20, 452:6b/6d, 453:20/65, 454:65/64
, 455:72/69, 456:72/61, 457:6f/2e, 458:72/ff, 459:ff/0d, 460:0d/0a
, 461:0a/44, 462:50/69, 463:72/73, 464:65/6b, 465:73/20, 466:73/65
, 467:20/72, 468:61/72, 469:6e/6f, 470:79/72, 471:20/ff, 472:6b/0d
, 473:65/0a, 474:79/50, 475:20/72, 476:74/65, 477:6f/73, 478:20/73
, 479:72/20, 480:65/61, 481:73/6e, 482:74/79, 483:61/20, 484:72/6b
, 485:74/65, 486:0d/79, 487:0a/20, 488:00/74, 489:00/6f, 490:00/20
, 491:00/72, 492:00/65, 493:00/73, 494:00/74, 495:00/61, 496:00/72
, 497:00/74, 498:00/0d, 499:00/0a, 506:bf/cb, 507:cc/d8
1) Copy original to backup
2) Copy backup to original
3) No action
?

```
This is what i get when i run fsck.

I donno how am i proceed with what option

EDIT: The 3 options at the end of the output that I have posted does not comes up during boot, i just ran fsck from terminal to post the output here

---

### Post by aktiwers on 2007-07-19
Did you try to run :
```
sudo  fsck -ry 
```

?

I had a problem like this, and that fixet it. Do you have to press CTRL+D to be able to boot up normally after the scan?

Then it looks like my problem, happend every single time I booted the PC! 
I dont remember the exact error message, but the command above help me.

---

### Post by ittiam on 2007-07-19
No i didnt have to press ctrld-d on boot up, it just says cant fix this automatically and proceeds.  Will contemplate trying your suggestion and let you know the results. Am at work now and need to do this when i get bk home

---

### Post by aktiwers on 2007-07-19
Anyways, did you try run that command?
It fixed it for me. You can read what the -ry do in the Man page of Fsck. Thats where I found it.

---

### Post by bodhi.zazen on 2007-07-19
You need to run that command from a  live CD with the partition in question unmounted.

---

### Post by ittiam on 2007-07-19
Ok will do it as suggested by you both, using live cd and then running the command. No I havent tried running the command because I am having this problem with my laptop @ home. Am @ work now. Will try it and let you know the results.

One more question, is it possible that because of this that you might get some sounds when the hard disk is reading or writing. I dont know how to describe the sound but it is definitely not the deadly "tick" sound. I get this sound particularly while it is booting or when I am trying to install something.

---

### Post by ittiam on 2007-07-19
```
prasanna@Inspiron-e1505:~$ sudo fsck -ry /dev/sda2 
fsck 1.40-WIP (14-Nov-2006)
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

***** CURSOR BLINKS HERE FOR COUPLE OF SECONDS, DOES NOT GIVE ME ANY OPTIONS OR WHATSOEVER ******

/dev/sda2: 35720 files, 1156569/1790500 clusters

```

When i run the command you guys suggested, it shows the above thing and the cursor blinks at the point i mentioned abovr then prints a line of detail and comes back to the prompt

---

### Post by bodhi.zazen on 2007-07-19
> **ittiam said:**
> ```
prasanna@Inspiron-e1505:~$ sudo fsck -ry /dev/sda2 
fsck 1.40-WIP (14-Nov-2006)
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

***** CURSOR BLINKS HERE FOR COUPLE OF SECONDS, DOES NOT GIVE ME ANY OPTIONS OR WHATSOEVER ******

/dev/sda2: 35720 files, 1156569/1790500 clusters

```

When i run the command you guys suggested, it shows the above thing and the cursor blinks at the point i mentioned abovr then prints a line of detail and comes back to the prompt

yep, go ahead and re-boot. That should have fixed your problem.

See man fsck : [http://linux.die.net/man/8/fsck](http://linux.die.net/man/8/fsck)

> -r
    Interactively repair the filesystem (ask for confirmations). Note: It is generally a bad idea to use this option if multiple fsck's are being run in parallel. Also note that this is e2fsck's default behavior; it supports this option for backwards compatibility reasons only. 
-y
    For some filesystem-specific checkers, the -y option will cause the fs-specific fsck to always attempt to fix any detected filesystem corruption automatically. Sometimes an expert may be able to do better driving the fsck manually. Note that not all filesystem-specific checkers implement this option. In particular fsck.minix(8) and fsck.cramfs(8) does not support the -y option as of this writing.

I do not see any error messages, so I presume you are good to go.

---

### Post by ittiam on 2007-07-19
I rebooted and i get the same thing again :(

---

### Post by bodhi.zazen on 2007-07-20
You will need to look into disk recovery tools such as [testdisk](http://www.cgsecurity.org/wiki/TestDisk) (testdisk is in the ubuntu repositories) or try running fsck manually (and fixing the problem yourself):

sudo fsck -r /dev/sda2

Data loss may occur :(

---

### Post by ittiam on 2007-07-24
sorry for the late reply. Well i cant afford data loss in the drive..that is the drive using which my comp boots. any other suggestion?

---

### Post by LordKenTheGreat on 2007-08-25
I have the same problem on my system, is there a solution to this?

---

### Post by Herman on 2007-08-25
Yes, back up your data first.
Read this link, [                      When the bootsector is not the same as its backup]("http://users.bigpond.net.au/hermanzone/p10.htm#differences_between_the_bootsector_and_its_backup").

You need to be careful when you decide whether to copy the original to the backup or the backup to the original boot sector. 
Usually the backup is okay and it is the original boot sector that has been corrupted somehow, but sometimes it's the other way around..
If this is a Windows operating system partition you are talking about,  maybe it has been caused by some program you installed or was installed for you.  Update your antivirus and run a scan, then do some free on-line scans by rival antivirus companies, you may have some virus or malware. 

Consider switching completely to Linux.

Regards, Herman :)

---

### Post by Herman on 2007-08-25
> Well i cant afford data loss in the drive..that is the drive using which my comp boots. Computers boot from the **M**aster **B**oot **R**ecord first, then if they have code in the MBR to make them point to Windows, they boot the  Windows boot sector and then to NTLDR and boot.ini in Windows.
 If the MBR has code in it to look for GRUB, (stage1), it will use stage 1_5 in the first track to help it find GRUB stage2 in the Ubunu partition. Ubuntu can have code in it's boot sector but it is optional and most of the time it isn't needed, so by default it is not written there. GRUB doesn't rely on a boot sector for booting Linux, only for chainloading Windows.

So the Windows boot sector is of no importance in booting the computer, only for booting Windows. The MBR is important for booting the computer.
To repair the bootloader part of the MBR you can use FIXMBR for Windows or you can restore GRUB to MBR for Linux (Ubuntu). 

If you have a [Super Grub Disk]("http://geocities.com/supergrubdisk/"), you can still boot Ubuntu or Windows even if the MBR has a problem. 
You can also repair the Windows boot sector with Super Grub Disk.
Another way to repair the Windows boot sector is with a Windows install CD, with the FIXBOOT command.

SO what I am trying to say is, don't be scared, there are lots of ways to fix your computer, just make sure your data is backed up, (like you do all the time anyway, right?), and go ahead and try to fix it. Most of the time you will get it fixed right away, if not, try a different way, but don't be scared to try. As long as your data is backed up and you have the software CDs what do you have to lose? :)

Regards, Herman :)

---

