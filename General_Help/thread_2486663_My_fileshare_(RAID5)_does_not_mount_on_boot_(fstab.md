---
title: "My fileshare (RAID5) does not mount on boot (fstab)"
date: 2023-05-07
forum: General Help
---

### Post by sepp1945 on 2023-05-07
I have a mount to my RAID 5 for all data, the Opsys is on a DELL T440 BOSS-S1.
I setup the mount in fstab, all other items mount on boot, except the RAID 5
I can mount it from the file system, no problem   ... CHANGE I MUST SUPPLY MY PASSWORD
Works fine after that. What have i done wrong?
I supply the relevant line below.

Many thanks

Sepp

***************************************************
12 #RAID MOUNT POINT
13 /dev/disk/by-uuid/3F92-52B3 / ext4 defaults,x-gvfs-show 0 1
***************************************************

---

### Post by TheFu on 2023-05-08
The UUID looks to be for a FAT32 partition, not ext4.  Also, mounting to / is probably a really bad idea.  Please post the complete fstab, wrapped in forum 'code-tags' so we get the full picture.  

Would help to see the manual mount command you claim works too.

---

### Post by MAFoElffen on 2023-05-08
It's because of this:
> **sepp1945 said:**
> 
***************************************************
12 #RAID MOUNT POINT
13 /dev/disk/by-uuid/3F92-52B3 **[COLOR=#ff0000]/[/COLOR]** ext4 defaults,x-gvfs-show 0 1
***************************************************
If you instead tried this:
```

sudo mkdir /data

```
And changed the fstab entry to
```

***************************************************
12 #RAID MOUNT POINT
13 /dev/disk/by-uuid/3F92-52B3 /data ext4 defaults,x-gvfs-show 0 1
***************************************************

```
Then it will work...

Want an explanation?

You said it was a data type of storage, not your root drive. By this time root is already mounted. You need an empty partition stub to mount it "to"... (Not "/") The reason it mounts manaully, is that you were probably mounting it to "/mnt"...

---

### Post by Morbius1 on 2023-05-08
I think you missed this:

> **TheFu said:**
> The UUID looks to be for a FAT32 partition, not ext4. 
This is what an ntfs UUID looks like: **73186E124070CC8F**

This is what an ext4 UUID looks like: **b74f2dd-5e4b-4bc4-ad61-881b40d3e4e3**

And this is what a fat32 or maybe xfat UUID looks like:
> /dev/disk/by-uuid/**3F92-52B3** / ext4 defaults,x-gvfs-show 0 1

---

### Post by sepp1945 on 2023-05-08
Thank you all,

first my system
UBUNTU 22.04.2 ON DELL T 440
installed on BOSS-S1 (2 X 480GB M.2) RAID 1
RAID 5 IS DATA DISK mount on media/sepp/MD

the fstab is below
**********************************************************
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during curtin installation
# /boot/efi was on /dev/sdb1 during curtin installation
/dev/disk/by-uuid/0DF9-E1F5 /boot/efi vfat defaults 0 1
/swap.img    none    swap    sw    0    0
#RAID MOUNT POINT
/dev/disk/by-uuid/3F92-52B3 / ext4 defaults,x-gvfs-show 0 1
#MASTER BOOT
/dev/disk/by-uuid/1abc73cd-57e2-4b51-9236-2a12e62e76ed / ext4 defaults 0 1
*****************************************************************

i get the RAID 5 working (i installed Docker on it) by opening files (cinnamon) and clicking on MD, it askes for my password and i have the data disk mounted

I thank you all for helping

Sepp

PS here is the blkid output
**************************************************************
sepp@mercury:~$ sudo blkid
[sudo] password for sepp: 
/dev/sdb2: UUID="1abc73cd-57e2-4b51-9236-2a12e62e76ed" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="fc994bb9-0640-4b0b-b319-f78182dfc24d"
/dev/sdb1: UUID="0DF9-E1F5" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="ffda26ba-28cf-4e99-8766-3c6a095f5aaf"
/dev/sda: LABEL_FATBOOT="MD" LABEL="MD" UUID="3F92-52B3" BLOCK_SIZE="512" TYPE="vfat"
/dev/loop1: TYPE="squashfs"
/dev/loop8: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop0: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
***************************************************************************************

---

### Post by TheFu on 2023-05-08
```
/dev/disk/by-uuid/3F92-52B3 / ext4 defaults,x-gvfs-show 0 1
/dev/disk/by-uuid/1abc73cd-57e2-4b51-9236-2a12e62e76ed / ext4 defaults 0 1
```

The first is 100% invalid.  You cannot mount a non-Linux file system onto /.  It isn't allowed.  Saying it is ext4 when it isn't (and clearly it isn't) won't work. Not ever.

So, try this:
```
$ sudo mkdir /mnt/data
```
then inside the fstab
```
UUID=1abc73cd-57e2-4b51-9236-2a12e62e76ed     /     ext4     defaults    0 1
UUID=3F92-52B3      /mnt/data      vfat      defaults,user,fmask=0113,dmask=0002,x-gvfs-show    0 2
```
Yes, change the order too.

BTW, putting a FAT32 or exFAT file system on to a Linux MDADM RAID is a terrible idea.  
After you replace the lines I posted and put in the new lines, run
```
sudo mount -a
```
to mount it.

But really you need to re-format the RAID to be ext4 or to use LVM.  Don't use FAT32 or exFAT. Please, for the love of dog!

---

### Post by sepp1945 on 2023-05-08
OK I understand and thank you for all your help\

My raid card only supports Windows, so i am getting a new RAID card.

Thank you all very much

---

### Post by MAFoElffen on 2023-05-09
> **sepp1945 said:**
> OK I understand and thank you for all your help\

My raid card only supports Windows, so i am getting a new RAID card.

Thank you all very much
Wait...
You said your system was:
```

UBUNTU 22.04.2 ON DELL T 440
installed on BOSS-S1 (2 X 480GB M.2) RAID 1
RAID 5 IS DATA DISK mount on media/sepp/MD

```
Since I was a Lenovo, HP and Dell Technician...

That card only has two drive connectors for two each M.2 NVMe SSD drives. Is supports RAID1. and it supports non-RAID drives. It does not support any other RAID modes.

It can support any filesystem you want to put on it.

The certified OS'es listed by Dell for that card are: Windows, RedHat, SUSE, Ubuntu and VMware ESXi...

So, that makes me very curious... What model Dell PERC RAID card in that Dell PE server do you have that you say is only supported by Windows, where you are getting your RAID5 support? That you say will not support ext4? All models I know of are supported by the OS'es listed above... Do you have some kind of aftermarket RAID card?

---

### Post by sepp1945 on 2023-05-09
The card BOSS-S1 works fine no problem, RAID 1, UBUNTU 22.04.2 
The problem card is PERC H750, as per DELL it only supports Windows RAID.... thats why had the problems. The option for LINUX is greyed out.

Windows RAID works fine, you can use it in Linux, BUT  it want mount on boot, you have to mount it from files.

I am using the onboard controller now and setting up the RAID via mdadm in Ubuntu

Cheers

Sepp

---

### Post by MAFoElffen on 2023-05-09
Yes it is... On The PERC 750 is certified for Ubuntu 20.04 and newer, Reference: [https://linux.dell.com/files/supportmatrix/Ubuntu_LTS_Support_Matrix.pdf?dgc=SM&cid=243909&lid=spr5932103165&RefID=dtw22_sm5932103165&linkId=140648423](https://linux.dell.com/files/supportmatrix/Ubuntu_LTS_Support_Matrix.pdf?dgc=SM&cid=243909&lid=spr5932103165&RefID=dtw22_sm5932103165&linkId=140648423)

Which says not for Ubuntu 18.04 and older. Even if you are not using the RAID from the card, you can still use the non-raid support to pass-through the drives and use mdadm. and ZFS dRAID or ZFS RAIDz. (Which I use the later two.)

(I saw in your last post that you said you are using mdadm...)

That PERC card is reported by Linux as: Broadcom / LSI MegaRAID 12GSAS/PCIe Secure SAS39xx

You just need to ensure that the firmware on the card is updated...

Do you have the Dell Ubuntu Driver Repository added to your source list and ensure your drivers are up to date?
RE: [https://linux.dell.com/repo/hardware/omsa.html](https://linux.dell.com/repo/hardware/omsa.html)

EDIT: The thing that bothered me, even about Lenovo, HP and Dell Support, is that when you called them, you had to ask to get transferred to another tier, to get to someone who knew their company had all this other OS support for their own products... Such as the Dell EMC Tier, who fully supports Ubuntu on their PowerEdge Servers. Even on consumer products, they do sell consumer products pre-installed with Ubuntu, so have many different (hidden from the general public) repositories for driver support with Canonical ([http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates))...

---

