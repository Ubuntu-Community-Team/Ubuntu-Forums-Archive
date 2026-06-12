---
title: "I now have write permissions for the WHOLE file system"
date: 2006-10-22
forum: General Help
---

### Post by 16777216 on 2006-10-22
In trying to change the permissions of some files I backed up as root back to  the proper owner I seem to have accidentally gave them write permissions to the whole file system.

how do I fix this?

---

### Post by aysiu on 2006-10-22
Can you explain exactly what you did? What files? What command did you use (if any)? Did you use the GUI instead of the terminal?

---

### Post by scudellari on 2006-10-22
I did the same sort of thing.  My command was:

sudo find / -type d -exec chmod 775 {} \;

Now, every once in a while I try to run something, and it gives me a permissions error.  I can fix it quickly and move on usually, but I want to fix EVERYTHIng.  Is there someway to do this using the install CD?  Some tool that can fix my permissions?

Thanks.

---

### Post by 16777216 on 2006-10-22
OK, background:

I dual boot Ubuntu  and Win XP©.
Two IDE hard drives
XP on hda1 [ntfs] : 
( now ) /media/Backup on hda2 [ext3]
/media/Storage on hdb1 [FAT32]
and the rest of my Linux partitions on hdb2 - 6. 

So XP borks /media/storage by scrambling a directory. ( and I guess something else )
I run XP chkdsk and fix the offending directory.
I need to reinstall XP any way. ( it crashes every 30 min or so )
I decide to redo Ubuntu as well.
I reinstall XP. ( all goes good )
I boot the live CD, run the installer, and QTparted gives some kind of error about hdb and refuses to mount, edit or any thing.
After some trial & error I find that the option of erasing hdb will fix the problem. Oy...
I create /media/Backup
I mount  /home
I copy my wife's and my own home directories to /media/Backup
Reinstall Ubuntu, recreate  her user and mine .
Find out my back ups are owned by root, do a search find " do a chown -L -R user /dir/dir ( user being me or my wife and /dir being the dir to change ownership of )
I do this for her, now she has write permissions for everything.
( this is really bad because as even she puts she is " 'puter 'tupid " ( computer stupid ) )
I use a different method for my files that I can't remember right now, but they are fine.

I think that is about it.

---

