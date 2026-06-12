---
title: "Strange problem with FAT32 partition"
date: 2006-07-07
forum: General Help
---

### Post by Sciamano on 2006-07-07
Hello everybody.
I woke up this morning to find my Thunderbird on Ubuntu complaining because it could not write on the disk.
My mail resides on a FAT32 partition, so that I can share it with the Windows installation of Thunderbird.

I know what you are thinking: "oh, no... just another fool who can't read the wiki guides about assigning the right permissions". But this is not the case! 
I gave the right permissions to this partition, and it worked perfectly until this morning, when -as I said- I woke up just to find a lot of error messages coming from Thunderbird.


This is the fstab line to mount the fat32 partition:

/dev/hdb2       /media/fat    vfat    iocharset=utf8,umask=000 0       0

I've also tried the following because I read somewhere that it would be better to write 4 zeros in the umask parameter, but that changed nothing:

/dev/hdb2       /media/fat    vfat    iocharset=utf8,umask=0000 0       0

Also, if I check the permissions of the subfolder "fat" in the "media" folder, or those of the folder that contains my Thunderbird profiles and mail, I can see that I have all the rights (drwxrwxrwx), but still I can't write on the disk (I can't either create a new folder nor delete a file).

Any idea on how to solve?
Thanks!
Luca

---

### Post by Sciamano on 2006-07-07
Solved. Some files in the FAT32 partition got corrupted somehow.
Had to go in Windows and launch a "chkdsk /f" command to get things back to normal.
Hope this information can help someone in the future.

---

### Post by Hansers on 2006-07-08
I have also encountered problems with my fat-drive shared with a dual booted windows xp. I make folders and save files on the disk in Ubuntu Dapper, but when I reboot into xp the files and folders are gone. I get error messages that ask me to run chkdsk, which I haven't tried jet.

Hmmm...

---

### Post by Sciamano on 2006-07-08
try to run chkdsk.
It worked for me.

---

### Post by pitkali on 2006-07-08
> **Hansers said:**
> I have also encountered problems with my fat-drive shared with a dual booted windows xp. I make folders and save files on the disk in Ubuntu Dapper, but when I reboot into xp the files and folders are gone. I get error messages that ask me to run chkdsk, which I haven't tried jet.

Hmmm...
I can only hope you do not write to fat partitions and switch between windows and linux through hibernation option, because that's exactly what happens then (windows do not "unmount" its partitions upon hibernation and so it does not see any changes made to them after being awaken).

Regards,

---

### Post by Hansers on 2006-07-09
Aha! That is it. Runninf chkdsk [drive:] /F now. I'll see oif that corrects it. Will never do this again :-)

---

