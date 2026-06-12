---
title: "Resize root(/) and home(/home) partitions"
date: 2016-01-03
forum: General Help
---

### Post by atharvalele on 2016-01-03
While installing 15.10, I accidentally reversed the space I wanted to allocate for / and /home
I wanted a 50GB /home and 20GB/ but now I have the reverse.

How can I reseize the partitions? Do I need to do it while in a LiveBoot environment? I've a bootable USB of 15.04 with me.

And both the partitions are side by side so I don't have to go through the trouble of moving data I guess.
I've attached a screenshot from GParted. 

My setup -
Lenovo IdeaPad s510p
i3 4th Gen, 8GB RAM, 1TB HDD


Any help is appreciated.

---

### Post by ajgreeny on 2016-01-03
It is possible in theory to do that using a live USB or DVD Ubuntu system; you can not do it from the installed Ubuntu you appear to be using for the screenshot as the partitions will all be locked as shown in your screenshot.

You may find it is quicker to reinstall as you have a backup of all your files already, I hope;  moving files, which is what actually happens, could take hours to do the filesystem checks and then the moving of all the files on both partitions that gparted will do, but if you want to try it then you can do so, but **MAKE SURE YOU HAVE BACKUPS FIRST, INCLUDING WINDOWS**; hopefully nothing will go wrong but backups are always advised for any partition editing.

**WARNING**
Do not do this under battery power; make sure you are powered by the mains supply as if the partition work is interrupted you will probably lose everything on the disk, including possibly the Windows install.

---

### Post by atharvalele on 2016-01-03
Oh, thanks for the info.

So I should just fire up the 15.10 USB and reinstall and select the partitions? 
I'll try it later. Thank you once again.

---

### Post by Bucky Ball on 2016-01-03
Just a note, slightly off-topic. What are you going to use /home for? You seem to already have your personal data stored on various NTFS partitions. Why not just a 20Gb / and a 2Gb /swap and symlink to the data folders on the data partitions you already have. Putting data in a EXT* /home partition locks it away from Windows. NTFS partitions can be read and written to by both Win and Ubuntu.

We can show you how to create symlinks. That is easy. I have a number of installs and they are all symlinked to the same data in the same data partition. I delete the folders in the /home directory in / after install then create symlinks to the folders on the data partition instead. No redundancy, all installs access the same data, no confusion. :)

Just thought I'd throw that in. Back to your issue, though: a resize from a live session will work but may take some time, as suggested, or a clean install is naturally going to remedy the situation simply. Good luck.

---

### Post by atharvalele on 2016-01-03
> **Bucky Ball said:**
> Just a note, slightly off-topic. What are you going to use /home for? You seem to already have your personal data stored on various NTFS partitions. Why not just a 20Gb / and a 2Gb /swap and symlink to the data folders on the data partitions you already have. Putting data in a EXT* /home partition locks it away from Windows. NTFS partitions can be read and written to by both Win and Ubuntu.

We can show you how to create symlinks. That is easy. I have a number of installs and they are all symlinked to the same data in the same data partition. I delete the folders in the /home directory in / after install then create symlinks to the folders on the data partition instead. No redundancy, all installs access the same data, no confusion. :)

Just thought I'd throw that in. Back to your issue, though: a resize from a live session will work but may take some time, as suggested, or a clean install is naturally going to remedy the situation simply. Good luck.


I don't have much in /home except some kernel sources and toolchains for my phone.
And what you're suggesting is actually a good idea. It would be great if you could point me towards a tutorial. :D

So maybe I'll just shrink the root partition and add it to one of my NTFS ones.
Also a little off topic, any Ubuntu apps that I install, do they go into / or into /home?

---

### Post by oldfred on 2016-01-03
Bucky may have another suggestion on instructions, but these are my suggestions.

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

### Post by kevdog on 2016-01-03
@oldfred

I don't understand your need for the /data partition.  Why just not make a large /home partition?  And why would you reformat /home partition accidentally? Why is this more a risk than reformatting /data?

---

### Post by grahammechanical on 2016-01-03
Ubuntu needs a root ( / ) partition and a /home folder. The /home folder can be in the root partition or on its own partition. When we re-install we have to select mount points for the partitions and as we do that we are offered the option to format the partition at the same time. So, there is the possibility that when we select the /home partition and give it the mount point of /home we might also tick the box to authorise the format of the /home partition.

When we re-install we do not need to select the data partition and mount it. In fact there is no option to select & mount /data. So, there is absolutely no possibility of inadvertently ticking to format the data partition during a re-install.

Regards.

---

### Post by Bucky Ball on 2016-01-03
> **kevdog said:**
> @oldfred

I don't understand your need for the /data partition.

In my case, I have three (or is it four?) installs, all with a /home folder inside / and symlinks inside /home to the folders, e.g. /Documents, /Videos, etc., on the /data partition. That way they all use the same data, no redundancy, no confusion.

Backing up, I think, is also easier. All my personal data is on the /data partition. My OS and user settings are on the / partition. If I want to reinstall, I can kill the / partition and go again. Relink to the /data partition when installed and I'm done. ;)

---

