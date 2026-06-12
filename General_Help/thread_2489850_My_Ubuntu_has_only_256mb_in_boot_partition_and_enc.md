---
title: "My Ubuntu has only 256mb in boot partition and encrypted, better just reinstall?"
date: 2023-08-11
forum: General Help
---

### Post by drugdoubles on 2023-08-11
[COLOR=#212121][FONT=Verdana]The boot partition was installed years ago, it would say not enough space sometimes when I need to update, then need to use commands to solve it. I Google and seem like so complicate to deal with it since all are encrypted. Better and easier just to reinstall whole Ubuntu? 2gb boot partition should be good for like next 10 years?[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-08-11
In my installation recipes, I create 1.5GB to 3GB boot partitions. But I go that big to keep snapshots of what changes within that partition. Before going to a File Manager that had that capability, I did from 1GB to 1.5 GB on the boot partition.

Please backup your system before doing "anything". Always good to have a go-back-to point.

Have you thought about trying to resize that partition? That is also an option... Usually the boot partition is not encrypted... <-- Unless you manually did that on your own, i a manual install. The default "check the box" default Ubuntu Installations that were default with the install process did not do that on their own.

To confirm that, please post the output of
```

lsblk -e7 -o name,label,size,fstype,model

```

---

### Post by drugdoubles on 2023-08-13
> **MAFoElffen said:**
> In my installation recipes, I create 1.5GB to 3GB boot partitions. But I go that big to keep snapshots of what changes within that partition. Before going to a File Manager that had that capability, I did from 1GB to 1.5 GB on the boot partition.

Please backup your system before doing "anything". Always good to have a go-back-to point.

Have you thought about trying to resize that partition? That is also an option... Usually the boot partition is not encrypted... <-- Unless you manually did that on your own, i a manual install. The default "check the box" default Ubuntu Installations that were default with the install process did not do that on their own.

To confirm that, please post the output of
```

lsblk -e7 -o name,label,size,fstype,model

```

Thx for advice, here is the result:

sda                             119.2G             SATA SSD
&#9500;&#9472;sda1                            512M vfat        
&#9500;&#9472;sda2                              1K             
&#9500;&#9472;sda5                            731M ext4        
&#9492;&#9472;sda6                            118G crypto_LUKS 
  &#9492;&#9472;sda6_crypt                    118G LVM2_member 
    &#9500;&#9472;vgubuntu-root               117G ext4        
    &#9492;&#9472;vgubuntu-swap_1             976M swap

By the way this is a portable ssd and I only use it for Ubuntu

---

### Post by MAFoElffen on 2023-08-13
I would use these 3 for reference:
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)
[https://wiki.archlinux.org/title/Resizing_LVM-on-LUKS](https://wiki.archlinux.org/title/Resizing_LVM-on-LUKS)
[https://www.golinuxcloud.com/resize-luks-partition-shrink-extend-decrypt/](https://www.golinuxcloud.com/resize-luks-partition-shrink-extend-decrypt/)

Using them for reference, adapt the device names to what you have on your own system.

Note that all 3 guides ask you to back up your data before you start.

---

### Post by drugdoubles on 2023-08-17
> **MAFoElffen said:**
> I would use these 3 for reference:
[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)
[https://wiki.archlinux.org/title/Resizing_LVM-on-LUKS](https://wiki.archlinux.org/title/Resizing_LVM-on-LUKS)
[https://www.golinuxcloud.com/resize-luks-partition-shrink-extend-decrypt/](https://www.golinuxcloud.com/resize-luks-partition-shrink-extend-decrypt/)

Using them for reference, adapt the device names to what you have on your own system.

Note that all 3 guides ask you to back up your data before you start.

Thx for finding these guidelines for me. Look so complicated that I would just reinstall Ubuntu lol xd anyway thx.

---

