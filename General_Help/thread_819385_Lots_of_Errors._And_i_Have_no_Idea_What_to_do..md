---
title: "Lots of Errors. And i Have no Idea What to do."
date: 2008-06-05
forum: General Help
---

### Post by momopo on 2008-06-05
Hey,
   i used Wubi to install Ubuntu 8.04 on my Lenovo T60 a few days ago, At first it went well but after i installed the updates and stuff it just went down hill. Im going to try to remember all the errors, here are a few. 

Just a second ago a new error happened, the whole gnome desktop crashed. It gave me this error. Does this have something to do with the fact that my wireless connection notifier just keeps going in circles with the little green dots? 

Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0

^^^ that repeats about 100 times.

PS my internet works fine when using a land line but the wireless is speratic and of poor quality. 


Also on boot up Ubuntu trys to do a "disk data check", when it completes the process it says there has been an era and that ill have to do in manually. However, i can just hit ESC and it boots just fine.

*Fire Fox 3 was crashing but i changed to Fire Fox 2 last night and so far so good.

Also if i leave it on overnight i come back to a black screen with just the cursor movable on screen.

Sorry for all the questions, im a complete Noob but im willing to learn.

Thanks in advance.

---

### Post by momopo on 2008-06-05
Bump

---

### Post by bingoUV on 2008-06-05
The error while booting might have a lot to do with your problems. To fix it, read [http://ubuntuforums.org/showpost.php?p=5038792&postcount=3](http://ubuntuforums.org/showpost.php?p=5038792&postcount=3)

---

### Post by momopo on 2008-06-05
When i do

sudo /sbin/fdisk -l

I get 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xbeaebeae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5061    38261128+   7  HPFS/NTFS
/dev/sda2            5062       12651    57380400    f  W95 Ext'd (LBA)
/dev/sda3           12652       12921     2041200   1e  Hidden W95 FAT16 (LBA)
/dev/sda5            5062       12651    57380368+   7  HPFS/NTFS

And when i do sudo /sbin/e2fsck -c -f <device all i get is, 

bash: syntax error near unexpected token `newline'


I have no idea what that means haha. It says your suppose to make everything under system say linux right?

---

### Post by bingoUV on 2008-06-05
Sorry, did not realize you are on Wubi. No idea how to fix in wubi.

---

### Post by mrMango on 2008-06-05
Bumping your thread more than once every 24 hours will probably sic the mods on you.

You may have more luck in the Wubi support forum.

---

