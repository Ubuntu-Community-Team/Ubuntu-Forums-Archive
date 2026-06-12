---
title: "Cannot get permissions to my backed-up folders"
date: 2008-01-23
forum: General Help
---

### Post by 1002285 on 2008-01-23
[LIST]
[*]I used LinuxMint 3.0 LiveCD on the computer where I wanted to back up my documents (the installed system could not write on the necessary backup partition).
[*]After that I was able to get the read/write permissions for that partition, using the installed system. But I could not get the permissions to the folders created using the Live CD.
[*]Then I used sudo nautilus to change permissions from the Properties box, but I was only able to change the permissions for one, highest-level folder, and the sub-folders are still locked. There are very many subfolders.
[*]Then I used chmod -R +rw /media/partition-name/highest-level-folder, but got "Operation not permitted" answers for all folders.
[*]Then I reinstalled LinuxMint 4 - I was sure that I would get the permissions then. I did not, the situation is the same: the highest level folder, for which I changed permissions using sudo nautilus, is the only one I have access to, but the subfolders are still locked. [*]The chmod still gives the very same answers than before.
[*]When trying to use sudo nautilus to change permissions - nothing changes. One thing I can't understand there: For the highest level folder I already have myself set as the owner, and this owners folder permissions are "create and delete". But when I change the owner's file permissions from "---" to "read and write" - It does not get applied. The nex time I open the properties box, it's back to "---". Is that normal?
[/LIST]
What should I do to get access to all the folders I copied there with the LiveCD?

---

### Post by burbankmarc on 2008-01-23
```
sudo chmod -R o+rw
```

---

### Post by bodhi.zazen on 2008-01-23
what file system ? FAT and NTFS do not support permissions, so you need to set them at the time of mounting the partition.

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent][/list]

---

### Post by 1002285 on 2008-01-23
> **burbankmarc said:**
> ```
sudo chmod -R o+rw
```
Thank you, that worked (although I needed sudo, too, almost gave up :)).
It just feels so ridiculous now to think of how much I tried the wrong things.

---

