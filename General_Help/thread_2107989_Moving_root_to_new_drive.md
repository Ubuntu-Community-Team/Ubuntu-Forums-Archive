---
title: "Moving root to new drive"
date: 2013-01-23
forum: General Help
---

### Post by jdallara on 2013-01-23
Scenario: Internal drive on my laptop died.  Have been running on external USB drive for several months.  Finally replaced internal drive, now I want to move everything from the external drive to the new drive and use the internal drive only.

I'm running Ubuntu 12.04 latest version (36?) .  The internal drive is 60GB, partitioned as root, home, and tmp.  The external drive is 500GB and partitioned as root and home.  The internal drive is bootable and I have installed Ubuntu to it from my live CD and the laptop will run fine.  I want to preserve the updates and work that I've been doing over the last several months otherwise I'd just start over with the ISO that I have (12.04 version 29).  Tried recovering from a backup but that only hoses the OS when it gets to /lib.

I remember doing this same thing years ago on HP-UX and I know it was non-trivial to move the root drive but I can't remember the procedure to do it.  Any ideas?

Thanks in advance,

Jon

---

### Post by oldfred on 2013-01-23
If you have already installed you just need to copy /home over. Does /home fit? The /home folder or partition has all the user settings & data.

It is not quite this but you should backup current /home which may have a few new settings and copy old /home into new /home that is on internal drive.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

    
Only if you made some system wide changes then you may have something in /etc to copy. And you can export a list of installed apps & reinstall. If you have not house cleaned out the .debs you can just copy them over.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

    
       Location of downloaded debs
/var/cache/apt/archives/

    
       More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

### Post by jdallara on 2013-01-23
Thanks for the suggestions.  It's been 12+ years since I was a UX sys admin and I'm a little rusty.  If I only need /home then that is easy.  I was using 'cp -a -v . /home' to push the files, but I'll look at the rsync thread.  I was used to having apps all over the place, but Ubuntu looks much more regimented than I remember.  I'd still like to know if there is a way to do a root drive move, i.e. move all files from the root drive to a new drive, remove the old drive, install the new drive, reboot and have everything as it was.  I'll check out the other info as well.

Thank you,

Jon

---

### Post by orb9220 on 2013-01-23
Sounds like [Redo Backup]("http://redobackup.org/") might do it easy peasy for you.
As can mirror the partitions then restore them to new drive.

I have separate / and /home but also Win7,Winxp so can mirror all or selected and apply to a new drive. Like Redo as easy peasy and can't mess up trying to sync or move files across devices.

I install new distros' so overwrite installed flavor with new flavor and back that up also. That way can on the fly change linux flavor or restore a bork install of Windows or Linux in about 20 mins.
.

---

### Post by jdallara on 2013-01-24
Thanks for the pointer, I'll have to check it out.  Ended up just moving  the /home drive was enough to save most of what I wanted.  I had done a  LOT of experimenting on this machine and after I thought about it for a  little while, a clean install was the best way to go so I wouldn't have  to remove a bunch of packages that I didn't want any more.  Thanks for  the help, I mark it as solved.

Jon

---

