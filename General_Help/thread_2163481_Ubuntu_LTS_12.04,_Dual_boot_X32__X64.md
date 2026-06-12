---
title: "Ubuntu LTS 12.04, Dual boot X32 / X64"
date: 2013-07-18
forum: General Help
---

### Post by Lewis Balentine on 2013-07-18
I have installed Ubuntu LTS 12.04 on a Dell D630 Laptop with a 120 GB SSD and 3 GB of ram.
After I have the OS setup like I want it I went to install the target application: DraftSight.
It will only install on 32 bit Ubuntu.   :>(

Can I go back and install Ubuntu 12.04 (X32) and dual boot the system 
or 
do I need to start from scratch and downgrade the OS?

---

### Post by oldfred on 2013-07-18
You cannot downgrade. You can dual boot or else you have to totally reinstall.
Are you sure it does not work with 64 bit?

If dual booting, you may want to have a shared data partition and keep most data in that partition so both systems have all the same data. Each then has its own /home with user settings. I have multiple installs of Ubuntu (all 64 bit now) but have data in two 100GB data partitions, one NTFS from when still booting XP and the other Linux formatted where all new data goes. 

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

### Post by oldfred on 2013-07-18
You cannot downgrade. You can dual boot or else you have to totally reinstall.
Are you sure it does not work with 64 bit?

If dual booting, you may want to have a shared data partition and keep most data in that partition so both systems have all the same data. Each then has its own /home with user settings. I have multiple installs of Ubuntu (all 64 bit now) but have data in two 100GB data partitions, one NTFS from when still booting XP and the other Linux formatted where all new data goes. 

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

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

