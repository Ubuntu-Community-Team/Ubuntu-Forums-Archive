---
title: "create LVM"
date: 2015-10-11
forum: General Help
---

### Post by jimmyh1972 on 2015-10-11
Hi
how to write an inactive bash script to create LVM from my /dev/sda?
I need 4 partitions
1 for boot
2 for root
3 for home directory
4 for swap

thanks ahead

---

### Post by TheFu on 2015-10-11
"inactive"?

Actually, you probably want 2 partitions
* /boot - required. Cannot boot a partition inside LVM, correct?
* /everything-else for LVM
Then inside the LVM, you want a PV, a VG and 4 LVs.  An LV is equivalent to a "partition".

These requirements actually make the solution easier.

/boot should be fixed regardless of the HDD size - 500MB or 750MB if you want lots and lots of kernels. Others may have different suggestions for this size.  I'd format it as ext2. Call this sda1.

The rest of the HDD for all other stuff is 1 partition. Then you can make the entire sda2 a full PV and make the VG that entire space too. **pvcreate**, **vgcreate** and **lvcreate** ... are the commands. Of course, "sda" probably isn't the HDD since you've booted off some other installation media. 

Plus, thanks to LVM, provided the initial sizes all fit into the VG, each LV size isn't a big deal .... er.... provided ext4 is used, not xfs. xfs file systems cannot easily be reduced in size.

So ... you have the tools to get started. Just make certain that the disk being used has over some minimal amount of space - 20G? Take a stab at the script, post it and we can comment.

Perhaps starting with some high level steps?  That's how I begin coding - those become the code comments. 

Sounds like a fun and useful script.

---

### Post by jimmyh1972 on 2015-10-11
yes you are right
i want a boot partition of 1 giga
5 giga swap
and a lvm that will contain 10 giga root 
100 giga home
inactive means that the user will just run the script 
i tried 


sudo fdisk /dev/sdb <<EOF
d
n
p
1


+1G
n
p


+5G
n
p






w


EOF
doesnt work...

---

### Post by TheFu on 2015-10-12
a) don't use fdisk.  It can break GPT disks. That goes for sfdisk, cfdisk too. Plus those  commands didn't always align sectors on the correct boundaries. Beware.
b) there are machine readable inputs to parted.  **OR**
c) just clone an existing layout from a disk that you like. With GPT that isn't as easy as with MBR disks. [https://askubuntu.com/questions/57908/how-can-i-quickly-copy-a-gpt-partition-scheme-from-one-hard-drive-to-another](https://askubuntu.com/questions/57908/how-can-i-quickly-copy-a-gpt-partition-scheme-from-one-hard-drive-to-another) explains.  **sudo sgdisk --backup=filename {device}** is probably what you want. Please read the manpage VERY, VERY, carefully. Some of the options appear to be opposite from what other commands follow.

Put swap inside a LV too.  This way , if/when you decide to add encryption to the mix, the entire 2nd partition can be encrypted and all the LVM stuff inside, including swap will be encrypted too.  Like this:
```
$ sudo lsblk
NAME                            MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                               8:0    0 119.2G  0 disk  
&#9500;&#9472;sda1                            8:1    0   243M  0 part  /boot
&#9500;&#9472;sda2                            8:2    0     1K  0 part  
&#9492;&#9472;sda5                            8:5    0   119G  0 part  
  &#9492;&#9472;sda5_crypt (dm-0)           252:0    0   119G  0 crypt 
    &#9500;&#9472;c720--vg-root (dm-1)      252:1    0  51.9G  0 lvm   /
    &#9500;&#9472;c720--vg-lv--swap (dm-2)  252:2    0   4.1G  0 lvm   [SWAP]
    &#9492;&#9472;c720--vg-lv--Stuff (dm-3) 252:3    0    50G  0 lvm   /Stuff

```

Unfortunately, gdisk can break MBR disks. parted works with both. parted can be scripted according to the manpage. I've never tried.
```
$ sudo parted  -m /dev/sda
GNU Parted 2.3
Usando /dev/sda
¡Bienvenido/a a GNU Parted! Teclee «help» para ver la lista de órdenes.
(parted) p                                                                
BYT;
/dev/sda:128GB:scsi:512:512:msdos:ATA SC2 M2 SSD;
1:1049kB:256MB:255MB:ext2::arranque;
2:257MB:128GB:128GB:::;
5:257MB:128GB:128GB:::;
(parted) q       
```      
That is for the same disk/partitions.

---

