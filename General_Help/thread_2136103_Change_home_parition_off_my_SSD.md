---
title: "Change home parition off my SSD"
date: 2013-04-16
forum: General Help
---

### Post by kr651129 on 2013-04-16
I've got Ubuntu 12.10 installed on a new SSD.  I'd like to move my home parition to my 1TB traditional drive.  Is there an easy way to do this?

---

### Post by leclerc65 on 2013-04-16
Follow this guide

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by oldfred on 2013-04-16
+ on leclerc65 link to moving /home.
That is probably the best way for most users.

But I moved data and left /home inside / (root). I only left the hidden files & folders and even some of those with lots of data like Firefox & Thunderbird profiles also were moved. I do that partially as I have multiple installs and then easily share data but not user settings and I can do a new install but with defaults to start with and only copy over some configurations that I may want.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by Bucky Ball on 2013-04-16
*Thread moved to **General Help**.*

---

