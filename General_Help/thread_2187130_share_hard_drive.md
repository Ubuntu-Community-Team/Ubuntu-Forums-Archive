---
title: "share hard drive"
date: 2013-11-10
forum: General Help
---

### Post by linuxuser427 on 2013-11-10
is there a way i can have a central shared location on a dual or tripple boot system without having to mount the volumes or log or and switch system.


trying to access documnets music pictures etc. no matter what OS i was using when i save it and have access from all three

---

### Post by bab1 on 2013-11-11
> **linuxuser427 said:**
> is there a way i can have a central shared location on a dual or tripple boot system without having to mount the volumes or log or and switch system.


trying to access documnets music pictures etc. no matter what OS i was using when i save it and have access from all three
The short answer is no.

You would have to create a partition for the common data and mount that partition when each OS is booted up.  If you are sharing data with a Windows distro you would have to format the common partition as NTFS.  The mount into Ubuntu would have to explicitly name the user (and group) for that user to have the correct ownership of the partition.

Maybe the user @oldfred will chime in on this subject.

---

### Post by oldfred on 2013-11-11
I started sharing a Windows formatted partition back in 2006, back then it was FAT, but now is NTFS. I also moved Firefox and Thunderbird profiles to that NTFS partition and still have them there. I will move to my Linux formatted data partition, but have not changed yet. So I have two data partitions, one NTFS and one Linux. I modify my fstab to auto mount both and link folders into my /home so it is like a default install. These two data partitions are mounted in every one of my many installs. I now have a script to automate it since I found I was repeating the same commands over & over with every new install.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

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

### Post by bab1 on 2013-11-11
Thanks for helping out.  :-)

---

### Post by linuxuser427 on 2013-11-11
thanks ill give that a try

---

