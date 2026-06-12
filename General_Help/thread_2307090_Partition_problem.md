---
title: "Partition problem"
date: 2015-12-21
forum: General Help
---

### Post by knoebber on 2015-12-21
Hi, I recently installed 15.10 and did a manual partition table which has been working fine for the last month, but today I got a disk space low message. 
It seems as though /home is somehow filling up my root directory, as I know that I haven't installed enough programs to fill it. I got some help on the irc today, and someone pointed out that my home and root directory are on logical partitions (sda5 and sda6) which could be a problem. Anyways is some terminal stuff:

partition sizes: [http://paste.ubuntu.com/14134515/](http://paste.ubuntu.com/14134515/)
home usage: [http://paste.ubuntu.com/14134563/](http://paste.ubuntu.com/14134563/)
disk usage [http://paste.ubuntu.com/14134569/](http://paste.ubuntu.com/14134569/)
disk usage in mb of root: [http://paste.ubuntu.com/14134627/](http://paste.ubuntu.com/14134627/)

Any help would be appreciated, thanks!

---

### Post by yancek on 2015-12-22
The problem is due to the fact that your / (root filesystem) partition is full:

> /dev/sda5        14G   13G     0 100% /

Your home partition is not filling up your / partition.  Any software you install will almost always be on the / partition.  The home partition will have some configuration files for the users and general data.  Being on a logical partition as opposed to a primary should not be part of the problem.  If you don't have anything on / partition you can delete, you should be able to increase the size of the / partition by first shrinking the home partition.  If you have the Ubuntu installation media, you have GParted on it and you can use that.  Probably the best first step is to use GParted to post an image here of the drive and partitions and get more specific instructions.  Before doing anything, definitely do a backup of any data as there is always a risk of losing data when changing partition. The link below is to the GParted Manual which you should take a look at before beginning.

[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by ian-weisser on 2015-12-22
Are you sure your sda6 /home is mounting properly?

Look for files on sda5's /home, which should be an empty dir used as a mount point.
If there are files in there, then sda6 failed to mount at some point. 12G is a lot for one failed mount. Maybe this has been going on a while.

---

### Post by knoebber on 2015-12-22
Okay you are  right. I poked around more in / and saw that I have a kern.log file that is 4gb, and a syslog.log1 file that is just as big. I deleted the syslog.log1 file, but why are they so big? Can I make the kernel log smaller safely?

---

### Post by ian-weisser on 2015-12-22
They are so big because your system is trying to tell you about an important problem.
I would explore those huge logs, discover the problem, and simply fix it

---

