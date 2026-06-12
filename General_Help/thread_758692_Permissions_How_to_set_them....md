---
title: "Permissions??? How to set them..."
date: 2008-04-18
forum: General Help
---

### Post by slicemaster on 2008-04-18
well, here is the deal. I have been using Ubuntu for all of about 12 hours and am impressed by what it can do. I am a little disappointed that certain tools didn't come with the distro, but that is forgivable for most people who have internet access. but anyways, the concept of using terminal and preforming operations that could compromise the main system (namely the root system folder/drive) is a good one but it really gets old to have to do certain thing such as edit system configuration files from the terminal so I was wondering if you can create a short cut on the desktop that will run the file browser  as root, asking for password, I just want to reduct the wasted time of doing simple operations from the GUI. also, I am a little stumped as to how to properly set permissions for a mounted drive, not the system drive but a data drive formated in FAT32 that I use for data that I need to have accessible on my XP install, docs, vids, pics, etc. you get my point. anyways, it is becoming a real hassle because I don't know how to set up the permissions for this drive. I want everyone from this computer to be able to write, read, edit, rename, move, delete, etc. (more or less have root privileges) on that drive. could you please assist in this, not sure how to go about it. thanks

Slice

---

### Post by fguilhon on 2008-04-18
You have to put the following line on your /etc/fstab (make sure to backup this file first, just in case):
```
/dev/hda1 /media/hda1 vfat rw,umask=0,auto  0  0
```
where /dev/hda1 is your fat32 partition and /media/hda1 is the default mountpoint..

---

### Post by JohnFH on 2008-04-18
Hi Slice,

To create shortcuts to GUI applications that require root privilieges, the shortcut command should start with 'gksudo' if you're using Gnome or 'kdesu' if you're using KDE.

For setting permissions of mounted drives, look at your /etc/fstab file which mounts drives at startup.  For full control (everyone has all access), one of the options should be umask=000 when mounting the drive.  See the manpages for mount and fstab for more details.

To don't need to use vim or other terminal editing programs to edit the files, instead type the command 'gksudo gedit /etc/fstab' into the terminal (or create a shortcut with that command).

Hope that helps,
John.

---

### Post by george9233 on 2008-04-18
> **slicemaster said:**
> so I was wondering if you can create a short cut on the desktop that will run the file browser  as root, asking for password
On the desktop right click and click "Create Launcher", then in the "Command" section type
```
gksudo nautilus
```
This shall work.

---

### Post by slicemaster on 2008-04-18
works great, thanks for the help...

---

