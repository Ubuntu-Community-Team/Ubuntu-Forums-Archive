---
title: "superblock corrupted"
date: 2006-10-15
forum: General Help
---

### Post by 7he on 2006-10-15
Hi guys!

This morning when I booted my computer, Ubuntu told me it had to check my hard drives because they were mounted 30 times without check.
Then I got an error telling me my superblock may be corrupted.

I tried the command they recommended to me:
e2fsck - b 8193 /dev/hdb

But it doesn't work.

fstab:
/dev/hdb1 /media/hdd2 ext3 defaults 0 2

Anyone an idea?

Thks

---

### Post by 7he on 2006-10-15
Found some very useful info's at that address:

[http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=503&st=200](http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=503&st=200)

I did want to test the tips but:
I powered my computer on, and it seems to be blocked: 

*checking all filsystems
/dev/hdb1 has been mounted 30 times without being checked, check forced.
/dev/hda4: clean .....
/dev/hda2: clean ..... 

and nothing more is coming... Do I have to wait?

---

### Post by 7he on 2006-10-15
The problem is resolved!
I just waited about 15 minutes, and now everything seem to work! It seems there's no data loss!

THANK YOU UBUNTU !!!

So, if you have the same problem I had, 
wait the time it 'll need when booting, even if there no message nor progressing bar...
If it doesn't repair your problem , then try the following guide

[http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=503&st=200](http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=503&st=200)

Bye!

---

