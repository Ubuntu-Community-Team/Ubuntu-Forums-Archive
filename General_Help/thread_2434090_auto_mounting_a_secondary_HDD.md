---
title: "auto mounting a secondary HDD"
date: 2019-12-30
forum: General Help
---

### Post by pjstock on 2019-12-30
I have a secondary 250gb HDD sdb on a desktop system on which I store my Thunderbird profile.
On boot I have to click on this HDD in order to mount it or my Thunderbird fails to find the profile.
Not a big deal but I often forget to manually mount the drive. I would like it to just mount automatically on boot.
reading up, it seems that I have to modify my fstab to do this.

but I am not sure of the mount point that I would want for this drive and I don't want to mess up my fstab and system by experimenting.

can anyone give me clearer step by step instructions for this modification?
I think the correct UUID (for /dev/sdb1) seems to be UUID="6e07ec52-5ab1-4ef3-87b4-c889d34cc7a5" 

below is the output for 
sudo fdisk -l
and
sudo blkid

many thanks

Peter


```

sudo fdisk -l

Disk /dev/sda: 74.5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x63419c79

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048    206847    204800  100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 106493460 106286613 50.7G  7 HPFS/NTFS/exFAT
/dev/sda3       106493950 156301311  49807362 23.8G  5 Extended
/dev/sda5       106493952 148076543  41582592 19.8G 83 Linux
/dev/sda6       148078592 156301311   8222720  3.9G 82 Linux swap / Solaris


Disk /dev/sdb: 232.9 GiB, 250000000000 bytes, 488281250 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xe522e522

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1  *           63 409563181 409563119 195.3G 83 Linux
/dev/sdb2       409565182 488280063  78714882  37.5G  5 Extended
/dev/sdb5       409565184 480057343  70492160  33.6G 83 Linux
/dev/sdb6       480059392 488280063   8220672   3.9G 82 Linux swap / Solaris

Disk /dev/sdc: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf4529cc4

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdc1        2048 976769023 976766976 465.8G  7 HPFS/NTFS/exFAT


```

```
peter@nowinnorland:~$ sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="4ED4240ED423F73D" TYPE="ntfs" PARTUUID="63419c79-01"
/dev/sda2: UUID="5ABA2917BA28F0E5" TYPE="ntfs" PARTUUID="63419c79-02"
/dev/sda5: UUID="9ee3603b-73ca-47fe-8364-5fb0925fcd20" TYPE="ext4" PARTUUID="63419c79-05"
/dev/sda6: UUID="07413113-284b-48f7-854e-b70eec1a5728" TYPE="swap" PARTUUID="63419c79-06"
/dev/sdb1: LABEL="Int 250Gb Linux" UUID="6e07ec52-5ab1-4ef3-87b4-c889d34cc7a5" TYPE="ext4" PARTUUID="e522e522-01"
/dev/sdb5: UUID="40840a5b-68f1-48bd-86e6-12b36db49041" TYPE="ext4" PARTUUID="e522e522-05"
/dev/sdb6: UUID="e9d76651-689d-412c-8d59-896c3a7c50cd" TYPE="swap" PARTUUID="e522e522-06"
/dev/sdc1: LABEL="Small USB 500GB" UUID="828AB2A68AB295DF" TYPE="ntfs" PARTUUID="f4529cc4-01"

```

---

### Post by oldfred on 2019-12-30
I have my Firefox & Thunderbird in my /mnt/data partition and in a mozilla folder, no . like when in /home as hidden folder.

So where in sdb1 is your mozilla folder? 
Is that anther install or just a folder with it.

This is my mount of my data partition.
```
# Entry for /dev/sdb4 on Asus AR:
UUID=a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5 /mnt/data ext4 relatime,nofail,x-systemd.device-timeout=4 0 2

```

But I then have to change profiles.ini to have full path:

```
fred@bionic-z97:~$ cat ~/.thunderbird/profiles.ini
[InstallFDC34C9F024745EB]
Default=/mnt/data/mozilla/thunderbird/lyu25irb.default

[Profile0]
Name=default
IsRelative=0
Path=/mnt/data/mozilla/thunderbird/lyu25irb.default
Default=1

[General]
StartWithLastProfile=1
Version=2


```

I have used this same profile, with XP in shared NTFS going back years. I retired XP in 2011 and moved profile to ext4 partition and share with other Linux installs & systems.

---

### Post by The Cog on 2019-12-30
Where do you mount the drive to when you do it manually? If not sure, lsblk while it's mounted will tell you. Maybe you should mount it there with crontab.

It looks like you have the right UUID.

---

