---
title: "File ownership issues"
date: 2012-12-10
forum: General Help
---

### Post by Anaxagore on 2012-12-10
Hi,

After I plugged in one of my USB flash drives, I found out that I had read access but no write access (all options to create folders, rename files, etc. were greyed out).

Somehow the owner of all files and folders was set to root. The flash drive was auto-mounted to /media/floppy

I opened a command line, went to /media/floppy and tried
sudo chown myname *

but the result was
chown: changing ownership of `Folder1': Operation not permitted

for each and every file and folder. I tried the same thing graphically, with 
gksudo nautilus
then right-clicked on the first folder and went to the properties/permissions tab.
It showed the following:
Owner: Me; access: create and delete files
Group: root; access: access files
Others; access: access files

If I try changing "Me" to myname, I get the message: "Sorry, could not change the owner of 'Folder1': Error setting owner, operation not permitted"
If I try changing "root" to the myname group, I get: "You do not have the permissions necessary to change the group of 'Folder1'"
If I try changing the "access files" associated to the group to "create and delete" files, it automatically resets to "access files" only.

How come I am not able to change the ownership of files even after using sudo?? Is there any solution for me to gain ownership of the files, i.e. avoid using root access if i want to copy anything to my flash drive, or even just rename a file or folder?

Thanks in advance for your help!!

---

### Post by Bucky Ball on 2012-12-10
I'm presuming it is NTFS or probably FAT format? File permissions are set when the device is formatted I believe and you can't change them the way you are trying to. Those commands (chown for instance) won't work on that file system.

You might try accessing it as root, backing up anything you need, getting out of root then formatting it again (right click>format or with Gparted). See if that makes any difference.

---

### Post by CaptainMark on 2012-12-10
+1 to that, your flash drive is mounting read-only its not a permissions of ownership problem

---

### Post by JKyleOKC on 2012-12-10
Try this:```
sudo mount /media/floppy -o rw,remount
```Be sure that the flash drive is plugged in and readable before doing so, and change "/media/floppy" to the actual path to the flash drive if it's different.

This command will re-mount your flash drive in read-write mode, although it will still be owned by root. You can add options to make yourself the owner and to grant permissions to others, if this works for you.

Forcing an override in this way preserves the device's compatibility with other operating systems, which would not be the case if you reformatted it. The "remount" capability is extremely powerful, although not widely known!

---

### Post by Rebelli0us on 2012-12-10
Canonical should publish root's name & phone number so people can call him directly.

---

