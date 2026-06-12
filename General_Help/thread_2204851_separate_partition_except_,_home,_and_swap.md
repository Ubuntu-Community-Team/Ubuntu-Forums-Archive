---
title: "separate partition except /, /home, and swap"
date: 2014-02-10
forum: General Help
---

### Post by chillering on 2014-02-10
I heard 3 partitions (SWAP, /Home, and /) are enough for single user computer. However, I keep on moving to different distros and want to keep backup of my documents and movies etc in a separate safe partition which I can copy stuffs from /Home to that partition anytime. 

So, what file system, mounting point, and type of partition I can use to keep such backups? Your help will be appreciated.

---

### Post by oldfred on 2014-02-10
Having backup on the same hard drive is not the best backup, as hard drive failure is often an issue.
If just an issue with corruption on a partition then the backup may help.

For data any format will work, but if you use NTFS then you lose ownership & permissions. With data you can restore those easily. Otherwise use ext4 for Linux, but you have to set ownership & permissions so you can use it correctly.

I keep /home inside my / (root) and have a separate data partition on another drive for all my data. And I have multiple installs all using the same data.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by chillering on 2014-02-11
> **oldfred said:**
> Having backup on the same hard drive is not the best backup, as hard drive failure is often an issue.
If just an issue with corruption on a partition then the backup may help.

For data any format will work, but if you use NTFS then you lose ownership & permissions. With data you can restore those easily. Otherwise use ext4 for Linux, but you have to set ownership & permissions so you can use it correctly.

I keep /home inside my / (root) and have a separate data partition on another drive for all my data. And I have multiple installs all using the same data.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

Thanks a lot. Very informative and somehow solve my problem

---

### Post by chillering on 2014-02-11
Suppose I'm shifting back to Windows someday and have tons of data in /Home partition. So I will have to create new partition EXT4, copy /Home data there, and then format?

---

### Post by oldfred on 2014-02-11
Windows will not read Linux formatted partitions. There are some drivers that can be loaded that should work to read the data if necessary, but generally better just to use NTFS if you want to share with Windows.

I still have two shared data partitions, one NTFS from when I still used XP and one Linux formatted. I just have not reorganized and moved data from NTFS to my Linux partition.

---

### Post by chillering on 2014-02-11
> **oldfred said:**
> Windows will not read Linux formatted partitions. There are some drivers that can be loaded that should work to read the data if necessary, but generally better just to use NTFS if you want to share with Windows.

I still have two shared data partitions, one NTFS from when I still used XP and one Linux formatted. I just have not reorganized and moved data from NTFS to my Linux partition.

Ok, thanks I got it.

---

