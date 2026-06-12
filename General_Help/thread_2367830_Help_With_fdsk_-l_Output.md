---
title: "Help With fdsk -l Output"
date: 2017-08-03
forum: General Help
---

### Post by brenneke on 2017-08-03
I know just enough to be dangerous so looking for clarification - does this show two hard drives or one? (sda & sda1) I am looking to mount second hard drive after Lubuntu installation over an old Windows XP machine. This is not dual boot, Lubuntu only now. Any help in getting me going in the right direction will be much appreciated. 

```
rwh@RWH:~$ sudo fdisk -l
[sudo] password for rwh: 
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x90c5ef0b

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1  *     2048 976771071 976769024 465.8G 83 Linux


Disk /dev/sdf: 14.3 GiB, 15376000000 bytes, 30031250 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x928642e1

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdf1          32 30031249 30031218 14.3G  c W95 FAT32 (LBA)
rwh@RWH:~$ 

```

---

### Post by Bashing-om on 2017-08-03
brenneke; Hello;

That fdisk output reveals 
one hard drive of 465.8 GiB capacity with a linux install
one likely  USB thumb drive of 14.3 GiB with a Windows file system

[INDENT]hope this helps
[INDENT][INDENT]-ask-[/INDENT][/INDENT][/INDENT]

---

### Post by brenneke on 2017-08-03
That is what I was afraid of! Any suggestions as to what do do / where to go / what to read to get 2nd HDD to detect? (both HDDs were functioning with XP)  Thank you.

---

### Post by Bashing-om on 2017-08-03
brenneke; Humm ..

fdisk does not see a 2nd known installed hard drive then you have a problem.
Does bios "see" the drive when booting up ?
check the cabling . IDE device (ribbon )  crimped ? Got power to the drive ?

Install testdisk :
does testdisk "see" the drive ? 

[INDENT][INDENT]ouch - bad things can happen
[/INDENT][/INDENT]

---

### Post by brenneke on 2017-08-04
2nd HDD not showing in BIOS, also not seen by testdisk. I am not going to be able to set that one up I guess. Thanks for your help.

---

### Post by Bashing-om on 2017-08-04
brenneke; Yuk.

Drives do die;

In My opinion. not worth the effort to try and revivie.

If it it not seen anywhere;

[INDENT][INDENT]it's dead Jim
[/INDENT][/INDENT]

---

