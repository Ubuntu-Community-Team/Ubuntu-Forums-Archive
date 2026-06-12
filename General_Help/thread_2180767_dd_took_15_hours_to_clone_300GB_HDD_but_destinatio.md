---
title: "dd took 15 hours to clone 300GB HDD but destination is corrupted"
date: 2013-10-14
forum: General Help
---

### Post by Scottie303 on 2013-10-14
I wanted to make a disk clone for backup purposes of a Windows7 HDD for an HP laptop. This was for extra safety before restoring the Laptop to factory defaults. I tried Clonezilla but for some reason it failed to even begin the cloning process ( I did not take note of the errors). I resorted to using **dd** from the Terminal.

I was booting Ubuntu from an external USB HDD and I was trying to create my backup in a partition on a different HDD also connected via USB. The partition **was** bigger than the disk I was trying to clone. So **fifteen hours later** I found that the destination partition was corrupt and my back-up files were nowhere to be found. Well I couldn't face another 15 hours of **dd** with an unknown outcome so I took a gamble and was able to restore the Windows machine to its factory condition using HP's built in restore program.

So there was no harm done.

When I was waiting for **dd** to complete I did a few things that may or may not have caused the procedure to fail: 
1 - I mounted the target partition part way through **dd** procedure to see if any files had shown up - they had not. 
2 - I kept an eye on the process by running the command:** $ sudo kill -USR1 [dd PID]** which caused **dd** to print out a progress report before it would carry on.
3 - The command used to run **dd** was: **sudo dd if=/dev/sda of=/dev/sdc2  **(note - sda is a Windows HDD with three partition, sdc2 is the second partition on an HDD with two partitions)

One other thing may have caused a problem and this was reported by **fdisk -l** in a terminal: There was a warning that **"Partition (sdc1) does not end on cylinder boundary"**

Does anyone know if one of the above could have caused the target partition to become corrupted after the **dd** procedure? 
(It is marked as RAW - unformatted whereas before **dd** it was formatted for NTFS )

---

### Post by oldfred on 2013-10-14
I do not know dd well, except it can be dangerous as any typo causes big issues. Nicknamed Data Destroyer for that reason.
But it is intended for same size to same size copies. Or drive to drive or partition to partition. You can copy drives or partitions to files if enough space, but it also copies all empty space. 
 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

        from caljohnsmith post #7
I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)

    Often bs setting for blocksize can speed it up a lot.

RAW is an unformatted NTFS partition. Data may be NTFS, but the PBR or partition boot sector must also be NTFS with what boot loader (even if data only)  and start & size of partition that must match partition table.
       
Full image backup
GNU ddrescue (packaged as gddrescue, though once installed the command is "ddrescue") 
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

    
 Old info on dd to image drive:
[http://ubuntuforums.org/showthread.php?t=896519](http://ubuntuforums.org/showthread.php?t=896519)
sudo dd if=/dev/sde | gzip >/media/400/16GB.gz
zcat /media/400/16GB.gz | dd of=/dev/sde

Suggest using Windows backup tools for Windows.
      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by VMC on 2013-10-14
@ jjm95,

Clonezilla erros can be found on "/var/log/partclone.log". Usually the errors is just a matter of fsck'ing  your partition.
```
 sudo fsck /dev/sdaX
```
For example:
```
$ sudo fsck /dev/sda6
[sudo] <enter password> 
fsck from util-linux 2.20.1
e2fsck 1.42.8 (20-Jun-2013)
/dev/sda6: recovering journal
Setting free inodes count to 1103814 (was 1103822)
Setting free blocks count to 4123339 (was 4123390)
/dev/sda6: clean, 177306/1281120 files, 997266/5120605 blocks
```

---

### Post by VMC on 2013-10-14
Also i think it would be more efficient to use a block size (bs=) with the dd command.
Another thing you can try, if Clonezilla doesn't work for you,  ntfsclone :
```
ntfsclone --overwrite /dev/sda1 /dev/sdc2
```

Here's the info on copying Windows to another hard drive:
[http://www.nilbus.com/linux/disk-copy.php](http://www.nilbus.com/linux/disk-copy.php)

By the way, your dd is copying the entire hard drive instead of the Windows partition(s).

More info on using the dd command is found [here]("http://softpanorama.org/Tools/dd.shtml"), and and another good one [here]("http://www.noah.org/wiki/Dd_-_Destroyer_of_Disks").

You can also use dd to backup to an image as well: ```
dd bs=1M if=/dev/sda of=drive.img
```

The problem with dd is it copies **everything**, including empty blocks. That's why I use either CloneZilla, partclone or fsarchiver.

---

