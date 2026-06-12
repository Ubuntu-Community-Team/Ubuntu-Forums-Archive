---
title: "Files missing on second drive after reinstalling on first drive"
date: 2008-02-17
forum: General Help
---

### Post by wraith@nc.rr.com on 2008-02-17
I have a Ubuntu 7.10 Server with 2 drives in it. One drive, SDA has the OS on it. The other, SDB, is large drive for mass storage. I ended up needing to reinstall Ubuntu on SDA, and now that I have, all the files on SDB aren't showing up after I mount it, and do a "ls -la".  What's weird is that the drive is mounted, and the top level directories are still there, but the files under them are gone.

ie :

The second drive is mounted under /mnt/storage. If I do a "ls -la /mnt/storage" I see a list of directories, DIR1, DIR2, DIR3, etc... However, all the files that should be under DIR1, DIR2, DIR3 don't show up. 

I don't get it. If I accidentally formatted SDB, the directories wouldn't be there, so that can't be it. Where did the files go? All I did was reinstall Ubuntu on SDA. That shouldn't have affected SDB. Hmmm.

Any ideas anyone?

---

### Post by sb12 on 2008-02-17
> **wraith@nc.rr.com said:**
> I have a Ubuntu 7.10 Server with 2 drives in it. One drive, SDA has the OS on it. The other, SDB, is large drive for mass storage. I ended up needing to reinstall Ubuntu on SDA, and now that I have, all the files on SDB aren't showing up after I mount it, and do a "ls -la".  What's weird is that the drive is mounted, and the top level directories are still there, but the files under them are gone.

ie :

The second drive is mounted under /mnt/storage. If I do a "ls -la /mnt/storage" I see a list of directories, DIR1, DIR2, DIR3, etc... However, all the files that should be under DIR1, DIR2, DIR3 don't show up. 

I don't get it. If I accidentally formatted SDB, the directories wouldn't be there, so that can't be it. Where did the files go? All I did was reinstall Ubuntu on SDA. That shouldn't have affected SDB. Hmmm.

Any ideas anyone?

whats the file system on sdb

---

### Post by tact on 2008-02-17
What if you  do sudo ls -la ??

If all the files show up then you have a permissions/ownership problem.  chown and chmod become your friend.  :)

---

### Post by wraith@nc.rr.com on 2008-02-17
I believe the filesystem on SDB is ext3. I also thought of a permissions problem, but even as root, I don't see any files under the directories. This is really weird.

Here's how my fstab looks :

/dev/sdb1 /mnt/storage ext3 defaults 0 2 

And fdisk reports the filesystem as "LINUX"

---

### Post by sammydee on 2008-02-17
Have you tried loading up a livecd and looking seeing if you can see your files on the storage drive from there?

Sam

---

### Post by wraith@nc.rr.com on 2008-02-17
I haven't. That's a good idea.

---

### Post by wraith@nc.rr.com on 2008-02-17
Here's another interesting tidbit. It's a 250GB drive, but for some reason "df" shows this :

/dev/sdb1             230G  188M  218G   1% /mnt/storage

even though a "du" says that only 32K of the partition has been used. 

"sudo du -sh
32K "    .

:confused:

It's almost as if the files are in some limbo partition that linux can't see. I'm stumped.

---

### Post by tact on 2008-02-17
> **wraith@nc.rr.com said:**
> Here's another interesting tidbit. It's a 250GB drive, but for some reason "df" shows this :

/dev/sdb1             230G  188M  218G   1% /mnt/storage

even though a "du" says that only 32K of the partition has been used. 

"sudo du -sh
32K "    .

:confused:

It's almost as if the files are in some limbo partition that linux can't see. I'm stumped.

You can't use du on /dev/anything.  Any drive/partition will give that result.

First mount the partition somewhere  (you know how?) e.g. mount /dev/sdb1 on /media/test and then do a du on /media/test

"ls" is the same...  cannot "ls" on /dev/anything...   mount partition first and then "ls".   Otherwise you get the kind of results you seem to get.

[Oops - edit]
Ok I see your /dev/sdb1 is mounted on /mnt/storage

So when you do your "du" or "ls" you do it on /mnt/storage not on /dev/sdb1 - correct?   and you still get the unhappy result that your files seem to be missing?

---

### Post by wraith@nc.rr.com on 2008-02-18
Correct. I was doing the "du" and "ls" on "/mnt/storage." The files just don't show up. I think I'm going to have to accept the face that the files are gone and just redo the partition. :(

---

### Post by tact on 2008-02-18
> **wraith@nc.rr.com said:**
> Correct. I was doing the "du" and "ls" on "/mnt/storage." The files just don't show up. I think I'm going to have to accept the face that the files are gone and just redo the partition. :(

*ouch*  sorry I am out of ideas now.

---

