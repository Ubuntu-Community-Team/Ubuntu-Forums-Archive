---
title: "USB Drive: ...Mount(2) system call failed: Structure needs cleaning."
date: 2018-01-20
forum: General Help
---

### Post by tjscott on 2018-01-20
I am using Lubuntu 17.10 and brand new to this. I learned what I have so far reading a few posts here. Now I am stuck. 

I have a WD 2 TB hard drive (Disk /dev/sdb: 1.8 TiB noted below) connected via USB port. This drive was in a WD MyCloud EX4 that stopped working. I want to offload the files. 

I am getting the error:[INDENT]Error mounting /dev/sdb4 at /media/thomas/70d534fb-554f-4c93-aa91-227965570d0b: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb4" "/media/thomas/70d534fb-554f-4c93-aa91-227965570d0b"' exited with non-zero exit status 32: mount: /media/thomas/70d534fb-554f-4c93-aa91-227965570d0b: mount(2) system call failed: Structure needs cleaning.

[/INDENT]
 
I guess I need to clean the file structure. Below are the couple things I  tried. Where do I go from here? Please let me know if any more  information would be helpful.

Thank you in advance.

Side bar: How do I turn off the touchpad? Uggh! Dell Inspiron 15. 

---------

In a terminal window:[INDENT]thomas@thomas-Inspiron-5520:~$ **fsck -a /dev/sdb4**
[/INDENT]
[INDENT]fsck from util-linux 2.30.1
fsck.ext2: Permission denied while trying to open /dev/sdb4
You must have r/w access to the filesystem or be root
[/INDENT]
[INDENT]
thomas@thomas-Inspiron-5520:~$ **sudo fdisk -l**
[sudo] password for thomas: 

**Disk /dev/sda: 931.5 GiB**, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe03ce000

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1               63      80324      80262  39.2M de Dell Utility
/dev/sda2  *         81920   29044735   28962816  13.8G  7 HPFS/NTFS/exFAT
/dev/sda3         29044736 1788747569 1759702834 839.1G  7 HPFS/NTFS/exFAT
/dev/sda4       1788747774 1953523711  164775938  78.6G  5 Extended
/dev/sda5       1788747776 1953523711  164775936  78.6G 83 Linux

**Disk /dev/sdb: 1.8 TiB**, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C617062A-C923-4146-87CF-BB28DCE032E8

Device          Start        End    Sectors  Size Type
/dev/sdb1        2048    4196351    4194304    2G Linux swap
/dev/sdb2     6293504 3904931839 3898638336  1.8T Microsoft basic data
/dev/sdb3  3904931840 3907029134    2097295    1G Microsoft basic data
/dev/sdb4     4196352    6293503    2097152    1G Microsoft basic data

Partition table entries are not in disk order.
thomas@thomas-Inspiron-5520:~$ 
[/INDENT]

---

### Post by yancek on 2018-01-20
I don't use 17.10 but the link below explains how to disable touchpad on 17.10.

