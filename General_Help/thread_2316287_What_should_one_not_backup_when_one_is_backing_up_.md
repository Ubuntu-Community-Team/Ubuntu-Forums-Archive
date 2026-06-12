---
title: "What should one not backup when one is backing up the / partition of Ubuntu?"
date: 2016-03-06
forum: General Help
---

### Post by mikodo on 2016-03-06
Hello, everyone!

I've decided to go ahead and backup my / with my ~ which, is really small because of my data being symbolically linked to it from ~ in a /mnt/data partition.

I'll follow [this guide]("https://wiki.archlinux.org/index.php/full_system_backup_with_rsync") over in Arch. I am not going to backup the boot bits. I'll make a small area of sda for it and let the installer use that, if it comes to needing to reinstall. I am going to try to keep the backup of it current with the rsync -- delete option.

Can anyone think of anything that should also be excluded that, would be also be populated in a new install with an .iso of Ubiquity?

Anything here, that I shouldn't have in this exclude list?
```
# rsync -aAXv --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found"} / */path/to/backup/folder*
```

Addendum: Mine is just a simple desktop install. 

Thank you.

---

### Post by 1clue on 2016-03-06
I use **cp -rax <srcdir> <dstdir>** for my backups. That basically tells copy to copy all permissions, and stay in a single filesystem.  Do it as root.

There is probably something like that in rsync, but I don't use rsync as it only solves a small portion of the requirements for a real backup.

I also generally don't backup / as a whole.  I backup /etc and other select directories which I modified, I figure if I fry a disk I'll want to install fresh anyway, and then copy my stuff over the top.

---

### Post by dFlyer on 2016-03-06
I don't think this is an answer to your question as you wanted to know what folders/files to backup in root. I only back up my /home folder. I feel backing up / is a waste of time.

---

### Post by mikodo on 2016-03-06
> **1clue said:**
> I use **cp -rax <srcdir> <dstdir>** for my backups. That basically tells copy to copy all permissions, and stay in a single filesystem.  Do it as root..

The -a = archive mode does include saving the permissions with rsync. I don't know what, "stay in a single filesystem" means? This of course is done with root too.> **dFlyer said:**
> I don't think this is an answer to your question as you wanted to know what folders/files to backup in root. I only back up my /home folder. I feel backing up / is a waste of time.I thought this would be a nice and quick way to be back with the system I have including copying my "symlinks as symlinks" to my data partition. And let the installer do the boot. Then, make and sync/populate a partition for my data from backups and let the symlink point to it, if I lost the disk.

Thank you, for the replies!

---

### Post by SeijiSensei on 2016-03-06
> **mikodo said:**
> The -a = archive mode does include saving the permissions with rsync. I don't know what, "stay in a single filesystem" means? This of course is done with root too.I thought this would be a nice and quick way to be back with the system I have including copying my "symlinks as symlinks" to my data partition. And let the installer do the boot. Then, make and sync/populate a partition for my data from backups and let the symlink point to it, if I lost the disk.

Thank you, for the replies!
Rsync also has the "-x" option for "one file system."  In both cases it means the program won't traverse other mounted filesystems.  For instance, I have /home on a separate partition, and I also have some directories on a file server mounted with NFS.  These will be ignored if the "-x" option is used.

---

### Post by mikodo on 2016-03-06
> **SeijiSensei said:**
> Rsync also has the "-x" option for "one file system."  In both cases it means the program won't traverse other mounted filesystems.  For instance, I have /home on a separate partition, and I also have some directories on a file server mounted with NFS.  These will be ignored if the "-x" option is used.

Thank you. I just found the -x and its' explanation. "this tells rsync to avoid crossing a  filesystem  boundary  when  recursing".

Especially, thank you for your explanation. I really wouldn't know what I pasted here meant, without it.

---

### Post by 1clue on 2016-03-06
-x also means it won't copy /dev, /sys, /proc or most of your other listed exclusions because these are special filesystems mounted on /.

---

### Post by mikodo on 2016-03-07
Thank you again, 1clue. I read your last response.

Actually, I don't see the benefit of using this over another thread I started, (I have had some time to do some reading and thinking since starting this thread).

So, I'll mark this thread solved so as, to stop wasting people's time.

 Not that I didn't learn from the posters' responses, I did.

I am going to follow up with doing what is in [this]("http://ubuntuforums.org/showthread.php?t=2313110") thread, instead.

Thank you, everyone.

---

