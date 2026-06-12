---
title: "[SOLVED] Neebie can not copy"
date: 2008-07-05
forum: General Help
---

### Post by majikhotline on 2008-07-05
Hello ubuntu country,
I can not copy a file to my flask stick, i get the error :Read-only file system.
1 what does this mean
2 how can i fix it so i can copy a file to my flack stick
3 how do i prevent this from happening again

thanks

---

### Post by joshsmith on 2008-07-06
i think probably the folder where the flash disk is mounted doesnt have write permissions. so change it with chmod
the disk will be mounted in /media/something where something is disk or similar, so check for the folder in nautilus

so run 
sudo chmod 777 /media/something
in the terminal

---

### Post by issih on 2008-07-06
A curious one, generally flash disks are fat or fat32 format which should be mounted read write by default.

If you right click on the desktop icon representing your flash drive, and select properties, then go to the volume tab, what file system is on the stick?

If its ntfs, I'm not 100% sure ubuntu provides read write drivers for that format out of the box. They certainly are available, but you may have to install a package if that is the problem..

---

### Post by DGortze380 on 2008-07-06
> **joshsmith said:**
> i think probably the folder where the flash disk is mounted doesnt have write permissions. so change it with chmod
the disk will be mounted in /media/something where something is disk or similar, so check for the folder in nautilus

so run 
sudo chmod 777 /media/something
in the terminal

this should work, but there are more secure ways to do it. 777 is a world writable file and leaves you vulnerable to attacks from the outside or even just other users on your system making changes by mistake or otherwise.

Try this (commands in italics):

*cd /media*
*ls -al*

paste the output of that command here.

if it looks something like -r-------- /yourUSBstick, then you don't have permissions for the drive.

If thats the case, try this:

*chmod 700 yourUSBstick*

this gives you read/write/execute privileges but no one else has access (except root ofcourse)

---

