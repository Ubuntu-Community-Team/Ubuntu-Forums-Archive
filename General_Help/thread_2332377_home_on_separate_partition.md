---
title: "/home on separate partition"
date: 2016-07-31
forum: General Help
---

### Post by boz_1812 on 2016-07-31
Ubuntu 14.04 LTS

I've been following some comments from users who have partitioned their hdd, having / and /home on separate partitions.  
The aim is to make reinstall or upgrade easier, without disturbing user settings in the /home directories.  I'm interested in this because I prefer to clean install rather than upgrade, something I learned from years of Windows use; cleaning out the mass of accumulated junk.
My question is, what are the pros and cons of this approach?  Does retaining existing configuration files work if new packages have to be installed?

I've located a well defined process at,
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Is it worth doing?

Thanks.

---

### Post by sudodus on 2016-07-31
It works better than I had expected before I tried, to keep /home when re-installing an Ubuntu flavour (I usually run Lubuntu). But I guess there can be conflicts in some cases.

You should notice that there are global settings and tweaks, that are stored elsewhere, for example in /etc, so every tweak and setting may not survive, when you keep /home.

If you store your personal data files in your home directory, those will not be house-cleaned, if you keep /home, and you need to get rid of that kind of junk manually :-P

---

### Post by grahammechanical on 2016-07-31
Upgraded applications (such as Firefox & Libreoffice) lock on to the existing user configuration files in the /home partition. The applications are looking for certain files/folders in the /home folder and the OS knows the /home folder is on the /home mounted partition.

The only time this will break is if the application developers decide to change the folder layout for configuration files. But the installation of the application might be smart enough anyway to avoid this happening.

Having /home on a separate partition certainly reduces the risk of loosing data and configuration files. But there is still a risk that we might tick the box "Format the partition" when selecting the partition as /home.

Having data on a separate partition altogether and leaving /home as a folder under / eliminates that risk. But the user configuration files will be over-written.

Regards

---

### Post by oldfred on 2016-07-31
Another alternative is separate /mnt/data partition and linking all your data folders back into /home.
My /home folder in / is this size, so easily backed up.
595M    /home

But I have all data and even some of the larger hidden folders like the Firefox & Thunderbird profiles in my data partition. Primarily because I install several copies of Ubuntu and want to have same data in all installs.
       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

---

### Post by malspa on 2016-07-31
I still do this, separate / and /home partitions, for no particularly good reason because I always prefer a fresh installation rather than an upgrade. Well, there was one time several years back when a hard drive went bad on me... I couldn't do anything with the / partition but I was able to save all of my files from /home. That was really the only time having those two partitions helped me.

---

### Post by pfeiffep on 2016-07-31
I've used /home being shared with different releases [all Ubuntu] and found it provided some minor difficulties. I have all data on a separate NAS shared with 3 devices and 3 OSes.
Since I had minor difficulties and I have all data on a NAS I have just copied the /home areas I wanted to reuse ie .thunderbird, .mozilla, .lastpass etc. which provides fine grained control

---

### Post by Keith_Helms on 2016-07-31
I find it easier to keep a small /home on the / mount and link data directories within /home to another mount point.  It's not too hard to find the .config files for apps (like .mozilla for firefox) and copy them to a new install.  That way if you swap back and forth between OS versions, you don't have to worry about compatibility between old and new versions of packages.  Outside of configuration, files are then shared between multiple installs.  If you have a config directory that also contains data like Thunderbird, you can always set that one up as a link too.

---

### Post by boz_1812 on 2016-08-02
Really good information.  Thanks a lot passing on your experience.  I'll now work on a plan incorporating your suggestions.

Cheers,
Bob

---

