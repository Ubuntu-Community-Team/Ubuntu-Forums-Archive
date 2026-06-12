---
title: "Suggestion to improve post-install config!"
date: 2004-11-08
forum: General Help
---

### Post by sb73542 on 2004-11-08
Hello, I've got an idea.

From what I've read, the biggest complaint about Ubuntu is its lack of certain common programs, especially multimedia.  I realize that these can't be included do to their "non-free" nature, and I also realize they are fairly easy to install using synaptic.  However, anyone who is stuck with a slow dialup connection to the internet will probably agree that synaptic is not the answer for the countless linux users who still are forced to dialup.  On my connection, even an apt-get update takes 15 to 30 minutes, just to download package lists!  Many users do have access to broadband somewhere, and they are able to use the (now) old fashioned method of downloading programs and burning them to CD's or flash drives, or ordering them from a cheap online vendor.  However, with many linux programs  this is almost impossible to do manually because of the dependancies.  Many times the computer with broadband is running Windows, which basically means you have to manually read the package requirements and then start clicking your way through FTP directories and HTTP directory listings and start downloading about 25 big and little files.  

To improve this, why not create a multimedia meta package (is that the right word?) in universe?  It is fairly easy to download a 50 MB file, and then just install it on any computer.  To make it even easier, a simple shell script could be provided to be run with sudo, which would create symlinks and edit simple config files.  This could even help broadband users to configure their systems after they download programs.  I think the following programs with their dependancies are probably the most important to add on top of a default ubuntu installation:
-mplayer or xine+totem
-mplayer plugin or moz-plugger for firefox
-all the necessary codecs for sound and video
-Real Player 10 + plugin configured
-Sun JRE + firefox plugin configured
-Flash player plugin installed and configured for firefox

Any suggestions or thoughts?  Is this feasible?  Thanks for your help!!

---

### Post by ubuntu-geek on 2004-11-09
You may wish to mention your thoughts to the Ubuntu Dev list.. This will ensure they see it.

[http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel](http://lists.ubuntu.com/mailman/listinfo/ubuntu-devel)

---

### Post by TravisNewman on 2004-11-10
[QUOTE=sb73542]Hello, I've got an idea.

From what I've read, the biggest complaint about Ubuntu is its lack of certain common programs, especially multimedia.  I realize that these can't be included do to their "non-free" nature, and I also realize they are fairly easy to install using synaptic.  However, anyone who is stuck with a slow dialup connection to the internet will probably agree that synaptic is not the answer for the countless linux users who still are forced to dialup.  On my connection, even an apt-get update takes 15 to 30 minutes, just to download package lists!  Many users do have access to broadband somewhere, and they are able to use the (now) old fashioned method of downloading programs and burning them to CD's or flash drives, or ordering them from a cheap online vendor.  However, with many linux programs  this is almost impossible to do manually because of the dependancies.  Many times the computer with broadband is running Windows, which basically means you have to manually read the package requirements and then start clicking your way through FTP directories and HTTP directory listings and start downloading about 25 big and little files.  

To improve this, why not create a multimedia meta package (is that the right word?) in universe?  It is fairly easy to download a 50 MB file, and then just install it on any computer.  To make it even easier, a simple shell script could be provided to be run with sudo, which would create symlinks and edit simple config files.  This could even help broadband users to configure their systems after they download programs.  I think the following programs with their dependancies are probably the most important to add on top of a default ubuntu installation:
-mplayer or xine+totem
-mplayer plugin or moz-plugger for firefox
-all the necessary codecs for sound and video
-Real Player 10 + plugin configured
-Sun JRE + firefox plugin configured
-Flash player plugin installed and configured for firefox

Any suggestions or thoughts?  Is this feasible?  Thanks for your help!![/QUOTE]
 A lot of these, unfortunately, may have legal issues attached to them. Of course, they're already there in multiverse, so I don't guess it REALLY matters that much, but making them more prominent might actually make the-higher-ups start caring about it.

---

### Post by sb73542 on 2004-11-10
[QUOTE=panickedthumb]A lot of these, unfortunately, may have legal issues attached to them. Of course, they're already there in multiverse, so I don't guess it REALLY matters that much, but making them more prominent might actually make the-higher-ups start caring about it.[/QUOTE]
 Yes, I thought about that too.  Maybe if MEPIS can get away with it, Ubuntu can too.  But at any rate try to include as much as possible, especially the OSS stuff.  Thanks!  (I'll post this to mailing list)

---

