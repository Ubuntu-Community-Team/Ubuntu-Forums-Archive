---
title: "Using another Ubuntu's HD space"
date: 2013-08-23
forum: General Help
---

### Post by jgcsd on 2013-08-23
I have multiple OSes. One that I'm using has virtually no HD space left.

How can I temporarily use the space of a Ubuntu installation that's got lots of free space, from within a different Ubuntu installation?

Edit: Well creating a folder on the other partition with "sudo", then using chmod to change the user seems to work for now. So I'll do that. Fingers crossed that's not going to cause anything horrible to happen.

---

### Post by r_avital on 2013-08-23
I could be wrong, but I expect that all this will do, when you boot up into the other OS on the other partition, is prevent you from using that particular folder.

---

### Post by Dennis N on 2013-08-23
If the other *buntus has the same user name you have no problem, for sure. Just mount the other OS partition in the file manager, or from desktop icon if xfce, (no password required in either case) and you have full access. For example, my first partition was made quite large, so I use is for all multimedia and can access it from any other OS on the disk just as if it were on the running OS.

---

### Post by oldfred on 2013-08-23
I have many installs as I have not deleted all my old test or working installs as I still had room. Every install is in about a 25GB / (root) partition but I share two data partitions with every install. One is NTFS from when I still dual booted XP and the other is Linux formatted but I have to set ownership & permissions to make it work.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

