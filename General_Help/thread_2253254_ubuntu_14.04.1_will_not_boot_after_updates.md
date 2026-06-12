---
title: "ubuntu 14.04.1 will not boot after updates"
date: 2014-11-18
forum: General Help
---

### Post by okkie2 on 2014-11-18
I installed ubuntu 14.04.1 on a clean iT diskwith no problems and working perfectly. Then loaded all my documents,music and photos. Various updates were done and after another my system will not boot. I had to install another 14.04.1 next to the previous one to be able to do what I am doing now.I however need my documents, music etc badly and need help to access the previous install to obtain it. or a way to merge the two systems if possible.maybe if I can get into my hard drive which should be possible, I can try taking it from there to solve the boot problem and then delete the system I am using now. please any help will be appreciated.My computer is up to scratch.

---

### Post by Bashing-om on 2014-11-18
okkie2; Hello;

Often in a situation such as this what we find is that after an update a proprietary graphics driver broke.
To test this theory, can you boot the problematic install from the recovery console available from the grub boot menu -> advanced options ?
Also, to aid in testing, can you boot to console from the log in screen -> key combo ctl+alt+F1 ?

And YES. one can mount exterior partitions (file systems) and copy off the desired data - IF it should come to that .

Gotta start trouble shooting some where;

looks like a good place to start to me.

---

### Post by okkie2 on 2014-11-19
Thanks Bashing, here we go

---

### Post by okkie2 on 2014-11-25
Bash,
I have read so much of so many things I am now even more confused.However, I know if I have the Grub menu installed, I can at least pick which of the two Ubuntus installed I want to boot. The Grub menu will not install. I have tried everything in my power. I attach a screenshot of my disk with two partitions.It is obviously the big one I need to boot.
Is there another place where I can try to install the grub menu or a way I canmake the two partitions one without losing my everything ?
Sorry I can also not get the photo attached to my message[IMG]/home/okkie/Desktop/Screenshot from 2014-11-25 13:58:10.png[/IMG]

---

### Post by Bashing-om on 2014-11-25
okkie2; Hey ;

Hang'n with you. Commendable that you are seeking to learn !
Let's look and see what the partitioning on the hard drive is:
Post back the output - Between Code Tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
sudo blkid -c /dev/null

```
Depending on the partitioning scheme, is how grub will be installed -> how the system boots.

Do not feel bad about being confused of the grub process. I have been studying the boot process now for an extended period of time, and there are still factors I do not know about that constantly changing process - here comes SystemD ! -

Good chance, once we know what we are dealing with, we will struggle through this bit of mayhem.

Have you to this time learned how to mount the file system(s) and copy off your personal data ?

It is a process here
[INDENT][INDENT][INDENT]look'n for that point of failure
[/INDENT][/INDENT][/INDENT]

---

### Post by okkie2 on 2014-11-28
Thanks some more. I attach the information you asked for. Maybe this will take us somewhere.
Sorry if I do not react speedily at times as we are having internet problems.okkie@okkie-MS-7788:~$ sudo fdisk -lu
[sudo] password for okkie: 

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a3c60

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953521663   976509953    5  Extended
/dev/sda5          501760  1953521663   976509952   83  Linux

Disk /dev/mapper/sda5_crypt: 999.9 GB, 999944093696 bytes
255 heads, 63 sectors/track, 121569 cylinders, total 1953015808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 995.7 GB, 995719380992 bytes
255 heads, 63 sectors/track, 121055 cylinders, total 1944764416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 4177 MB, 4177526784 bytes
255 heads, 63 sectors/track, 507 cylinders, total 8159232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table
okkie@okkie-MS-7788:~$ sudo parted -l
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   1000GB  1000GB  extended
 5      257MB   1000GB  1000GB  logical


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 4178MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0,00B  4178MB  4178MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 996GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0,00B  996GB  996GB  ext4


Error: /dev/mapper/sda5_crypt: unrecognised disk label                    

okkie@okkie-MS-7788:~$ sudo parted /dev/sda unit s print
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1953523055s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start    End          Size         Type      File system  Flags
 1      2048s    499711s      497664s      primary   ext2         boot
 2      501758s  1953521663s  1953019906s  extended
 5      501760s  1953521663s  1953019904s  logical

okkie@okkie-MS-7788:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="ade3d283-5067-42ef-a206-22d498076013" TYPE="ext2" 
/dev/mapper/sda5_crypt: UUID="EflC1d-31sW-wlWc-KFIf-U22X-2V34-PXMIqe" TYPE="LVM2_member" 
/dev/mapper/ubuntu--vg-root: UUID="5bda7c4a-ef21-418b-9550-b6d9014f651f" TYPE="ext4" 
/dev/mapper/ubuntu--vg-swap_1: UUID="efae332b-9f4c-4be5-aeb5-42beff55dc7f" TYPE="swap" 
okkie@okkie-MS-7788:~$

---

### Post by Bashing-om on 2014-11-28
okkie2; UnGood !

I am glad to say I can not help you:
> 
Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

/dev/mapper/sda5_crypt: UUID="EflC1d-31sW-wlWc-KFIf-U22X-2V34-PXMIqe" TYPE="LVM2_member" 


As I know nothing about encryption, and little enough about Logical Volume Management.

Perhaps others can advise on a method to proceed to correct the partition table.

[INDENT][INDENT]If I know everything
[INDENT][INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

