---
title: "ntfs-config not my friend?"
date: 2007-11-21
forum: General Help
---

### Post by Wolkan on 2007-11-21
First off, I'd like to say I'm not very proficient with Linux at all.

Here's my problem:
I've got an external SATA drive with partitions of 15GB, 50GB and 400GB respectively.
So, I've just installed ntfs-config, enabled write for external drives, and tried making a folder in one of the 3 partitions. No dice. Create Folder is greyed out. I looked at the permissions, and it said "Read Only." Tried changing it to "Read and Write" but I only got
"Sorry, couldn't change the permissions of Media Partition"

Here are my fdisk results:
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       52218   419433052+   f  W95 Ext'd (LBA)
/dev/sdb2           52219       58430    49897890    7  HPFS/NTFS
/dev/sdb3   *       58431       60388    15727603+   7  HPFS/NTFS
/dev/sdb5               2       52218   419433021    7  HPFS/NTFS

It also says that I'm not the owner of either of the partitions.

So, how would I go around to fixing this? :(

---

### Post by YoG%*@ on 2007-11-21
hi,

which version of ubuntu are you using? (writing to an ntfs partition worked out of the box for me in gutsy).

you might need to install the ntfs-3g package too to enable read/write for ntfs partitions.

hth,
mux

---

### Post by Wolkan on 2007-11-21
I'm currently using Feisty.

Also, I have got the ntfs-3g package installed already. Sorry for not mentioning it.

---

### Post by YoG%*@ on 2007-11-21
can you check ownership and permissions of the files? (ls -l from a terminal). you may need to be root to write to the partition.

---

### Post by Wolkan on 2007-11-21
When using ls -l it doesn't show my external drive, just the local filesystem.
EDIT: I have managed to change /dev/sdb1 (and the rest)'s permissions using chown. I can indeed read and write according to that, but still nothing when accessing it directly.

Would I need to do it with /media as well? I tried doing so, but my partition names have a space in them. How would I enter it? =/

---

### Post by YoG%*@ on 2007-11-21
> **Wolkan said:**
> When using ls -l it doesn't show my external drive, just the local filesystem.


oh, i'm sorry, i was not precise enough: 

please change to the directory where your drive is mounted (usually /media/drivename or something like that) and issue the command there.

---

### Post by YoG%*@ on 2007-11-21
> **Wolkan said:**
> When using ls -l it doesn't show my external drive, just the local filesystem.
EDIT: I have managed to change /dev/sdb1 (and the rest)'s permissions using chown. I can indeed read and write according to that, but still nothing when accessing it directly.

Would I need to do it with /media as well? I tried doing so, but my partition names have a space in them. How would I enter it? =/


i would not change the ownership of /media since it is usually owned by root:root, but try enabling write permissions : 
```
sudo chmod o+w /media
```
(should let you write to /media as a normal user)

you can escape whitespaces by preceding them with a backslash. 
(e.g.: foo\ bar). try tab completion, it usually fills that in for you!

---

### Post by dabl on 2007-11-21
Add your user to the fuse group (or add the fuse group to your user) in User Management.  :)

---

### Post by Wolkan on 2007-11-21
Okay, I just noticed that I got the partition listed 2 (or 3) times.

Downloads Partition (empty folder)
Downoads Partition_ (can't be accessed)
Downloads Partition__ (all files are stored here)

Media Partition (empty folder)
Media Partition_ (all files are stored here)

Now, I can write to Downloads Partition and Media Partition, but still not to the ones with an underscore.

EDIT: dabl, did that. Still no change with the above problem. ^
EDIT2: [http://img265.imageshack.us/img265/7154/screenshotdownloadspartmb7.png](http://img265.imageshack.us/img265/7154/screenshotdownloadspartmb7.png)

---

### Post by Wolkan on 2007-11-21
Perhaps a small bump? :(

---

