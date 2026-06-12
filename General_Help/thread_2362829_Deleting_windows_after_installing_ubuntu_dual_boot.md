---
title: "Deleting windows after installing ubuntu dual boot"
date: 2017-06-02
forum: General Help
---

### Post by heron1337 on 2017-06-02
yo i have a question if i delete windows after i installed ubuntu dualboot, will the space from the windows (around 900gb) automaticly signed to ubuntu ?

---

### Post by RobGoss on 2017-06-02
Simple answer to your question is no, it will not place the unwanted space on your ubuntu partition automatically you will have to make that Windows **partition** unallocated and then use gparted to merge the two partitions

**Note**: It might also be best to use the Live disk when using gparted to merge the two partitions

Another way is to just do a clean installation and use the entire disk and save time

---

### Post by oldfred on 2017-06-02
You can also make a new ext4 partition in that space and use it for data. Or even move /home into that space if a lot larger.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[URL="https://help.ubuntu.com/community/Partitioning/Home/Moving"]https://help.ubuntu.com/community/Partitioning/Home/Moving

[/URL]I use separate data partition at /mnt/data as I have several Ubuntu installs all about 25GB. If I want to test different versions or experiment with other configurations/gui I do a clean install, so my main working install is not modified. But I often want my standard data in each install.

      
 The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

