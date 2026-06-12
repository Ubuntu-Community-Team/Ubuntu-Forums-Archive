---
title: "What is this partition that is created when clean install ubuntu 16.04."
date: 2018-03-02
forum: General Help
---

### Post by qwretyweee on 2018-03-02
what is this partition for and how can i delete it. i did a clean install on a empty hard drive. I'm referring to the "Ubuntu 17.04 amd64" partition.
[ATTACH=CONFIG]278746[/ATTACH]

---

### Post by vasa1 on 2018-03-02
Please open a terminal and run```
uname -a
```and```
lsb_release -a
```and post the output here.

---

### Post by qwretyweee on 2018-03-02
> **vasa1 said:**
> Please open a terminal and run```
uname -a
```and```
lsb_release -a
```and post the output here.
[ATTACH=CONFIG]278749[/ATTACH]

---

### Post by vasa1 on 2018-03-02
Please post terminal output as text between code tags. Use the # icon to generate [noparse]```
 and 
```[/noparse] tags or type type in yourself. It's more convenient for people to quote your data when responding to you.

Back to your issue: is the image you posted in the first post taken from the side-pane of your file manager?

If so, please run```
sudo fdisk -l
``` and```
sudo parted -l
```and post that information here.

---

### Post by qwretyweee on 2018-03-02
> **vasa1 said:**
> Please post terminal output as text between code tags. Use the # icon to generate [noparse]```
 and 
```[/noparse] tags or type type in yourself. It's more convenient for people to quote your data when responding to you.

Back to your issue: is the image you posted in the first post taken from the side-pane of your file manager?

If so, please run```
sudo fdisk -l
``` and```
sudo parted -l
```and post that information here.

Sorry for the improper reply,

this are the outputs.

```
vaio@vaio-VPCS117GG:~$ sudo fdisk -l
[sudo] password for vaio: 
Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe8e1bde2

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1  *          2048 1452847103 1452845056 692.8G 83 Linux
/dev/sda2       1452849150 1465147391   12298242   5.9G  5 Extended
/dev/sda5       1452849152 1465147391   12298240   5.9G 82 Linux swap / Solaris


vaio@vaio-VPCS117GG:~$ sudo parted -l
Model: ATA WDC WD7500BPVT-5 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  744GB  744GB   primary   ext4            boot
 2      744GB   750GB  6297MB  extended
 5      744GB   750GB  6297MB  logical   linux-swap(v1)


vaio@vaio-VPCS117GG:~$ 

```

---

### Post by leunam12 on 2018-03-02
Probably the best way to see what is going on is ```
lsblk
```

---

### Post by oldfred on 2018-03-02
You used the older BIOS/MBR configuration.
Which has / (root), extended & swap partition as default. With 17.10 or later swap partition is not created and swap file is used.
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 


With MBR(msdos), you can only have 4 primary partitions. So Linux installer added the extended partition with is a container for logical partitions.
You then can have an unlimited number of logical partitions inside the extended partition. You currently only have swap inside it. And it left you with two more primary partitions. The extended also counts as one of your primary partitions.

Newer UEFI systems use gpt(GUID) partitioning which can be used to BIOS boot on most systems if you add a bios_grub partition.

 gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR(msdos) [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by qwretyweee on 2018-03-02
```
vaio@vaio-VPCS117GG:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sr0     11:0    1  1024M  0 rom  
sda      8:0    0 698.7G  0 disk 
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0   5.9G  0 part [SWAP]
&#9492;&#9472;sda1   8:1    0 692.8G  0 part /
vaio@vaio-VPCS117GG:~$
```

---

