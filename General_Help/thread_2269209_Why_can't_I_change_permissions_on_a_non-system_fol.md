---
title: "Why can't I change permissions on a non-system folder?"
date: 2015-03-14
forum: General Help
---

### Post by KayeNg on 2015-03-14
My harddisk has four partitions:

PRIMARY PARTITION
------First partition = Windows 7

EXTENDED PARTITION
------Second partition = Data partition
------Third partition = Lubuntu LTS
------Fourth partition = swap

I open terminal, typed in "sudo pcmanfm" to open the file manager as root (please correct me if I'm wrong, newbie here)
Inside the file manager, I navigate to /media/homet/Data (which is actually the Second partition stated above), right click on a certain folder, click properties, go to Permissions tab, changed the following:

View content:
Change content:
Access content: 

to "Anyone", click OK, exit the file manager.  But when I go back and check the permissions, they're back to "Only Owner"

Why is that?

---

### Post by kerry_s on 2015-03-14
it's a separate partition, it go's by how it's mounted, check your /etc/fstab

---

### Post by CaptainMark on 2015-03-14
Please provide a little more information about the drive, it may be its file system or how its mounted. If its shared with Windows then to my knowledge neither vfat nor ntfs support file permissions.
Post the output of these commands
```
sudo fdisk -l
cat /etc/fstab
lsblk

```

Additionally you shouldn't launch graphical applications with sudo, you should instead use gksudo or gksu or pkexec depending on which is installed.

---

### Post by KayeNg on 2015-03-14
Thanks, it is an NTFS, maybe that's the reason why.

---

### Post by CaptainMark on 2015-03-15
Okay, so you won't be able to do anything with ownerships or permissions because NTFS simply doesn't support it. As long as you have read/write access then that's all you can do.

---

