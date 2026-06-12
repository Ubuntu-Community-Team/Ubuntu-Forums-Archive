---
title: "about change of owner"
date: 2012-12-29
forum: General Help
---

### Post by satimis on 2012-12-29
Hi all,

Ubuntu 12.04 desktop 64bit
external enclosure HD 640G, USB connection (/dev/sdb)

I expect using the HD on the external enclosure for storage purpose without partion.  The HD has been successfully blanked with dd

When I ran
sudo mkfs.vfat /dev/sdb
it complained not allowing without partition and requesting adding -I

sudo mkfs.vfat -I /dev/sdb
it worked adding the FS

After mounting the external enclosure;
$ sudo cp test.txt /mnt
worked without probem but the file is owned by root

change owner
$ sudo chown satimis:satimis /mnt/test.txt
it complained 'permission not allowed'

Also tried as root without result.

Whether I must create partition on the external enclosure HD?  Can I create a single partition using the whole HD?

Please advise.  TIA

B.R.
satimis

---

### Post by dino99 on 2012-12-29
wow, really a strange question coming from an old noob  ):P

- each device need to be formated with a supported format : usually ext3 (or ext4 with journalling)
- vfat ????  what an old dusty thing

mountall package will deal silently in the background with that device

---

### Post by satimis on 2012-12-29
> **dino99 said:**
>  -snip-

- each device need to be formated with a supported format : usually ext3 (or ext4 with journalling)
- vfat ????  what an old dusty thing

mountall package will deal silently in the background with that device
I have old Windows stuff for storage.

satimis

---

### Post by rnerwein on 2012-12-29
> **satimis said:**
> Hi all,

Ubuntu 12.04 desktop 64bit
external enclosure HD 640G, USB connection (/dev/sdb)

I expect using the HD on the external enclosure for storage purpose without partion.  The HD has been successfully blanked with dd

When I ran
sudo mkfs.vfat /dev/sdb
it complained not allowing without partition and requesting adding -I

sudo mkfs.vfat -I /dev/sdb
it worked adding the FS

After mounting the external enclosure;
$ sudo cp test.txt /mnt
worked without probem but the file is owned by root

change owner
$ sudo chown satimis:satimis /mnt/test.txt
it complained 'permission not allowed'

Also tried as root without result.

Whether I must create partition on the external enclosure HD?  Can I create a single partition using the whole HD?

Please advise.  TIA

B.R.
satimis
hi
fat, vfat and ntfs from windows and don't know something about user-group-other permission and the ownership is quite different. therefor it is shown as rwx-rwx-rwx root root
cheers

---

### Post by satimis on 2012-12-30
> **rnerwein said:**
> hi
fat, vfat and ntfs from windows and don't know something about user-group-other permission and the ownership is quite different. therefor it is shown as rwx-rwx-rwx root root
cheers
Ah, I see.  Thanks.

The HD is for storage purpose only.  Amongst those old stuff there are Windows format.  

In case I need running those Windows files I'll copy them to Windows PC to run them. I won't run them direct on the external enclosure. Besides most of them were either saved on Windows Notepad or MSOffice format.

Would .ext4 be the suitable format for my application? If YES I'll format the HD on ext4 FS running;```

$ sudo mkfs.ext4 /dev/sdb

```
?

TIA


Regards
satimis

---

### Post by rnerwein on 2012-12-30
> **satimis said:**
> Ah, I see.  Thanks.

The HD is for storage purpose only.  Amongst those old stuff there are Windows format.  

In case I need running those Windows files I'll copy them to Windows PC to run them. I won't run them direct on the external enclosure. Besides most of them were either saved on Windows Notepad or MSOffice format.

Would .ext4 be the suitable format for my application? If YES I'll format the HD on ext4 FS running;```

$ sudo mkfs.ext4 /dev/sdb

```?

TIA


Regards
satimis
hi
just use OpenOffice - it's able to handle Word-documents, LibreOffic too  ;-)
cheers

---

### Post by Cheesemill on 2012-12-30
Also I don't know if Windows will even understand the way you have set up your drive.

You should always create a partition and then create the filesystem on top of that, even if it is just one partition.

Creating a filesystem on an unpartitioned drive is asking for trouble (hence the warning from mkfs).

If I were you I would start again using gparted to give the drive an msdos type partition table and then create one large NTFS partition that uses the whole drive.

Once you've done this we can sort out mounting it with the correct permissions.

---

### Post by rnerwein on 2012-12-30
> **Cheesemill said:**
> Also I don't know if Windows will even understand the way you have set up your drive.

You should always create a partition and then create the filesystem on top of that, even if it is just one partition.

Creating a filesystem on an unpartitioned drive is asking for trouble (hence the warning from mkfs).

If I were you I would start again using gparted to give the drive an msdos type partition table and then create one large NTFS partition that uses the whole drive.

Once you've done this we can sort out mounting it with the correct permissions.
hi
as i know if you only give a device by running mkfs - mkfs will create one for the whole disk.
cheers

---

### Post by Cheesemill on 2012-12-30
> **rnerwein said:**
> hi
as i know if you only give a device by running mkfs - mkfs will create one for the whole disk.
cheers
Yes, it works. But it's not recommended. It will almost definitely cause you problems later on.

---

### Post by satimis on 2012-12-30
Hi all,

Thanks for your advice.

If I understand it correctly I'll perform following steps;

1)
# fdisk /dev/sdb
creating one partition covering the whole HD, primary

2)
# mkfs.ext4 /dev/sdb1
to format the partition

(Or omitting 2)) ?

B.R.
satimis

---

### Post by Cheesemill on 2012-12-30
Just install [gparted]("apt://gparted") and do it all using a graphical application, it's much easier.

Also you want to create an NTFS partition, not ext4 as Windows doesn't understand the ext4 filesystem.

When you've opened gparted click on the box in the top right to select your device (sdb). Then go to Device > Create partition table to create an msdos type partition table. Then right-click on the free space and create a new partition that takes up the entire drive and choose NTFS as the type. Then click on the tick to apply the operation.

Once you've done this you should be able to just plug the stick into any machine, mounting and permissions will be taken care of automatically.

---

### Post by satimis on 2012-12-30
> **Cheesemill said:**
> Just install [gparted]("apt://gparted") and do it all using a graphical application, it's much easier.

Also you want to create an NTFS partition, not ext4 as Windows doesn't understand the ext4 filesystem.
But on those old stuff there are Linux files.

> 
When you've opened gparted click on the box in the top right to select your device (sdb). Then go to Device > Create partition table to create an msdos type partition table. Then right-click on the free space and create a new partition that takes up the entire drive and choose NTFS as the type. Then click on the tick to apply the operation.

Performed following steps;

Start gparted as root
-> select /dev/sdb as advised.

Device -> Create Partition Table

Create partition table on /dev/sdb
Warning: This will erase all data on the entire disk /dev/sdb
Default is to create an MS-DOS partition table
-> Apply

block```

Unallocated
596.17GiB

```

Stop here and exit gparted.  I'm not quite sure which filesystme I'll create?  It'll take lengthy time to separate the old Linux stuff.  I won't run those files, Windows or Linxu direct on the external enclosure HD.

Regards
satimis

---