[https://askubuntu.com/questions/973818/how-can-i-disable-touchpad-palm-detection-on-ubuntu-17-10/973896](https://askubuntu.com/questions/973818/how-can-i-disable-touchpad-palm-detection-on-ubuntu-17-10/973896)

You need to preface the fsck command with sudo.  Using the fdisk command as you did just lists drive/partition information and won't change anything. 
I'm not sure that fsck will 'clean the structure' but running it shouldn't damage anything.  You might try it and see and if it doesn't improve, maybe post the results of the command.

---

### Post by ajgreeny on 2018-01-20
Your disk sdb is formatted mainly with what appear to be Windows filesystems so there is no point using fsck on it; you really need to repair it, or clean exit from it using Windows and its own tools.

Do you have access to a Windows OS which you can use and run chkdsk on the problem partition?

---

### Post by tjscott on 2018-01-21
> **yancek said:**
> I don't use 17.10 but the link below explains how to disable touchpad on 17.10.

[https://askubuntu.com/questions/973818/how-can-i-disable-touchpad-palm-detection-on-ubuntu-17-10/973896](https://askubuntu.com/questions/973818/how-can-i-disable-touchpad-palm-detection-on-ubuntu-17-10/973896)

You need to preface the fsck command with sudo.  Using the fdisk command as you did just lists drive/partition information and won't change anything. 
I'm not sure that fsck will 'clean the structure' but running it shouldn't damage anything.  You might try it and see and if it doesn't improve, maybe post the results of the command.

Yaneck, thank you for your help. Here's what I got. 

&#65279;_**Touch Pad**_ (Probably should be a separate thread from here). 
I couldn't find the settings window on Lubuntu 17 (brand new at this). This worked, though. 
[https://askubuntu.com/questions/969851/how-do-i-disable-the-touchpad-in-ubuntu-17-10](https://askubuntu.com/questions/969851/how-do-i-disable-the-touchpad-in-ubuntu-17-10) 
 
Command: [B]synclient TouchpadOff=1
[/B]
If I shutdown or reboot, it resets to On. 

_**Drive:**_

Below is a copy and paste of what I tried. I am trying to access the files on disc sbd4. Do you know what command I would use to do that? And if the file structure needed to be fixed, how would I do that? Like fdisk in Windows? 

thomas@thomas-Inspiron-5520:~$ [B]sudo fsck -a /dev/sbd4
[/B]fsck from util-linux 2.30.1
fsck.ext2: No such file or directory while trying to open /dev/sbd4
Possibly non-existent device?

thomas@thomas-Inspiron-5520:~**$ sudo fdisk -l**
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe03ce000

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1               63      80324      80262  39.2M de Dell Utility
/dev/sda2  *         81920   29044735   28962816  13.8G  7 HPFS/NTFS/exFAT
/dev/sda3         29044736 1788747569 1759702834 839.1G  7 HPFS/NTFS/exFAT
/dev/sda4       1788747774 1953523711  164775938  78.6G  5 Extended
/dev/sda5       1788747776 1953523711  164775936  78.6G 83 Linux

Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C617062A-C923-4146-87CF-BB28DCE032E8

Device          Start        End    Sectors  Size Type
/dev/sdb1        2048    4196351    4194304    _2G Linux swap_
/dev/sdb2     6293504 3904931839 3898638336  _1.8T Microsoft basic data_
/dev/sdb3  3904931840 3907029134    2097295    1G Microsoft basic data
/dev/sdb4     4196352    6293503    2097152    1G Microsoft basic data

Partition table entries are not in disk order.
thomas@thomas-Inspiron-5520:~$ ^C
thomas@thomas-Inspiron-5520:~$

---

### Post by tjscott on 2018-01-21
> **ajgreeny said:**
> Your disk sdb is formatted mainly with what appear to be Windows filesystems so there is no point using fsck on it; you really need to repair it, or clean exit from it using Windows and its own tools.

Do you have access to a Windows OS which you can use and run chkdsk on the problem partition?

Hi ajgreeny, 

Thanks for your help. 

I first tried Disk Management in Windows 10. (I have used this before a bunch of times with success on other external drives). I could see the drive, but Windows could not read it. I tried to initialize the drive. I was prompted that it needed to be formatted. 

This drive was in a WD MyCloud EX4. I read that it uses a Linux file system. It looks like it's part that and part some kind of Microsoft system. 

Here's the drive info again below. It looks like "Linux Swap" may be the key? Do you know what command I could use to access and fix the file system? i.e. the Linux equivalent of fdisk. I tried a few things and can't get into any partition. 

[INDENT]Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C617062A-C923-4146-87CF-BB28DCE032E8

Device          Start        End    Sectors  Size Type
/dev/sdb1        2048    4196351    4194304    2G **Linux swap**
/dev/sdb2     6293504 3904931839 3898638336  1.8T Microsoft basic data
/dev/sdb3  3904931840 3907029134    2097295    1G Microsoft basic data
/dev/sdb4     4196352    6293503    2097152    1G Microsoft basic data
[/INDENT]

A little more research yielded this command and results:

[INDENT]thomas@thomas-Inspiron-5520:~**$ lsblk -f**
NAME   FSTYPE            LABEL    UUID                                 MOUNTPOINT
sda                                                                    
&#9500;&#9472;sda1 vfat                       3E19-485E                            
&#9500;&#9472;sda2 ntfs              RECOVERY D2821C04821BEC2B                     
&#9500;&#9472;sda3 ntfs              OS       78EE1F1F3E1BD823                     
&#9500;&#9472;sda4                                                                 
&#9492;&#9472;sda5 ext4                       4c0a6f4b-c4ea-4ba2-9daf-d77f76476256 /
sdb                                                                    
&#9500;&#9472;sdb1 linux_raid_member          de4cb4dc-4e68-b0f8-97b1-8ca2eb36b398 
&#9500;&#9472;sdb2 linux_raid_member 1        eecafe31-f5f2-899e-0300-c4fef8e6fed1 
&#9500;&#9472;sdb3                                                                 
&#9492;&#9472;sdb4 ext4                       70d534fb-554f-4c93-aa91-227965570d0b 
sr0                                    
[/INDENT]

There's something here, [http://www.rodsbooks.com/linux-fs-code/](http://www.rodsbooks.com/linux-fs-code/), that looks like I am on the right track. I don't understand any of it, though. Can you help?

---

### Post by ajgreeny on 2018-01-21
Looks like the partitions are, or have been, part of a RAID system abouty which I know nothing at all, so you will need to await more help from someone else who does know, I'm afraid.

---

