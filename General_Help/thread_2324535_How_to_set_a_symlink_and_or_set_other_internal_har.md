---
title: "How to set a symlink and or set other internal hard drives available for all users?"
date: 2016-05-14
forum: General Help
---

### Post by unknown14 on 2016-05-14
Hi,

I have a recent install of unbuntu 16.04 and it was installed to a single m2 format ssd, whilst a bunch of other disks salvaged from the old PC have been installed internally, some with NTFS partitions etc.

I want some on the folders to be available on a symlink I install for each user for Pics, Music etc. Currently each drive seems to appear on media/<user-name>/<folders>, but they are not removable drives, so should not sit under /media/ I believe.

What is the best place to force a mount for these other drives, and what is the best tool to do that with. 

I have been a long time windows user, so comfortable with the windows way of doing these things and currently on a steep learning curve getting them done the way of the penguin.

---

### Post by yancek on 2016-05-14
The standard place for a mount point is in the 'mnt' directory.  Create the directories in the /mnt directory as the mount point (Pictures, Music, etc.) and then create an entry in the /etc/fstab text file edited as root (use sudo).  There are countless tutorials and examples online for proper entries in the fstab file for both Linux and windows partitions/filesystems and what you use depends upon what access you want users to have.

---

### Post by unknown14 on 2016-05-19
I tried that and ended up making some mistakes, the system would not go  to gui, so I had to comment out the lines in /etc/fstab for now, till I  understand the entries better.

---

### Post by oldfred on 2016-05-19
You first have to get mounts correct in fstab.
If you want to post your UUID, fstab and desired mount points we can help.

Mounting templates here:
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. 


Linking Details here:
 The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

