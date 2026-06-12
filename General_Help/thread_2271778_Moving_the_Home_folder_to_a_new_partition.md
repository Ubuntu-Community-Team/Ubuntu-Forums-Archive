---
title: "Moving the Home folder to a new partition"
date: 2015-04-01
forum: General Help
---

### Post by Lloydb39 on 2015-04-01
I'd like to separate the OS in 14.04 from my data. Can I not 1. Create a new partitition with Gparted. 2. Move Home to it. 3. Shrink the partition containing Ubuntu to a smaller size?
All the instructions I have seen make it much, much more complicated.

---

### Post by nerdtron on 2015-04-01
Why would you want to move your home folder to another partition? is it because you want to protect your data when you reinstall the OS?

If so, I won't encourage you to do it. Home partition also contains config files (for OS and the user) which can get conflicts when you reinstall the OS without formatting the home partition. So it is best to reformat the whole Ubuntu partition (including /home) when you do a fresh install of ubuntu.

Now, how do you protect your data? Create a separate partition for it. But don't mount it as /home. You can mount your own data partition as for example /media/user/data. This way, next time you re-install, just format the whole Ubuntu drive to get a fresh OS. Then after install, just mount your data partition again and all your data will be there.

Also a note on what you want to do, you can't resize the Ubuntu partition if is mounted. Meaning, you'll probably need to boot into Live mode, then shrink the partition you want. 
For moving the /home, to that partition, I can't help.

---

### Post by Impavidus on 2015-04-01
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

> 

[LIST=1]
[*]Setup your new partition 
[*]Backup and edit your fstab to mount the new partition as /media/home (just for the time being) and reboot. 
[*]Use rsync to migrate all data from /home into /media/home. 
[*]Edit fstab again so the new partition mounts as /home instead of /media/home but not reboot just yet. 
[*]Move /home to /old_home and reboot 
[*]Delete /old_home. 
[/LIST]

Moving the /home directory involves several steps. You have to move the data to the new partitions and instruct the system to mount that partitions at the location of the original home directory. That doesn't sound too hard to me.

---

### Post by oldfred on 2015-04-01
Because I have multiple installs, I use the shared data partition. I do not want each install to share /home and have the possibility of conflicts. But for a newer user the separate /home is easier to set up & configure.

 I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

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

### Post by ajgreeny on 2015-04-01
Whilst what nerdtron says is true in theory, I have been running a separate /home partition in my various Ubuntu, Xubuntu and Lubuntu OSs on different computers for many years without so much as a tiny glitch as a result of different versions of the applications.

I also agree with oldfred that it is much simpler to make a separate /home partition at installation time than to have a separate data partition which has then  to be mounted at boot with an edit of /etc/fstab; maybe easy enough if you know what you're doing but also easy to get wrong and then find that you can not get to your data.

The ideal setup, in my opinion, though so far I have not yet done it this way, is to have a separate small /home partition like oldfred's, another separate data partition, and then make soft links from the folders in /home to folders in the data partition.  That way all the data will still appear to be in /home but will actually be sitting in the data partition.

---

### Post by Keith_Helms on 2015-04-01
I leave my home on the / filesystem, but all my directories under it - download, bin, documents, etc. - are softlinks to a shared partition.   When I install a new OS, I run a script to get rid of the directories that the installer created and create softlinks to my shared partition.  I don't usually worry about copying all the .config type files from an old home to the new one.  Generally the configuration options have changed somewhat between releases anyway.

---

