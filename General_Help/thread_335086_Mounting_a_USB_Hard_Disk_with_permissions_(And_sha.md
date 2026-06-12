---
title: "Mounting a USB Hard Disk with permissions (And sharing with Samba)"
date: 2007-01-09
forum: General Help
---

### Post by ThatOtherGuy435 on 2007-01-09
Hello all. I have had a bear of a problem with mounting an external USB hard drive.

Ubuntu Edgy detects and automounts it fine, but it mounts it with 500 permissions - I use that hard drive as a movie and music share to my network, and I therefore need it to mount at least as 555!

The catch is that the drive is formatted with NTFS, so I can't do a chmod -R on it, or anything like that.

A friend of mine suggested a udev rule for mounting usb disk devices, but I do not know how to use udev rules in the slightest.

A corallary of this is then taking that and sharing it with Samba to my Windows machines. I also have some physical (SATA and IDE) drives with folders shared through Samba. I can connect to the hosting machine, and get a list of directories - But trying to enter into any of said directories gets me a "<network path> is not accessible. You might not have permissions to use this network resource. Contact the admin... The network path was not found." These drives are mounted as 551, and are formatted NTFS. I suspect I will run into exactly the same problem with the USB drive, even once it is mounted 555.

I am not running Firestarter, so nothing is flat blocking samba ports as far as I am aware.

Any help is much appreciated.

-That Other Guy

---

### Post by dcstar on 2007-01-10
> **ThatOtherGuy435 said:**
> Hello all. I have had a bear of a problem with mounting an external USB hard drive.

Ubuntu Edgy detects and automounts it fine, but it mounts it with 500 permissions - I use that hard drive as a movie and music share to my network, and I therefore need it to mount at least as 555!

The catch is that the drive is formatted with NTFS, so I can't do a chmod -R on it, or anything like that.

A friend of mine suggested a udev rule for mounting usb disk devices, but I do not know how to use udev rules in the slightest.
........
Any help is much appreciated.

-That Other Guy

I have an external USB stick that I have an EXT3 FS on that I have labeled (using tune2fs).

I also have the same name as the label in my /media directory, so it mounts on that particular point - and the permissions are what I have set on the mount point.

You may want to try this with your drive and see if it works for you (not sure with NTFS).

---

### Post by ThatOtherGuy435 on 2007-01-12
I did give this a whirl, and unfortunately it did not work :(

I would just change it to ext3, except that it will, on occassion, interface with WinXP systems that will not have any kind of ext interpreter on them. I can set my own machines up with fs-driver, but my friends often don't even know what a driver is.

-ThatOtherGuy

---

### Post by ThatOtherGuy435 on 2007-01-16
I did end up getting this (sortof) solved - I had to set 
force user = myusername
force group = myusername
and suddenly I can see all. Apparrently there's just bugger all permission problems with NTFS drives and sharing.

---

### Post by madams11 on 2007-01-22
> **ThatOtherGuy435 said:**
> I did end up getting this (sortof) solved - I had to set 
force user = myusername
force group = myusername
and suddenly I can see all. Apparrently there's just bugger all permission problems with NTFS drives and sharing.

Could you tell me how you implemented this solution?  I have the same problem with my usb external hard drive.  That is, where do I put these force commands?

---

### Post by BrowneR on 2007-01-23
I have a FAT32 USB drive which has been auto-mounted by edgy at /media/EXTERNAL/

It has permissions 700 which is fine for normal use and i can even **browse** its contents remotely via samba without problems.

However if I want to **mount** it remotely via smbmount I get an access denied message when trying to browse it. It mounts fine so I guess the problems arise because the samba useron my local machine doesn't have access to the drive (permissions 700).

Where is the script that auto-mounts usb devices located? What daemon handles this process?
If I can get access to that then I should be able to have it mounted with different permissions.

Cheers

---

