---
title: "What to do with USB flash drive or SD card"
date: 2016-06-06
forum: General Help
---

### Post by palmgrower on 2016-06-06
_**MicroSD card: **_I got a 64GB microsd card. Printed on the card are: class 10, microsdxc 1, Lexar633x, 64GB. I understand this comes with exFAT. Now I need to change to FAT32 so that I can use it in a mp3 player. Home screen > Left top > Disk > Gear icon > format > fat32. It is not recognized by the mp3 player. 

_**Format/Partion difference**_: I put the card back in computer. Gear Icon > Partition format. What is the difference between partition and format?

Thank you.

---

### Post by sudodus on 2016-06-06
A partition is a part of a mass storage device (hard disk drive, SSD, USB pendrive, ... SD card). It can be a container of a file system. FAT32 is a file system. To format is to create a file system. In a general sense 'to create a partition table with partitions' might also be considered as 'to format'. Maybe it is better not to use 'format' but to state clearly 'create a partition table', 'create or edit partitions', 'create a file system', 'prepare a partition for linux swap'.

These operations will usually (but not always) remove the contents of previous partitions and file systems. So you should backup all important files and directories before these operations. (It is ***not*** the same as removing all traces of previous files.)

-o-

I think SDXC cards are specified to use the exfat file system. I am not sure that they work or are recognized with other file systems. See this link

[sdxc-specifications-and-compatibility](http://kb.sandisk.com/app/answers/detail/a_id/2520/~/sd%2Fsdhc%2Fsdxc-specifications-and-compatibility)

> Because SDXC uses a different file system called exFAT and it works differently than standard SD cards, this new format is NOT backwards compatible with host devices that only take SD (128MB to 2GB) or host devices that only take SDHC (4GB to 32GB). Most host devices built after 2010 should be SDXC compatible.

To ensure compatibility, look for the SDXC logo on cards and host devices (cameras, camcorders, etc.).


- Do I understand correctly that you have already formatted the card to fat32 with ***Disks***?

- Did the format process seem to finish correctly?

- Can you mount the FAT32 partition of the card in your computer?

- Can you read/write files from/to the new partition in the card?

-o-

I think it is easier to use ***gparted*** for these tasks, because 'you see' what you do with the graphical user interface. ***gparted*** is included in the Ubuntu iso files and can be used directly when you 'try Ubuntu' alias run a live session booted from a DVD or USB drive.

You can install gparted into an installed system

```
sudo apt-get install gparted
```

***If you must format to exfat again***, I suggest that you do it in Windows, because exfat is a proprietary file system owned by Microsoft. Borrow a computer if you have no Windows in your own computer.

---

### Post by howefield on 2016-06-06
> **palmgrower said:**
> _**MicroSD card: **_I got a 64GB microsd card. Printed on the card are: class 10, microsdxc 1, Lexar633x, 64GB. I understand this comes with exFAT. Now I need to change to FAT32 so that I can use it in a mp3 player. Home screen > Left top > Disk > Gear icon > format > fat32. It is not recognized by the mp3 player.

Most mp3 players and the like would offer to format the disk upon insertion or have an option to carry out the format, have you tried that ? 

> _**Format/Partion difference**_: I put the card back in computer. Gear Icon > Partition format. What is the difference between partition and format?

Disks can be "sliced" up into several parts, each part being a partition. Formatting means preparing the disk or partition to enable files to be written to it, each partition could contain differing file systems.

---

### Post by X-RED_Tech on 2016-06-06
Most MP3 players I know do not support 64GB cards (SDXC) nor exFAT.

---

### Post by palmgrower on 2016-06-06
> **sudodus said:**
> - Do I understand correctly that you have already formatted the card to fat32 with ***Disks***?

- Did the format process seem to finish correctly?

- Can you mount the FAT32 partition of the card in your computer?

- Can you read/write files from/to the new partition in the card?
Thank you for the explanation of partition.
Yes, I formatted the card to fat32.
Yes, the formatting seemed to finish correctly.
No, the device was not mounted.
No. Since it was not mounted, I could not do anything.

---

### Post by palmgrower on 2016-06-06
> **howefield said:**
> Most mp3 players and the like would offer to format the disk upon insertion or have an option to carry out the format, have you tried that ? 
It hangs.

---

### Post by X-RED_Tech on 2016-06-07
Make/model of the MP3 player?

---

### Post by sudodus on 2016-06-07
> **palmgrower said:**
> Thank you for the explanation of partition.
Yes, I formatted the card to fat32.
Yes, the formatting seemed to finish correctly.
No, the device was not mounted.
No. Since it was not mounted, I could not do anything.

When connected to your computer, can you 'see' the card with one of the following commands? Please post the output within [noparse]```
tags
```[/noparse]

```
sudo parted -ls

sudo lsblk -fm
```

If you can see the card, for example as /dev/sdb and the FAT32 partition as /dev/sdb1, you can try to mount it manually with the following command

```
sudo mount /dev/sdb1 /mnt
```

And then you can try to write a file and after that read it.

```
cd /mnt
sudo bash -c "echo 'Hello World' > hello.txt"
cat hello.txt
```

The command 'cat hello.txt' should produce the output 'Hello World'. Does that work for you? In that case the card works with FAT32 in your computer.

If not, I suggest that you connect the card to a computer running Windows and try to format it to exfat again.

---

### Post by oklokl on 2016-06-07
sdcard reader(Please use recommended.)

Camera equipment or hardware is impossible to recognize the Ubuntu system.
You need to install additional programs.
(Identical to the Windows)

Old hardware devices.
Not supported.

---

