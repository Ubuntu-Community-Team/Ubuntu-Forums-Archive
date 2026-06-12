---
title: "[SOLVED] Complete copy of home to external fat-drive?"
date: 2007-08-30
forum: General Help
---

### Post by olavjunior on 2007-08-30
I am going to reinstall my whole system, and therefore need backup of all my files. 
But all my external harddrives are fat. And using rsync gives me many permission denied. 

Any ideas on how to copy all my files, leave the permissions behind and just get ALL of them? Some filenames also causes a problem..

---

### Post by bmorency on 2007-08-30
when you plugged in your external drive it probably mounted it so only root could write to it. did you run rsync as root?

---

### Post by olavjunior on 2007-08-30
I tried doing it as root, but then it stopped almost right away. Didnt notice the errors thoug.. The problem isnt that it doesnt back up, but it skips some files.. and that can be annoying!

---

### Post by kebes on 2007-08-30
FAT and FAT32 don't support some features of the ext3 filesystem that Linux uses. In particular file ownership, permissions, and some filename characters. You can still use rsync to copy files over (or just use a conventional "cp" command), but you will have to drop the "preserve owner" and "preserve permissions" flags.

In short, backing up your /home/ to a FAT drive is not a good idea, because you won't be able to restore it with proper permissions. You would be better creating a partition that is ext3 and backing up there.


Another option is maybe to compress the entire /home/ into a giant compressed file that preserves ownership and permissions (I believe tar can do this). Then this big file (or multiple files if you split it up) can be safely stored on another drive, including a FAT drive.

---

### Post by tszanon on 2007-08-30
I agree on that. Create a tar/tar.gz/tar.bz file, split it in pieces of at most 4GB (the file size limit in FAT) and then save them there in the external drive. This way, you won't lose any metadata about the files.

---

### Post by olavjunior on 2007-08-30
ok, thanks! But whats the problem if the file looses its owner? Cant I just change that later on? I will search for how to tar into split volumes then :)

---

