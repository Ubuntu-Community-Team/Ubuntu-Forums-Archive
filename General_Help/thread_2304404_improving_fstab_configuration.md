---
title: "improving fstab configuration"
date: 2015-11-26
forum: General Help
---

### Post by zakrapovic on 2015-11-26
Hello everyone,

Here is the relevant parts of my fstab : 

# My home
```
UUID=28c1edcf-c306-4af2-8103-52307509349e /home           ext4    defaults        0       2
```

# A data HDD
```
UUID=982A1FCC2A1FA5F2 /mnt/data ntfs defaults,dmask=027,fmask=037,uid=1000,gid=1000 0 0
```

#The way I mount folder from my data HDD into my home, as it becomes the personal folder recognized by the system
```
/mnt/data/Documents /home/zod/Documents none bind 0 0
/mnt/data/Music /home/zod/Music none bind 0 0
/mnt/data/Pictures /home/zod/Pictures none bind 0 0
/mnt/data/Videos /home/zod/Videos none bind 0 0
/mnt/data/Desktop /home/zod/Desktop none bind 0 0
/mnt/data/Downloads /home/zod/Downloads none bind 0 0
```

The problem is I do not like having to specify each folder that it should mount in my fstab, the equivalent should be something like :
```
/mnt/data/* /home/zod/ none bind 0 0 (it does not works)
```
As I actually mount everything from my /mnt/data into my home

The second issue is it sucks making a mount point for each of this folder as the system will copy files between them instead of just moving it

The best solution would be to just specify another path for my personal folder (dconf maybe?).

Thanks a lot for reading it!

---

### Post by ajgreeny on 2015-11-26
As the data partition is already mounted using fstab with the line ```
UUID=982A1FCC2A1FA5F2 /mnt/data ntfs defaults,dmask=027,fmask=037,uid=1000,gid=1000 0 0
``` I suggest you remove all the usual main data folders in your home and make symbolic links to the data folders in the data partiton to a link file of the same name in your home with command ```
ln -s /mnt/data/Documents Documents
``` and so on, one for each data folder.  

All your files will then appear to be in those normal named folders in your home even though they are actually still sitting in the data partition. You should not see any difficulties running the system that way and there is no need to copy any files across from the data partition to your home as they will all be there as far as you are aware.

---

### Post by oldfred on 2015-11-27
I also use links, but once I have with a new installed deleted the folders I know are empty, I just run a one line script that finds all the folders & links them into /home.

#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

But this user who knows more about mounting and configuring mounts than most, prefers bind. In other posts I believe the issue related to seeing mounts from other systems correctly on network. I do use NFS, but my links are directly to /mnt/data not to /home. 
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by zakrapovic on 2015-11-28
Hello,

Thank you for your advice
I am interested with your solution of doing links but just afraid to lose the "user folder integration" on nautilus doing it.
Will nautilus discover the symlinked folder and interpret it as user folder ?

---

### Post by Bucky Ball on 2015-11-28
The symlink will appear in whatever folder you create it in. I have all mine in the /home directory in / and they are linked to folders in my /Data partition. 

Nautilus doesn't 'discover' anything. You manually create the symlink where you want it. It will appear and act as any regular folder.

---

### Post by oldfred on 2015-11-28
Make sure you Docuements folder in your install is empty and backed up, and then delete it like ajgreeny shows you above. Then link to your folder in your data partition. You may have to remove the bind link first also, so you will have conflicts.

After you see it works then you will know.

---

### Post by zakrapovic on 2015-12-24
Thank you all :)
Finally did the symlinks

---

