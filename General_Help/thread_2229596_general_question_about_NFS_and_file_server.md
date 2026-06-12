---
title: "general question about NFS and file server"
date: 2014-06-14
forum: General Help
---

### Post by bearboy518 on 2014-06-14
hello,

I currently run Ubuntu on a laptop and 2 desktops.  I use ssh and nfs between all three machines.  I was wondering how feasable it would be to buy a brand new hard drive and make the one I always have running a file server and make /home common between all three? is this possible and feasble? I know it's possible and I could probably do it, and I understand its wireless and there is little possibility right now of me making it wired, but do the machines need different files in the home directories to make them run correctly?

my second question is..when browsing files in the browser, is there any way to make the file info and size appear in list format?

thanks for any help you can give

---

### Post by TheFu on 2014-06-14
Sharing HOME over a network has been a core method in corporate environments since the 1980s.  It works.

However - I'd NEVER attempt this over wifi.  The bandwidth is just too variable - in a way that humans don't notice, but machines do.  Look into wireline/powerline networking to solve the current cable issue.

So - do different machines need different files to make them work?  I'll explain with a story.  I've run with the same home directory shared for years.  The systems involved were NOT even the same type - SunOS, Solaris, Irix, HP-UX, AIX, Ultrix, OSF/1, and Linux.  The differences mean that some commands need to be modified.  Thankfully, there are commonly used environment variables that can be checked to see what machine architecture is running to group commands in that way - then for machine specific stuff - just check the hostname.  This needs to be done inside the startup files ... 
* .profile
* .bashrc
* .aliases
* .cshrc, .tcshrc ....
You get the idea.

Then we make use of program specific environment variables per-server.  JAVA_HOME is a good example - JAVA is installed in different places on almost every sort of machine.

If all the machines are Linux running the same distro, I wouldn't worry.  Where issues happen is when different DEs are used.  Some DEs are not compatible with others and screw with the config files inside ~/.config/  

So ... it may be easier to just have shared data storage mounted under your HOME on each machine these days.  I use a /D/ for data stored on NFS.  Then use autofs to mount it only when needed on each machine here. I've played with it over wifi about 25ft away from the router almost line-of-sight - is works, mostly, but when it doesn't work - it can lock up the system.  Yep, wired is 1000x better.

So, I know you're gonna try the HOME thing anyway. I would too. ;)  Be careful that the options used match your needs.  Also, DO NOT MAKE THE NFS SERVER non-wired - don't use wifi for it. PERIOD.  File corruption is the reason for that.

Can't answer the 2nd question - don't use a GUI for file management - too slow.

---

### Post by bearboy518 on 2014-06-14
OK.  I will not use common /home directory over wireless.  But I am moving soon.  If I am able to make the network wired, do I have to start over or what? How would I go about merging the three computers?  Just copying 3 and copying the Downloads, Pictures, etc., and not the . directories? will they function without these directories? or do I have to reinstall each machine and just make the home directory on the machine I do the most work on the shared one? I do use programs like gimp, chrome, etc. on each one, is this going to cause a problem?

---

### Post by TheFu on 2014-06-15
Pick 1 system /home to be the NFS server, move the /home from the other systems to somewhere else, create the new mount point, /home and setup NFS to mount it there.

Or mount the selected HOME somewhere else and modify the userid account information inside the /etc/passwd file.  /home is nothing special to the system. It can be anywhere - provided the passwd file knows where it is.  There are other requirements to make it useful as a general user HOME - owned by the userid, ... stuff like that.

Whether any of those programs have issues or not is completely up to the programmer.  No settings should be absolute paths - always off the $HOME variable, so it really shouldn't matter if the mount points are different on different machines ... but I'd make them all identical for simplicity.

---

### Post by oldfred on 2014-06-15
I use fallback/flashback so how you set Nautilus may be different. But in 12.04 you open edit, preferences and change default view to list view.
In 14.04 I originally had trouble finding where that was, but there is a tiny icon on the right that is the setting. You can also add ownership & permissions to view.

I only use NFS to copy my data partitions from my desktop to laptop when traveling & back when I return. But I have many installs on desktop and only have two shared data partitions. One is still NTFS from when I still booted XP, and the other Linux formatted for all new data. But I prefer to have /home inside my install and with no data it is tiny. My /home is about 2GB and 1.5GB of that is .wine for my Picasa, so settings must be only 500MB? And I prefer that each install boot without any other hard drive working, even if I get errors on /mnt/data or swap not mounting. Or I want /home inside my working install or at least on same drive.

---

