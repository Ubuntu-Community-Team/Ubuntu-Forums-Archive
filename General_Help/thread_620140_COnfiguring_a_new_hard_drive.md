---
title: "COnfiguring a new hard drive"
date: 2007-11-22
forum: General Help
---

### Post by Broodmdh on 2007-11-22
I recently added a new hard drive that is intended to be shared amongst the various computers in my home network.  I formatted the drive to fat32, and thought that I had set it up properly to work with samba, but I don't think that is the case.  When I try to add a directory to the drive I get the following error:

mkdir: cannot create directory `Media_Files`: Permission denied

After a little digging I found something that I thought would enable me to set the permissions, but that didn't work either.  This is what I tried:

/media/networkdrive$ sudo chmod -R a+rw *
chmod: cannot access `*': No such file or directory

I basically want all users (I guess they would be anonymous, but I'm not really sure if that is how it works) on the network to have read and write access to this drive.  Help would be greatly appreciated.

---

### Post by mpierce on 2007-11-22
First of all, you need to provide some additional information, i.e.,
  1) is the drive attached to your linux computer
  2) is the drive USB

Try mounting your drive and creating your directory as the root user, i.e., 
    sudo mkdir /media/usbHD/Eraseme

This will then tell you if it is a permissions problem that will need to be corrected in your fstab file. 

I'll bet you can only mount the drive as root and that this is the problem.

Hope this helps you...

---

### Post by Broodmdh on 2007-11-22
The drive is just a typical Maxtor Internal SATA drive.  I don't know what I am doing differently, but I now seem to be able to make the directory and set the permissions.  Is there anything else that I need to do to get this drive to work with samba?

---

### Post by mpierce on 2007-11-22
Here is how my USB HD is setup in my fstab: 
   //dellbook/G$   /media/lacie320 smbfs   rw,users,uid=mpierce,noauto,credentials=/home/mpierce/.smbpasswd

The drive is automatically mounted when I start my Linux computer or root can mount/umount the drive at any time. (The mount command does not know anything about smbfs - this is technical.)

My entry gives rw (read/write) access to all users, e.g.,
  rw,users,

By using uid=mpierce, the drive will always have me as the owner first in the permission, e.g.
   sudo mkdir /media/lacie320/Eraseme
   ls /media/lacie320/Eraseme -al
   total 8
   drwxr-xr-x 1 mpierce root 4096 2007-11-23 01:49 .
   drwxr-xr-x 1 mpierce root 4096 2007-11-23 01:51 ..

credentials=/home/mpierce/.smbpasswd - this file has two entries to log onto my XP USB HD:
  username=myusername to log on
  password=mypassword to log on

This permission on this file is 600 mpierce.mpierce so that no one but me can read the logon password. 

Hope this helps...

---

