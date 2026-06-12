---
title: "Redo Rescue Error on Boot."
date: 2022-05-28
forum: General Help
---

### Post by Disabled20241022 on 2022-05-28
I have a new laptop (XPS 17 from Dell) and i am running ubuntu but when i use my external SSD to boot from a grub menu and then into Redo Rescue (software, ISO file) to make a backup of my partition i get this and i would like some help fixing this.

---

### Post by Disabled20241022 on 2022-05-31
Is this because of the thunderbolt usb type c port or is it something else?

---

### Post by Disabled20241022 on 2022-06-25
Does anybody have a idea?

---

### Post by mIk3_08 on 2022-06-25
> **ayudha said:**
> I have a new laptop (XPS 17 from Dell) and i am running ubuntu but when i use my external SSD to boot from a grub menu and then into Redo Rescue (software, ISO file) to make a backup of my partition i get this and i would like some help fixing this.

Try to use fsck. It might solve your issue. fsck can check the inodes, blocks, sizes and structure of your storage. Regards and cheers.

---

### Post by Disabled20241022 on 2023-05-12
Doesnt do anything for me

---

### Post by mIk3_08 on 2023-05-12
Be sure you have pointed the fsck to the right destination.
example:
```
fsck /dev/sdf
sudo fdisk -l  /dev/sdf
```
To identify the exact destination run the following command below:
```
ls -l /dev | grep "sd"
```

---

### Post by Disabled20241022 on 2023-05-14
I get this:
> ~$ sudo fsck /dev/sda1fsck from util-linux 2.37.2
fsck.fat 4.2 (2021-01-31)
There are differences between boot sector and its backup.
This is mostly harmless. Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
[123?q]? 3
Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
[12?q]? 2
/dev/sda1: 385 files, 18335/201616 clusters




Afraid of losing data i pressed no.

---

### Post by yancek on 2023-05-14
What type filesystem are you trying to repair?  Is it a Linux or windows (fat) filesystem?  Your output in the last post would indicate a fat filesystem.  Also, note that the filesystem was not unmounted properly according to your post content.  You need to properly unmount the partitions filesystem before running fsck.  The link below is to one of the many sites online which explain the use of fsck and the various options.

[https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/](https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/)

---

### Post by Disabled20241022 on 2023-05-17
It is a bootable USB drive in grub with multple partitions, one is a FAT for EFI and the others are ext4 partitions.

---

### Post by yancek on 2023-05-17
[https://unix.stackexchange.com/questions/607434/fsck-dirty-bit-is-set](https://unix.stackexchange.com/questions/607434/fsck-dirty-bit-is-set)

The link above gives an explanation of what the dirty bit is/does.  Also, the error you posted above indicates that the usb was not properly unmounted so that is the first step as fsck generally won't work on a mounted partition.

---

### Post by Disabled20241022 on 2023-07-08
Could you please be so kind to 101 it for me?
Guide me though the steps of doing this because im afraid of losing data by pressing yes/no.

---

### Post by ActionParsnip on 2023-07-08
> **ayudha said:**
> 
Afraid of losing data i pressed no.
Your backups will protect your data. You have backups.... Right?

---

### Post by Disabled20241022 on 2023-07-10
This usb drive is my backup, so no haha.

---

### Post by ActionParsnip on 2023-07-10
> **ayudha said:**
> This usb drive is my backup, so no haha.

Then create a new backup. If the USB is the backup then you have the standing data... Yes?

---

