---
title: "Easy to use Web gui for ubuntu server"
date: 2014-05-23
forum: General Help
---

### Post by Chelidze on 2014-05-23
Hello lovely ubuntu community
   I want to set up a home file server, Well ideally I would want to access those files from other locations as well but if it is very hard I can settle with home wireless file server  (with 0 experience).  I will be honest here [freenas]("http://www.freenas.org/") look pretty good, I watched tutorials and I can install [owncloud]("http://owncloud.org/") from its [appcenter]("http://www.freenas.org/whats-new/2013/09/plex-on-freenas.html") or something similar, but as a linux/ubuntu user I want to use an ubuntu server or at least a good linux distro that will make my life a bit easier  


 So can anyone recommend me a nice gui for ubuntu server ??? 
Thank you in advance

[COLOR=#ff0000]update[/COLOR]

Well this is my experience so far with trying to make a home file server.

 Please note that: I have no experience in this field, setting up hdd were a lot of problem on every system I tried 

[OpenMediaVault ]("http://www.openmediavault.org/")Well I can live with it, This distro comes with a nice web gui, it even has a place app center sure not a lot of software on it but it gets the job done, I tried to install owncloud on it from in build app center well it worked but I encountered one problem , the upload limit on files are set to 10 MB, I looked up on how to change this limit but none were relevant to my case. over all not a bad experience, and quite user friendly. 

[Nas4Free ]("http://www.nas4free.org/")Well for starters it is a Bsd not a linux, what I want to say with this clearly there is quite less support, sadly even though Nas4Free comes with ok web gui it does not have a app center, so you you should manual install software on it,  I installed owncloud on it and it ran but not the most pleasurable experience 

[ubuntu server]("http://www.ubuntu.com/download/server") + [webmin]("http://www.webmin.com/") well this is the place I feel mostly at home but I really did not like webmin compered to other systems i tried webmin is something that lacks focus the most, but the worst thing about ubuntu server is outdated information on the web. I got a lot of 404 errors.

[Freenas]("http://www.freenas.org/") Well i got lost in settings, sure it comes with fantastic webgui (if you know what you are doing)  but I got i do not know what I am doing, sure it comes with an app center but jails is something I do not understand and how to add hdd to jails is something that I can not comprehend 

So at this moment I am one step away from giving up on this, not because installing software is hard on any above operating systems I mentioned no the problem will be the security, there is so many things to set up and I have not a lot of information on this. Will require a lot of reading 

I think the best way out for me will be to invest in a [Synology]("http://www.synology.com/")

---

### Post by tgalati4 on 2014-05-23
I would simply install Ubuntu desktop.  Then you can use *ssh* with X-forwarding to display the desktop remotely for administration tasks.  After a while, you can turn off the desktop when you get comfortable using the command line for server tasks.  For a home server, there is not a lot of maintenance required.

I have not played with owncloud, but it is built for several linux distros including Ubuntu:  [http://software.opensuse.org/download/package?project=isv:ownCloud:community&package=owncloud](http://software.opensuse.org/download/package?project=isv:ownCloud:community&package=owncloud)

I have been running a freenas server for several years.  It's a solid home file server.

[tgalati4@freenas ~]$ uptime
 8:50AM  up **488 days**, 18:37, 1 user, load averages: 0.00, 0.00, 0.00

---

### Post by Chelidze on 2014-05-23
> **tgalati4 said:**
> I would simply install Ubuntu desktop.  Then you can use *ssh* with X-forwarding to display the desktop remotely for administration tasks.  After a while, you can turn off the desktop when you get comfortable using the command line for server tasks.  For a home server, there is not a lot of maintenance required.

I have not played with owncloud, but it is built for several linux distros including Ubuntu:  [http://software.opensuse.org/download/package?project=isv:ownCloud:community&package=owncloud](http://software.opensuse.org/download/package?project=isv:ownCloud:community&package=owncloud)

I have been running a freenas server for several years.  It's a solid home file server.

[tgalati4@freenas ~]$ uptime
 8:50AM  up **488 days**, 18:37, 1 user, load averages: 0.00, 0.00, 0.00


Thank you very much for the reply, 

Well I thought I would install on ubuntu-desktop version owncloud but it asked me for a host address so right now I do not need it.
I will try the vbox but most probably I am going to get freenas, the thing is stopping me is this, the hardware I am going to be using will be like this, there will be one HDD for os and second HDD will be ntfs hdd (well there are reasons that I can not format it right now) so can freenas use ntfs hdd or it needs to format it and use its own file system which name I can not  rem member??

again thank you for the reply

---

### Post by tgalati4 on 2014-05-23
I use ext2 and zfs on my freenas server.  I understand that NTFS support is kind of hit-or-miss:  [http://forums.freenas.org/index.php?threads/1tb-ntfs-volume-not-adding-properly.20829/#post-119953](http://forums.freenas.org/index.php?threads/1tb-ntfs-volume-not-adding-properly.20829/#post-119953)

You could use FAT32, provided your files are less than 4GB in size.  

freenas is a BSD variant and it uses UFS as the native file system.  Normally you would create a small partition for the freenas operating system, then create whatever data partitions in whatever format you need, including several different RAID configurations.  You have to play with it for a while to get comfortable with how it works.

The first time you set it up, it will work, but then 6 months later you will want to rebuild it to more closely match your needs.  There are two flavors, old and new:

[http://nas4free.org](http://nas4free.org)  This will run on a Pentium I with 256 MB ram.

and

[http://freenas.org](http://freenas.org)  This one won't.

---

### Post by Chelidze on 2014-05-23
> **tgalati4 said:**
> I use ext2 and zfs on my freenas server.  I understand that NTFS support is kind of hit-or-miss:  [http://forums.freenas.org/index.php?threads/1tb-ntfs-volume-not-adding-properly.20829/#post-119953](http://forums.freenas.org/index.php?threads/1tb-ntfs-volume-not-adding-properly.20829/#post-119953)

You could use FAT32, provided your files are less than 4GB in size.  

freenas is a BSD variant and it uses UFS as the native file system.  Normally you would create a small partition for the freenas operating system, then create whatever data partitions in whatever format you need, including several different RAID configurations.  You have to play with it for a while to get comfortable with how it works.

The first time you set it up, it will work, but then 6 months later you will want to rebuild it to more closely match your needs.  There are two flavors, old and new:

[http://nas4free.org](http://nas4free.org)  This will run on a Pentium I with 256 MB ram.

and

[http://freenas.org](http://freenas.org)  This one won't.

Thank you very much for a detailed information.
If it is not too much trouble can you give me your though on this distro [OpenMediaVault]("http://www.openmediavault.org/") 
again thank you

---

### Post by tgalati4 on 2014-05-23
I'm not familiar with it.  It looks fairly new.  Based on Debian.  Why don't you install it and give us your impressions?

---

