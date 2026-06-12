---
title: "Partitioning problem"
date: 2005-10-28
forum: General Help
---

### Post by MichaelM on 2005-10-28
Hi,
I wanted to create a new FAT partition to share data between Windows and Ubuntu. I already had main and swap partitions in both, and apparently the maximum number of partitions is 4 (I had an extended partition, but I couldn't get it to expand). So I moved Windows's swap file to its main partition and deleted the swap partition.  Then I rebooted, and GRUB wouldn't load (Error 17). I booted the Ubuntu install CD in rescue mode and, after trying several other things (like regenerating menu.lst), I tried fdisk -l /dev/hdc.
It shows 4 functioning partitions (including the extended one), and one odd one:```
Device         Start        End        Blocks       Id    System
/dev/hdc5      88950      188196      797190399+     c    W95 FAT32 (LBA)
```
This is a 60GB HD, and the previous partition (hdc4) ended at 5620. Also, I don't have any FAT partions.
So I tried to use parted to delete the partition, but it said: "Error: Can't have a partition outside the disk!"

Can anyone help? :confused:

Michael

---

### Post by Remmelas on 2005-10-28
well, i'm not sure i can help with the issue, but an observation.  it's likely that /dev/hdc4 is your extended partition, and /dev/hdc5 resides within that partition.  I'm not sure what you have living on hdc5, but if it is a partition living on hdc4 extended, you'll not be able to delete your extended partitoin until you delete hdc5(which, you may not really want to do)

as far as fixing grub, i usually boot from a rescue disk of some sort, mount my linux partition (mount /dev/hdc1 /mnt/linuxmnt), hdc1 is of course particular to my machine, not necessarily yours, mount fstab on the linux partitions root (mount -t fstab fstab /mnt/linuxmnt/fstab), chroot into it (chroot /mnt/linuxmnt /bin/bash), then install grub from the command line.

---

### Post by MichaelM on 2005-10-28
> well, i'm not sure i can help with the issue, but an observation. it's likely that /dev/hdc4 is your extended partition, and /dev/hdc5 resides within that partition. I'm not sure what you have living on hdc5, but if it is a partition living on hdc4 extended, you'll not be able to delete your extended partitoin until you delete hdc5(which, you may not really want to do)Yes, hdc4 is the extended partition.  However, I just now tried to remove it, with the same result.  Are you saying that I have to remove one to remove the other, and I have to remove the other to remove the one?  :confused:
> 
as far as fixing grub, i usually boot from a rescue disk of some sort, mount my linux partition (mount /dev/hdc1 /mnt/linuxmnt), hdc1 is of course particular to my machine, not necessarily yours, mount fstab on the linux partitions root (mount -t fstab fstab /mnt/linuxmnt/fstab), chroot into it (chroot /mnt/linuxmnt /bin/bash), then install grub from the command line.
I don't have any rescue disks.  Could I do the same sort of thing with a live CD?

Thanks for your help!

---

### Post by MichaelM on 2005-10-28
It just occurred to me that on the list of partitions, the ext3 disk was hdc3, and in menu.lst, all the kernels boot from (0,3).  Do I need to change it?

---

### Post by Remmelas on 2005-10-28
[QUOTE=MichaelM]It just occurred to me that on the list of partitions, the ext3 disk was hdc3, and in menu.lst, all the kernels boot from (0,3).  Do I need to change it?[/QUOTE]

Yes, earlier i was saying you'd have to remove hdc5 to be able to remove hdc4 if hdc4 is your extended partition.

In regards to kernels booting from (0,3), yeah, that's an issue.  (0,3) would be hda4.  So, unless your boot partition is on partition 4 of your 1st hard disk, you need to change that.  if your kernel image is on hdc3, then (2,2) would be a correct hard drive address in grub, and of course, any pathing in menu.lst file is relative to that.

---

### Post by MichaelM on 2005-10-28
[QUOTE=Remmelas]Yes, earlier i was saying you'd have to remove hdc5 to be able to remove hdc4 if hdc4 is your extended partition.

In regards to kernels booting from (0,3), yeah, that's an issue.  (0,3) would be hda4.  So, unless your boot partition is on partition 4 of your 1st hard disk, you need to change that.  if your kernel image is on hdc3, then (2,2) would be a correct hard drive address in grub, and of course, any pathing in menu.lst file is relative to that.[/QUOTE]
Well, the odd thing is that I've looked in menu.lst before, and as far as I can remember, it always booted from (0,something).
But I tried changing it to (0,2) just now, and it didn't work.  I guess I'll try (2,2) instead. The problem (for me) is that since I'm booting rescue, I don't have a terminal. So, right now, vim is the only text editor I can use, and I find it rather painfully slow to do anything in. :(

---

### Post by Remmelas on 2005-10-28
mount your linux partition, and your proc file system on your linux partition, and chroot into it, that way you've got all your favorite tools

---

### Post by MichaelM on 2005-10-28
Actually, I was operating in my Linux partition.  I ran bash, and it gave me the bash prompt, but I still couldn't run anything that required a terminal.

I am now preparing to back up my /home folder to CD, after which I will boot a Windows CD, restore the MBR, and delete my Linux partitions.  But not to worry, I'm not quitting Linux; this is just a temporary fix to get me through this weekend's homework. :)  I'll reinstall sometime when I have more time.

---

