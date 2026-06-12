---
title: "ext4 and btrfs partitions"
date: 2018-08-02
forum: General Help
---

### Post by shaolin30 on 2018-08-02
Hi, I have 2 kinds of partitions which is ext4 and btrfs. The default drive that I am using now is the btrfs file system which I symlink'ed to ext4 to act as my backup drive, however I noticed that my ext4 got 100% full and I cannot download nor I cannot cd to any directory because of this error ```
bash: cannot create temp file for here-document: No space left on device
```. My problem is that I forgot where did I put the symlink bash command and I don't know where to start to fix this. Any help will be much appreciated. Thanks guys.

---

### Post by DuckHook on 2018-08-02
Welcome to the forums, shaolin30.

I am a bit confused. By symlinking, you are not using it as a "backup" drive—you are, in fact, using it as your main drive (at least, for those symlinked files).

[LIST]
[*]The usual method to free up space in a situation like yours is to boot from a USB stick/drive and offload enough stuff from the filled up drive to allow you to maneuver.
[*]You can see what your file structure looks like by doing a simple:```
ls -la
```Symlinked directories/files will have the letter "l" (that's el) in the first column of your properties block. Example:```
lrwxrwxrwx   1 duckhook duckhook     27 Jan 17  2018  Templates -> /mnt/data/storage/Templates
```
[/LIST]

---

### Post by shaolin30 on 2018-08-02
Hi DuckHook,

I just fixed it and was able to locate my symlink script with the help of my friend. Actually doing ```
cd /
``` to go the root directory and typing ```
du -hs <directory>
``` to each directory will identify which directory has taken up more space.
But that's not the real problem in my case because inside my > backupscript bash file is

> 
#!/bin/bash

rsync -a /home/ubuntu/ /backup/ubuntu/


using the above script filled up my sda1 partition even though I still have space in sda2. What happened is that whatever file I'm going to modify in sda2 will keep the reference of that data in sda1 and even though i.e. the file from sda2 is deleted, it will remain in sda1. So this is basically what is happening using that script.

So now what my friend and I did was updated the script to:

> 
#!/bin/bash

rsync -a --info=progress2 --delete /home/ubuntu/ /backup/ubuntu/


Then I run the backupscript (./backupscript) to take effect and delete those files that are not in sda2(btrfs) partition.

This way whatever changes I will make in sda2 will be the same as sda1.

---

### Post by HermanAB on 2018-08-03
With links (sym or hard) there is only ONE file and lots of links.  I prefer hard links - they work better for me.  I also use a utility called 'hardlink' to eliminate duplicate files on my machines.

If you want to make a backup, use rsync and run it from cron.daily or cron.weekly.

---

