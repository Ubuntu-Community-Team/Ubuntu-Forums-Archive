---
title: "file ownership/backup via livedisk"
date: 2015-05-24
forum: General Help
---

### Post by JamButty on 2015-05-24
My 14.04 Ubuntu is on the fritz (will not continue after login acceptance), so I will need to wipe and reload for the second time in a year for this same problem.
The issue is the backup before the wipe. I am using Brasero via the install disk, but somehow many of my most critical documents have become group=no access and, since I am not recognized as owner, I cannot normally back them up.

Any workarounds for this to backup those access= owner only files?
thanks

---

### Post by Rex Bouwense on 2015-05-24
Can't you copy them to a flash drive once you have booted from the CD?  That is how I saved my sister-in-laws files when her machine decided to die.  It doesn't always work but I managed to get her files.

---

### Post by ajgreeny on 2015-05-24
The live DVD install disk will always have this problem as the user on a live system is "ubuntu", not "jambutty" or whatever your username is on the borked install and you will not therefore have permission to do anything except read the files; maybe not even read, if your old home had more restrictive permissions set.

You can, however, as root using a live system, copy the files and folders from the old home folder by mounting the old home and then using the cp command to copy to a USB flash drive.  You will have to do this as root so the command will be something like ```
sudo cp /media/lubuntu/path/to/old/home/* /media/lubuntu/path/to/USB
```

You could also do it with the file manager with command ```
sudo -H pcmanfm
```to open pcmanfm with root permissions.

Using a live system there is no password needed for sudo, simply the sudo command followed by "Enter".

---

### Post by JamButty on 2015-05-25
eeesh. A lot of fumbling with the path. I could not refer to the source device as it is known to fdisk "/dev/sda5" nor as the graphic file manager knows it (pcmanfm not a default part of the livedisk) "183 GB Volume" but only by what I guess is the physical hard disk serial number thus insane lines like

> sudo cp /media/ubuntu/ce99ca80-8279-4950-8a87-835919efa28d/home/  etc....

but that did get the files copied over to an external hard drive, so progess. Now those files which, as user "Ubuntu", I had no read access to, I am now the owner of on the new copies on the ext. HD (ex   -rw------- 1 ubuntu ubuntu). Great. Now to open up that access so I won't be locked out of those files again after I wipe and reload the system. other=Read+write . nope...will not allow me, now the owner, to change the access permissions.
Using the graphical file manager, the "read and write" pops up for a half second, then goes back to "none". Using command line e.g. (with or without sudo the same)
> chmod ugo+rw '/media/ubuntu/Doh/holddocuments/other usergroups.txt'
no error is shown but nothing changes. I am still baffled.

---

### Post by ajgreeny on 2015-05-26
Your external drive is probably formatted to either FAT32 or NTFS, neither of which understand Linux file permissions, so when you eventually copy those files back to a new Linux OS as user, not as root, they will all automatically thake ownership of the user who copies them, ie , you.

If you want, or need, to keep Linux file permissions when copying files and folders to a FAT32 or NTFS disk you will have to first archive all the files and folders as a zip file or more likely in Linux, a tar.gz or other archive type.  When the archive is later copied back to the Linux file system and extracted, everything will have retained the original file permissions.

---

### Post by JamButty on 2015-05-30
Reload/restore done with minimal data loss. Thanks for help ajgreeny!

---

