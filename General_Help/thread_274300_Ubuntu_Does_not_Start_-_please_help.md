---
title: "Ubuntu Does not Start - please help"
date: 2006-10-09
forum: General Help
---

### Post by src2206 on 2006-10-09
Hi friends,

I have triple boot system in my PC. In the Disk 1, there are 4 partitons and in 2 nd HDD I have 8 partitions. In the **HDD1** **WinXP** and **Ubuntu** are installed and in **HDD2 FC5** is installed. Today morning [I don't know why] the GRUB loader of Ubuntu failed. As this is the last OS I installed out of the three existing, I have to use its Grub to enter in the system. So I reinstalled Ubuntu's GRUB using the Ubuntu live CD to the hd0, ie MBR. After that the grub loaded alright and I can boot in both of my FC5 and Win XP but not in Ubuntu. Whenever I choose the option to boot in Ubuntu I get the following error massege:

```
[B][SIZE="3"]Filesystem type unknown. Partition type 0X82
kernel /boot/vmlinuz-2.6.15-386 root=/dev/hda8 ro quiet splash
error 17. can not mount selected partition.[/SIZE][/B]
```

The problem I understand is due to wrong volume. The ubuntu is installed in **hda6** [found out using fdisk -l command in FC5], **hda8 is the SWAP partition**. But I can not edit vmlinuz file and I'm not sure editing which file would solve the problem. I can access the Ubuntu drive through FC5.

Please help.

```
Output of fdisk -l command:

[root@localhost ~]# fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1565    12570831    7  HPFS/NTFS
/dev/hda2            1566        4865    26507250    f  W95 Ext'd (LBA)
/dev/hda5            1566        1950     3092481    7  HPFS/NTFS
**[size=3]/dev/hda6            1951        2348     3196903+  83  Linux[/size]**
/dev/hda7            2349        4674    18683563+   7  HPFS/NTFS
**[size=3]/dev/hda8            4675        4865     1534176   82  Linux swap / Solaris[/size]**

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    f  W95 Ext'd (LBA)
**[SIZE="3"]/dev/hdb5   *           1        2618    21029022   83  Linux[/SIZE]**
/dev/hdb6            2619        3383     6144831    b  W95 FAT32
/dev/hdb7            3384        4148     6144831    7  HPFS/NTFS
/dev/hdb8            4149        5423    10241406    7  HPFS/NTFS
/dev/hdb9            5424        8611    25607578+   7  HPFS/NTFS
/dev/hdb10           8612        8764     1228941    7  HPFS/NTFS
/dev/hdb11           8765        9561     6401871    b  W95 FAT32
/dev/hdb12           9562        9729     1349428+   7  HPFS/NTFS
```

---

### Post by mark_g on 2006-10-09
You probably need to edit the file /boot/grub/menu.lst and change

> kernel /boot/vmlinuz-2.6.15-386 root=/dev/hda8 ro quiet splash

to

> kernel /boot/vmlinuz-2.6.15-386 root=/dev/hda6 ro quiet splash

if hda6 is your Ubuntu partition (could also be FC5, if so, then use hdb5).

---

### Post by src2206 on 2006-10-10
Thank you mark.
I have solved the problem :) in the way you have sugested.

---

