---
title: "partition for data"
date: 2013-05-08
forum: General Help
---

### Post by thorbs on 2013-05-08
At the moment I am dual booting ubuntu and xubuntu. However i would like to just have one partition with Ubuntu, and then one partition where I have stuff, likke music etc.

I need to format it somehow. Anybody who has a pointer what to do, and how to do it?


t.

---

### Post by ibjsb4 on 2013-05-08
You need a data partition.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9)

---

### Post by oldfred on 2013-05-08
I have several Ubuntu installs and shared data.

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
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by fantab on 2013-05-08
Just root "/" 25-30GB for Linux OS and a separate DATA partitions is the way to go, IMO. 
suggested:
25-30GB "/" Ubuntu
25-30GB "/" Xubuntu
2-4GB SWAP
DATA Partition ext4 (no mountpoint)

[QUOTE=oldfred]Works best if all installed systems are Debian based, see UID issues below[/QUOTE]

At one time I was sharing my DATA Partition between various Ubuntus, Fedora and Arch. NO ISSUES.
Earlier it was a PITA sharing that partition with Fedora, but since they moved to default UID=1000, no issues.

---

### Post by Buntu Bunny on 2013-05-08
> **oldfred said:**
> I have several Ubuntu installs and shared data.  I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders....

Oldfred, I've been wondering about this very thing. Your information is extremely useful, thanks.

---

### Post by thorbs on 2013-05-08
Thanks lot to read and experiment with.

---

