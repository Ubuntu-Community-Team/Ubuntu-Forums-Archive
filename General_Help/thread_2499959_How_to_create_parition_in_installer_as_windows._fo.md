---
title: "How to create parition in installer as windows. for Store your data without worry"
date: 2024-08-16
forum: General Help
---

### Post by 123nbom on 2024-08-16
How to create parition in the installer as windows. for Store your data without worry
in windows you can create parition:E  and store your data there without worry. but in ubuntu that is too very hard for any user i have no idea what to use /home or /data im not sure, i want similar step to windows.

Short question:
how to create a parition E as windows for ubuntu without worry about your data will be lost later.

also give short answer.

im just user that store data in parition.

---

### Post by ajgreeny on 2024-08-16
Whilst installing the OS you can create a separate /home partition which will then be used to store both all your data files and also much of your personal configuration for the OS and the applications installed for your use.

However, you can not when installing the OS create a separate /data partition which will be used without further configuration to store just your data files without all the configuration folders and files that are in your /home.
Once you understand how the Linux filesystem works it is not too difficult to create a /data partition after installation, give it appropriate permissions, and populate it with folders to which you can then create symbol links in your /home but actually leave all the data folders and files in that other /data partition.

It is not as difficult to do as you seem to suggest though if you are still a new Linux user you will need to spend some time learning and understanding how the Linux filesystem and permissions work, which is, as you have said, very different from Windows.

Personally I use a separate /home partition in which I have all my configuration and data files.
Tell us which you want to use and we can give you more detailed information.

---

### Post by 123nbom on 2024-08-16
Thank you.
 I now understand that I must keep the default folders in  /home, and create a folder and store all my data there.

---

### Post by dragonfly41 on 2024-08-16
If you have Windows and Ubuntu (dual boot) another option I use is to create an NTFS format partition to SHARE files between Windows and Ubuntu.

---

### Post by yancek on 2024-08-16
Creating a separate /home partition during installation is pretty simple and is explained at the link below.  Scroll to the bottom of the page.  You can also create a data partition in the same manner if you want.  Just create a mount point for it as explained at the site linked below.  Most applications will not be installed on a /home partition.  It is used for some configuration files and personal data so if you want just data, create a separate data partition wherre you can store movies, photos, music and other personal files.  The link below is to the Dell site but that doesn't matter.

[URL="https://www.dell.com/support/kbdoc/en-us/000131391/how-to-install-ubuntu-with-multiple-custom-partitions-on-your-dell-pc"]https://www.dell.com/support/kbdoc/en-us/000131391/how-to-install-ubuntu-with-multiple-custom-partitions-on-your-dell-pc


[/URL]

---

### Post by werewulf75 on 2024-08-16
> **yancek said:**
> Creating a separate /home partition during installation is pretty simple and is explained at the link below.  Scroll to the bottom of the page.  You can also create a data partition in the same manner if you want.  Just create a mount point for it as explained at the site linked below.  Most applications will not be installed on a /home partition.  It is used for some configuration files and personal data so if you want just data, create a separate data partition wherre you can store movies, photos, music and other personal files.  The link below is to the Dell site but that doesn't matter.
The article in that link is poorly written, vague and inaccurate in part, and the illustrations are wrong in part, so it's little help to the OP I fear. It also makes it seem more complicated/difficult than it really is. I'm sure there is a good guide to it somewhere...

---

### Post by oldfred on 2024-08-16
I used to use shared NTFS data partition.
I prefer to leave  unallocated space on drive after install and even after adding data partition(s) for future use if drive is larger.

I use gparted and format NTFS. I label all partitions, particularly those I do not always mount, so a default mount uses label not UUID.
Then create mount point and add entry to fstab.
Best to copy a good example of fstab entry and adjust for your UUID and mount point. Parameters for NTFS are important.
And NTFS does not support Linux permission, so default mount sets ownership (usually root) and permissions (bit more open, so you can use easily).

Mount parameter examples, ext4, NTFS, exFAT:
[https://ubuntuforums.org/showthread.php?t=2464668](https://ubuntuforums.org/showthread.php?t=2464668)
[https://ubuntuforums.org/showthread.php?t=2467566](https://ubuntuforums.org/showthread.php?t=2467566)
NTFS example fstab entry - TheFu
[https://ubuntuforums.org/showthread.php?t=2493845](https://ubuntuforums.org/showthread.php?t=2493845) & 
[https://ubuntuforums.org/showthread.php?t=2499276](https://ubuntuforums.org/showthread.php?t=2499276)

Several examples:
Do not confuse label with mount point. They can be same or different. I once confused data & Data which are different in Linux.
FSTAB Uses Label, not UUID. You then are responsible for unique labels.
sudo mkdir /Recordings
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
LABEL=Recordings   /Recordings    ntfs nodev,windows_names,nosuid,noatime,async,big_writes,uid=1000,gid=1000,fmask=0002,dmask=0002  0   0

Good example of manually mounting, 
For ntfs UUID shown is example only see below:
sudo mkdir /media/WinD
sudoedit /etc/fstab
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,gid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

