---
title: "[SOLVED] rsync - exclude does not work"
date: 2007-07-21
forum: General Help
---

### Post by rpw on 2007-07-21
Hello, 
 
somehow the exclude-function in rsync does not work or I'm doing it just wrong.

I'm trying to sync my home folder with rsyn, but I want to exclude some folders, for example cache-folders or icon-folders. 

This is the command I'm using (actually I'm trying to exclude some more fodlers, but this should give you a good example):
 
rsync -av --delete --exclude=/home/ralf/.kde/share/icons /home/ralf /media/SONSTIGES/testbackup/ 
 
But the excluded folder "icons" will still be copied with all its subfolders?! The target folder is on an NTFS-partition, mounted with NTFS-3G in /etc/fstab:

/dev/sda2 /media/SONSTIGES ntfs-3g defaults,locale=de_DE.UTF-8 0 0 

Found a lot of information in google but none of them really helped. IF also tried the "exclude-from=/EXCLUDEFILE" option and created a file containing the folders to exclude, but also without success.
 
Regards, 
 
rpw

************************************************************

Problem solved:

rsync starts from the folder I wanted to sync, so in this case it was looking for a folder "/home/ralf/.kde/share/icons" in my home directory, since this is the startfolder. So rsync was looking for "/home/ralf/home/ralf/.kde/share/icons", which of course was wrong.

Regards,

rpw

---

### Post by kolinab on 2007-09-12
I was having a nearly identical problem. Thanks for posting the solution!

---

### Post by kasperbs on 2007-09-28
Yeah me too, thanks for posting have been tryi9ng to solve this for hours

---

### Post by swoosh on 2007-10-18
Hi,

What will be the correct command for this,

> rsync -raz --progress --size-only --exclude=/home/jerry/test-rsync/exclude /home/jerry/test-rsync/* [server-name]:/home/jerry/network/administrator/test-rsync/ 

I wish to exclude

> /home/jerry/test-rsync/exclude

I have tried so long but couldn't get it right.

Thank you.

---

### Post by kolinab on 2007-10-18
I can only speak for the 'exclude' bit since I'm no rsync guru, but I think you want:

```

rsync -raz --progress --size-only --exclude=/test-rsync/exclude /home/jerry/test-rsync/* [server-name]:/home/jerry/network/administrator/test-rsync/

```

The reason is that rsync assumes you already begin within your home directory. Then why do you have to specify the whole pathname in other sections of the command? I don't know, maybe it's not required.

I think.

Let us know how it goes,

K

---

### Post by swoosh on 2007-10-18
> **kolinab said:**
> I can only speak for the 'exclude' bit since I'm no rsync guru, but I think you want:

```

rsync -raz --progress --size-only --exclude=/test-rsync/exclude /home/jerry/test-rsync/* [server-name]:/home/jerry/network/administrator/test-rsync/

```

The reason is that rsync assumes you already begin within your home directory. Then why do you have to specify the whole pathname in other sections of the command? I don't know, maybe it's not required.

I think.

Let us know how it goes,

K

Yes, you are right, the thread starter is correct. This works for me.

```
rsync -raz --progress --size-only --exclude=/test-rsync/exclude test-rsync [server-name]:/home/jerry/network/administrator/
```

Thanks for the direction K.

---

