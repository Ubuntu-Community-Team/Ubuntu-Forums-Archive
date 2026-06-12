---
title: "Grub To A Specific Partition"
date: 2013-03-07
forum: General Help
---

### Post by Mike Green9 on 2013-03-07
Hi.

I have a dual boot (windows & Ubuntu 12:10) dual drive system. I am trying make the second drive an image of the first, so that if the first one fails, I can boot the second.

I am using the mbr built by easybcd to allow me to boot Windows or Ubuntu. If I select 'Ubuntu', i get directed to Grub on my Ubuntu partition. All is aok here.

I have already duplicated the Windows Partition, and it boots fine.

I just used GParted to copy my Ubuntu Partition - SDA4 >> SDB4. That seemed to work fine.
As expectecd, Ubuntu on SDB4 is an ext4 partition. However, I noticed it's mount point is  '/mnt'. I don't know why it is not '/'.

 I then tried to install GRUB on SDB4:

 sudo mount /dev/sdb4 /mnt
 sudo grub-install /dev/sdb4 --force

and I get the message:

/usr/sbin/grub-bios-setup: warning: File system `ext2' doesn't support embedding.
/usr/sbin/grub-bios-setup: error: embedding is not possible, but this is required for cross-disk install.

What gives?

Thanks,

M...

---

### Post by oldfred on 2013-03-07
When you copied the partitions have you also copied UUIDs? Then you cannot have both drives connected at the same time as you cannot have duplicate UUIDs. Or if you have different UUIDs they are not the same.

Post this:
       # To clear cache and get new view:
sudo blkid -c /dev/null -o list

---

### Post by Mike Green9 on 2013-03-07
Hi oldfred.

After I used GParted to make the copy, I used it to change the UUID of the destination.

As per your request:

```
device         fs_type label    mount point        UUID
---------------------------------------------------------------------------------------
/dev/sda1      ntfs    DELL Windows 7 Active (not mounted) CAD8E361D8E34A71
/dev/sda3      swap             <swap>             
/dev/sda4      ext4    Ubuntu   /                  e962de0a-f9f5-cd01-2060-de0af9f5cd01
/dev/sda5      ntfs    DELL Temp Area (not mounted) 649C6DB59C6D8302
/dev/sda6      ntfs    DELL Large Apps (not mounted) 68A80638A8060572
/dev/sda7      ntfs    DELL Dynamic Data /media/mg/DELL Dynamic Data 4ED05FBAD05FA6CD
/dev/sda8      ntfs    DELL DTN (not mounted)      3E5862035861BA73
/dev/sda9      ntfs    DELL Future Partitions (not mounted) 01CDDC03E8EB26B0

/dev/sdb1      ntfs    DELL Windows 7 Bkup (not mounted) 6D080C0FD8E34A71
/dev/sdb3      swap             (not mounted)      
/dev/sdb4      ext4    Ubuntu Bkup (not mounted)   2923ce59-9453-40ae-abe3-caaae6f55d36
/dev/sdb5      ntfs    DELL Temp Area (not mounted) 25845A889C6D8302
/dev/sdb6      ntfs    DELL Large Apps Bkup (not mounted) 101C28DAA8060572
/dev/sdb7      ntfs    DELL Dynamic Data Bkup (not mounted) 2C5A987FD05FA6CD
/dev/sdb8      ntfs    DELL Future Bkup (not mounted) 204B9AA8F4CB63B0

```

Earlier, I tried running on the backup drive SDB. I swapped SATA cables so that is would become SDA, and booted Windows, and selected the Ubuntu Partition. It actually went into the GRUB menu - I selected Ubuntu, then It died.

(I swapped the SATA cables back to what they originally were to get the above output.)


Thanks,

M...

---

### Post by oldfred on 2013-03-08
Tried adding code tags to see if it would format like when you ran it in terminal & it partially did it.

May be best to see all the details.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Mike Green9 on 2013-03-17
Hi oldfred.

I finally managed to resolve the problem of copying my ubuntu partition to another partition on another drive, and allow it to be bootable.

I used gparted to copy sda4 to sdb4. And that's it. Initially I then changed the UUID using gparted, and when I tried installing grub to sdb4, I got strange errors as described above.

However, if I leave the uuid's the same (gparted will make the 2 uuids equal to the source), it works fine, as the gparted copy took care of sectors 1 to 64 where I assume grub resides.

To test if it works, I removed the source drive, and plugged in the destination as 'drive 1'. I boot sda1 (windows) where I have the option to boot ubuntu (now sda4). Works like a charm.

Both drives will not be physically hooked up at the same time - only when I choose to do another backup. In fact, before I start the next backup, I will first change the uuid of the destination to be sure that gparted will start off correctly.

I sort of understand why uuids are used, but for my home system, it sure would be nice to have the system just use devices like sda*.

Thanks for your help. I will mark this post as solved.


M....

---

### Post by oldfred on 2013-03-17
We really do not recommend device any more, but you can use UUID, device or labels. And you can do that in both fstab or grub(I think).

         [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Device: /dev/sdxy 
Label : LABEL=label

---

