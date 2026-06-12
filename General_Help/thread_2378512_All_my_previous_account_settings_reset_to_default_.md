---
title: "All my previous account settings reset to default on lubuntu"
date: 2017-11-23
forum: General Help
---

### Post by djdj21 on 2017-11-23
I'm using lubuntu and I logged into my only account, but when I log  on none of my previous edits to my account are there except for some software  applications I installed. My previous files that I had are missing. My  previous browser history is missing. My screen background is missing and  is set to the default screen that was when I initially installed  lubuntu, and the task panel bar also looks like it did when I initially  installed lubuntu. I don't know why this happened and so I don't know  how to prevent it if it happens again. I'm using lubuntu version 17.10.  Is there any way I can restore my computer to the previous state it was  in so I can retrieve my files back? The only thing that is left from my  previous settings are software applications I installed, but everything  else looks like it would when you install lubuntu fresh.

---

### Post by oldfred on 2017-11-23
May have posted same info in AskUbuntu.

Do you have a separate /home?
Post this:
sudo parted -l
cat /etc/fstab

If separate partition for /home run both these commands on that partition:

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by wildmanne39 on 2017-11-23
Please remove askubuntu formatting before you copy and paste your post here.

---

### Post by djdj21 on 2017-11-24
Ottoe@Roedelius:~$ sudo parted -l
[sudo] password for Ottoe: 
Ottoe is not in the sudoers file.  This incident will be reported.
Ottoe@Roedelius:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=0cd5ee34-4360-4d44-b152-dd59fef87bbd /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=BB88-309A  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0


This is my output after I put in those commands. I don't understand what any of this means. What should I do from here?

---

### Post by djdj21 on 2017-11-24
> **oldfred said:**
> May have posted same info in AskUbuntu.

Do you have a separate /home?
Post this:
sudo parted -l
cat /etc/fstab

If separate partition for /home run both these commands on that partition:

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

I also don't know if I have a separate partition, but I don't think I should have one.

---

### Post by oldfred on 2017-11-24
lYou must have more than one user.
As Ottoe is not in sudo users and the admin user must be able to use sudo.

So your other user is where your normal /home files are.
Post this, most will be system users UID 1000 is main user:
id

---

### Post by djdj21 on 2017-11-24
> **oldfred said:**
> lYou must have more than one user.
As Ottoe is not in sudo users and the admin user must be able to use sudo.

So your other user is where your normal /home files are.
Post this, most will be system users UID 1000 is main user:
id

Nevermind I solved it. I log back in and all my previous settings are here. I don't know why this happened but I guess I got lucky. Thanks for helping.

---

### Post by oldfred on 2017-11-24
Glad you got it working.

But then it shows why a good idea to have backups.

---

