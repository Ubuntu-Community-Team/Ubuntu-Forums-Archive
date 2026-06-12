---
title: "Help with formatting flash drive"
date: 2013-03-15
forum: General Help
---

### Post by spiritech on 2013-03-15
i need some help regarding the disks utility. first i would like to ask. what is the reason for the two formatting options, the one in the top right and the one just below the Volumes box. one gives the option to format (mbr/dos) or (gpt) or no partitioning (leave empty)  and the other gives the normal formatting options such as fat32, ext3/ext4 etc. in what case do i need to use the first options and if so which one is recommended.

secondly i am trying to parition a flash drive and keep getting errors. it says the content of the drive is Unallocated Space (GUID Partition Table). if i try to use one of the (mbr/dos), (gpt) or (leave empty) options i get this error

```
Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0)
```

if i try to format a partition i get this error

```
Error creating partition on /dev/sdc: Command-line `parted --align optimal --script "/dev/sdc" "mkpart \" \" ext2 1MiB 16240328191b"' exited with non-zero exit status 1: Error: The primary GPT table is corrupt, but the backup appears OK, so that will be used.
Error: Unable to satisfy all constraints on the partition.
 (udisks-error-quark, 0)
```

i really dont understand the two formatting options and/or when to use them. the only thing i can gather is one is table format and the other is partition format.

spiritech

---

### Post by spiritech on 2013-03-15
I have just checked the out put of ```
sudo lshw -class disk 
``` and the device is not listed. also i noticed that all the disks are patitioned as dos. so i guess i messed up when i tried to format the drive to 2TB (gtp) option.

---

### Post by MrsUser on 2013-03-15
GPT and MBR/DOS are different formats for the partition table. A partition table contains information about how you "arranged" or "parted" the physical space (partitions) of your storage device. In other words: Partitions are needed to separate the storage space for different purposes (e.g. partition that contains the OS, partition that contains your data, another partition with another OS, etc).

GPT is only needed for large disks >2TB. Create a MBR/DOS partiton table and then format to fat32, NTFS or ext4 or whatever you like. Use GParted (available from the Software Center). In GParted, select the flash drive from the dropdown menu in the top right corner. Then select "Device" > "Create Partition Table". Choose MBR/DOS. After that you can format it.

Note that MBR/DOS can only handle up to 4 primary partitions on one drive.

---

### Post by spiritech on 2013-03-15
> GPT and MBR/DOS are different formats for the partition table. A  partition table contains information about how you "arranged" or  "parted" the physical space (partitions) of your storage device

so GPT or MRB/DOS is the format of the table that contains/ or will contain any partition information.

> Use GParted (available from the Software Center). In GParted, select the  flash drive from the dropdown menu in the top right corner. Then select  "Device" > "Create Partition Table".

ok. i will give gparted a go.

> Note that MBR/DOS can only handle up to 4 primary partitions on one drive. 				

how many partitions can GPT handle?

---

### Post by carl4926 on 2013-03-15
GPT = as many primary as u like

msdos = 4 primary

---

### Post by spiritech on 2013-03-15
> In GParted, select the flash drive from the dropdown menu in the top  right corner. Then select "Device" > "Create Partition Table". Choose  MBR/DOS. After that you can format it.

thankyou. this fixed it. no more currupt drive. one thing i did notice is that there were quite a few different options for formatting, aix, amiga, bsd, dvh, gpt, mac, pc98, sun, loop. are there any advantages in using one of these over the msdos for a linux only platform?

---

### Post by oldfred on 2013-03-15
Those other partitioning options are for use with those systems. So if you have an IBM AS/400 you might want aix.

Most use MBR(msdos) as that is what the PC has used from the beginning. But new computers now use gpt for UEFI boot, drives over 2TB and SSDs. But Windows only boots from gpt partitioned drives with UEFI.

And new UEFI systems need gpt partitioning. 

I have used gpt on my 16GB flash drive with a full Ubuntu install, just to see if it works and to learn about gpt. It did work and once installed I do not see much difference. With my new SSD drive, I do not have Windows, so I created both an efi partition for future use with a new system (originally last summer), and a bios_grub partition which grub needs to BIOS boot with gpt partitioning.

There is a limit on gpt. It has a default maximum of 128 partitions in its partition table, but you can also change partition table so you can have more if need be.

 GPT Advantages (older but still valid)  srs5694 post #@:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

