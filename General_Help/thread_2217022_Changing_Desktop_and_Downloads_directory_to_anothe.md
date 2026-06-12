---
title: "Changing Desktop and Downloads directory to another partition or HDD"
date: 2014-04-15
forum: General Help
---

### Post by George_Papadeas on 2014-04-15
So i have a small ssd in which i have two partitions. One for windows and one for Ubuntu 12.04. I use only Ubuntu actually so i want to free some space from Ubuntu partition and put it to the other partition or maybe another HDD.

Is this possible? If yes how? Will i have any problems? 

Thanks..

---

### Post by Impavidus on 2014-04-15
Welcome.

The most common solution to your problem is moving the entire /home directory to a separate partition on a HDD. Read some documentation and ask questions here.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by SeijiSensei on 2014-04-15
Another solution is to move those directories to the other device and set up symbolic links in your home directory that point to the new locations.  My /home/user/Documents directory is a symlink to a directory on my server.

---

### Post by oldfred on 2014-04-15
I have two data partitions on hard drive and two Ubuntu installs on my SSD. Since I also install other installs on hard drive to test I mount data partitions in all my installs. One data partition still exists as NTFS from when still booting XP so I could share data with XP. All new data is in a Linux formatted partition.

 The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

