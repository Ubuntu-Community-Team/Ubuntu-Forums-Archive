---
title: "Partitioning - Removal of OS &amp; its parts &amp; then grow Ubuntu"
date: 2016-07-15
forum: General Help
---

### Post by xcdx100 on 2016-07-15
Hello! A few days ago SteamOS failed on me. Many files became broken. I want to remove it & its partitions & then grow Ubuntu's partitions with that released space. I have provided an attachment screenshot of my current partitions. 

```
sda1 is SteamOS's root directory (which I want to remove)
sda5 is ?
sda6 is linux-swap
sda7 is SteamOS's users' directories (which I want to remove)
sda8 is Ubuntu's directory (which I want to grow)
sda9 & sda10 are just empty partitions
```

So here is what I want to accomplish:

1. Removal of SteamOS's partitions2. New 'boot' partition(belonging to Ubuntu)
3. Grow Ubuntu's partition
*4. Move Ubuntu's '/home'directory to its own partition (if its advisable)

Could anyone guide me through the steps to perform these actions? :KS
I am still new to Linux & have not had the time to educate myself enough to handle this.

Thanks in advance you  :guitar:!

---

### Post by grahammechanical on 2016-07-15
You have MBR partitioning. This means that you are allowed only four primary partitions. Two of the primary partition allocation is already used up by sda1 & sda2 which is a special primary partition called an extended partition. Inside the extended partition (sda2) there are six logical partitions.

The key icons against all the partitions indicates that you cannot delete or resize those partitions. So, run GParted from alive session. The live session will still use the swap partition and that will lock the extended partition (sda2) and all the logical partitions inside it. You need to select the swap partition (sda6) and use the menu system to take "swap off." Now you can delete/resize/move partitions.

You need to decide how you are going to proceed afterwards. Why do you want a boot partition? One possibility

(1) Move any data in Ubuntu (sda8) into sda10 (empty partition). (2) Delete sda 5  (3) Delete sda7. That will create 158.81 GiB unallocated space in front of sda8 (Ubuntu). (4) move sda 8 to the front of the Extended partition. That will put the unallocated space behind sda8. (5) shrink sda8 to 30 - 35 GiB. (6) close GParted. (7) Re-install Ubuntu.

Used the Something Else option and (7a) give sda1 the mount point of /boot. (7b)  Give the previous Ubuntu partition (what was sda8) the mount point of /. (7c) Give what was sda9 the mount point of /home.

(8) After re-installation move the data from what was sda 10 into Ubuntu. (9) Run the live session again. Take swap off. (10) Delete what was sda10. (11) Resize the Ubuntu home partition to take up all the unallocated space.

Regards

---

### Post by xcdx100 on 2016-07-16
**[COLOR=#000000][grahammechanical]("https://ubuntuforums.org/member.php?u=1087323"), I appreciate your help! I now know a little more on how partitioning works. Thanks for lending me some *logic*.[/COLOR]**

---

### Post by grahammechanical on 2016-07-16
This is the guide for GParted

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted will lets us queue up actions. But resizing and moving partitions will take a long time. So, I like to complete each task one by one. Are you familiar with using the Something Else option? All Ubuntu flavours use the same installation methods. This is the Ubuntu Mate installation guide. It shows the screens and dialogs that we see when using the something Else option.

[https://ubuntu-mate.community/t/install-ubuntu-mate-using-something-else-method/651](https://ubuntu-mate.community/t/install-ubuntu-mate-using-something-else-method/651)

We select a partition and click Change. Then in the dialog we set Use As to Ext4. We tick to format the partition. then we set a mount point. There is a drop down menu. So, the boot partition will have a mount point of /boot. The Ubuntu partition will have a mount point of /. And the home partition will have a mount point of /home. The installer will automatically use an existing swap partition.

Regards

---

### Post by oldfred on 2016-07-16
If you want /home in a separate partition, this has detailed instructions on copy & edit of fstab.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 

I prefer to do clean installs and restore from my backups /home. 
But I have all data in a separate /mnt/data partition (separately backed up) and just have to remount that to have all my data in new install.

---

