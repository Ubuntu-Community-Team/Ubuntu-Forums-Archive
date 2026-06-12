---
title: "Doing a new install 16.04"
date: 2017-05-14
forum: General Help
---

### Post by Robbyx on 2017-05-14
Most people say it is best to do a fresh root install (assuming that the home directory is in another partition),. A possible next step is to reinstall via a stript of installed packages from synaptic. I run a fairly basic system, which includes a small network of devices. 

It is quick and easy to do the fresh install but what should I manually restore before reinstalling the missing program files: 

I usually restore the fstab file and change the uuid's for reformated partitions. How should I save and restore the special repositories I use?  What else would be sensible to save and restore?

---

### Post by TheFu on 2017-05-14
Use this as a chance to test your backup and restore procedures.
Lots of people have written *what they backup* and *why* here. I know I have, probably 10 times in the last 5 yrs.

At a min, I backup:
* /etc/  lots of stuff in there you _could_ need.  It is tiny, best to have it all.
* ~/  or where ever all the HOME directories are for your users.
* dpkg --get-selections
* anything /var/ that I put there specifically - like websites, DBs, whatever.
* anything in /usr/local/  that is where I place manually installed, not packages, software.
* anything in /opt/  that is where commercial software often likes to be install.

Test this a few times to make certain that what you have backed up is all that you need.  Took me about 5 attempts before I got everything.  Best to test using a new HDD.

---

### Post by Robbyx on 2017-05-14
Thank you for your reply. I am unclear what to do with  dpkg --get-selections. What i usually do is reformat the root because home is not reformated and left as is. Before the installation I thought I could get as list of installed programs wihich can then be run on the ew install once all the reps are in place . Am I ring to assume that the dpkg command is the same as that produced by synaptic?

---

### Post by oldfred on 2017-05-14
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade
#IF you get this error:
dpkg: warning: package not in database
sudo apt-get install dselect
sudo dselect 
   -> Update
   -> Install 


 and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings' 

But be careful with ppa repositories. Often you may be installing a newer Ubuntu and the ppa does not yet have available that version. Or you install the old ppa and version  issues are created. Use backup of ppas, as list of ones  you may want to reinstall, but do not auto reinstall.  Some may not even be needed.

---

### Post by TheFu on 2017-05-15
Cannot answer your question. I haven't use synaptic or any GUI to manage packages in a very long time. I think Oldfred's answer correct.  

The problem with using a GUI is that is hard to automate, run nightly, while I'm asleep.  

There are other little things that my backup scripts capture.  Partition layouts, LVM configurations, RAID configurations, etc.  Sometimes this extra data isn't needed. Just depends on the system purpose and if I'm trying to fix a failure or just wipe and restart from base.  It is ok to have 5 extra text files - they don't take much space.  OTOH, if I do need this data, it is really handy to have it.   A list of all the hardware in the system that includes the drivers being used is handy too.

Some extra config/settings that I capture before every backup starts:
```
# ls
blkid.txt   crontab.root  dpkg.list  lvdisplay.txt  vgdisplay.txt
crontab.thefu  df.txt        lshw.list  pvdisplay.txt
```

---

### Post by dragonfly41 on 2017-05-15
I'm in the process of migrating from 32 bits Ubuntu 14.04 to 64 bits Ubuntu 16.04.
I'm learning as I go.  Since this will involve deploying fresh installs and I'm also targeting some remote servers (google cloud, heroku and others) I decided to explore using migration/backup automation scripts.

I have decided to focus on using Fabric scripts combined with yapsy-plugin to create a class framework of automation libraries.

I'm building on the ideas I read here ..

[http://www.saltycrane.com/blog/2010/09/class-based-fabric-scripts-metaprogramming-hack/](http://www.saltycrane.com/blog/2010/09/class-based-fabric-scripts-metaprogramming-hack/)

That might be too complex an approach for the OP.

However while researching migration tools I saw the package Aptik Migration Utility found under System Tools.
That might be a tool worth exploring (although it is yet another gui).

---

### Post by oldfred on 2017-05-15
I also do like TheFu in including system configuration data in my backup script.

I use bootinfoscript which covers most of the drive and booting info.
       Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

I do not have many configuration files I edit in /etc, and make copies into /home whenever I edit them, so my backup of /home includes those files also.

---

### Post by TheFu on 2017-05-15
I like it oldfred!  Like it a bunch!

But don't forget the capture cron stuff from the 5 different places it might be configured.

And I'm thinking about adding the **lsblk** output - nice, clear, overview of how disks, partitions, LVM, encryption are setup.  These are relatively tiny files, so why not?

---

