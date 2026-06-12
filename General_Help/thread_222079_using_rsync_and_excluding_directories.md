---
title: "using rsync and excluding directories"
date: 2006-07-24
forum: General Help
---

### Post by jordilin on 2006-07-24
I use rsync to backup my home directory, but I want to exclude some directories such as .beagle. 
I do
```
rsync --av --exclude-from=/home/exclude-list --stats /home/username /media/externalharddrive
```
where in exclude-list I have:
> /home/username/.beagle/

but when executing the command it does not exclude the .beagle directory. What I'm doing wrong?

---

### Post by cssutto on 2006-07-24
This is what I use to back up my entire laptop drive to an external drive.

Note that all you need is --exclude=(the directory you want to exclude).

In my case, it is the various drives and partitions that already have backups on them.

sudo rsync --verbose  --progress --stats --compress --recursive --times --perms --links  --exclude=/media/LOCAL\ DISK-1/ --exclude=/media/LOCAL\ DISK/ --exclude=/media/H_\ \ \ \ ~1/ --delete //   /media/LOCAL\ DISK-1/linuxbackupcomplete

CSSJR

---

### Post by cssutto on 2006-07-24
I have no experiance with using list files.

CSSJR

---

### Post by jordilin on 2006-07-24
I have put the line
```
rsync --av --exclude=username/.beagle --stats /home/username /media/externalharddrive
```
in exclude I don't have to put the whole path /home/username/.beagle because rsync transfers the path /username/*  . It seems, there's a difference between writing /home/username/ and /home/username. I will investigate.

---

### Post by cssutto on 2006-07-24
Don't hold me to it because I am relatively new to linux and as soon as I get anything working, I go on to the next problem because it is one huge job to try to rebuild in a few weeks in linux what I have on W2K, a lot of which goes back to the days when Bill Gates was still in his garage.

Anyhow, I read somewhere that if you do /home you could end up with a subdirectory named home in the /home directory.

If you do /home/, you put the information in the original directory.

That may or may not be correct, but that is what I think I remember.

Note that I use --delete to purge the destination of any information that is not still in the source.  Remember that if you use --delete and tell rsync to copy a file in your home directory, not the entire directory, you will end up with only that file in the destination /home/.  All the old data in destination /home/ will be deleted.

I don't know what the syntax was, but one person I read about deleted everything in his source /home/ with the improper use of delete, so although it is an important feature, be careful.

CSSJR

---

### Post by jordilin on 2006-07-24
> **jordilin said:**
> rsync --av --exclude=username/.beagle --stats /home/username /media/externalharddrive
This command already works. But now I have openned another thread about rsync and synchronization. It does not synchronize if I switch on/off the external hard drive
see
[http://www.ubuntuforums.org/showthread.php?t=222165](http://www.ubuntuforums.org/showthread.php?t=222165)

---

