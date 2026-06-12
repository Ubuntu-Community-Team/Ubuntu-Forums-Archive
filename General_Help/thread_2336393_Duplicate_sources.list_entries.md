---
title: "Duplicate sources.list entries"
date: 2016-09-07
forum: General Help
---

### Post by watchpocket on 2016-09-07
I am getting duplicate errors when I run *sudo apt update*. 

This is after making an ***/etc/apt/sources.list.bak*** file (and then deleting the  ***/etc/apt/sources.list ***file):
```
Reading package lists... Done                                                  
W: Duplicate sources.list entry http://extras.ubuntu.com/ubuntu/ trusty/main amd64 Packages (/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://extras.ubuntu.com/ubuntu/ trusty/main i386 Packages (/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems  ***<-- (DOES NOTHING)***
```

Here is my current ***/etc/apt/sources.list*** file
```

  1 # deb cdrom:[Ubuntu MATE 14.04.1 _Trusty Tahr_ - final amd64 (20141111)]/ trusty main restricted
  2 # deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted #Added by software-properties
  3 
  4 # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
  5 # newer versions of the distribution.
  6 
  7 deb http://ubuntu.mirror.constant.com/ trusty restricted universe main
  8 # deb-src http://ubuntu.mirror.constant.com/ trusty main restricted #Added by software-properties
  9 # deb-src http://ubuntu.mirror.constant.com/ trusty universe multiverse #Added by software-properties
 10 
 11 
 12 ## Major bug fix updates produced after the final release of the distribution.
 13 deb http://ubuntu.mirror.constant.com/ trusty-updates restricted universe main
 14 # deb-src http://ubuntu.mirror.constant.com/ trusty-updates restricted universe multiverse main #Added by software-properties
 15 
 16 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu-
 17 ## team, and may not be under a free licence. Please satisfy yourself as to-
 18 ## your rights to use the software. Also, please note that software in-
 19 ## multiverse WILL NOT receive any review or updates from the Ubuntu
 20 ## security team.
 21 deb http://ubuntu.mirror.constant.com/ trusty multiverse
 22 deb http://ubuntu.mirror.constant.com/ trusty-updates multiverse
 23 
 24 ## N.B. software from this repository may not have been tested as
 25 ## extensively as that contained in the main release, although it includes
 26 ## newer versions of some applications which may provide useful features.
 27 ## Also, please note that software in backports WILL NOT receive any review
 28 ## or updates from the Ubuntu security team.
 29 deb http://ubuntu.mirror.constant.com/ trusty-backports restricted multiverse universe main
 30 # deb-src http://ubuntu.mirror.constant.com/ trusty-backports restricted universe multiverse main #Added by software-properties
 31 
 32 deb http://ubuntu.mirror.constant.com/ trusty-security restricted universe main
 33 deb http://ubuntu.mirror.constant.com/ trusty-security multiverse
 34 # deb-src http://ubuntu.mirror.constant.com/ trusty-security restricted universe multiverse main #Added by software-properties
 35 
 36 ## Uncomment the following two lines to add software from Canonical's 'partner' repository.
 37 ## This software is not part of Ubuntu, but is offered by Canonical and the
 38 ## respective vendors as a service to Ubuntu users.
 39 deb http://archive.canonical.com/ubuntu trusty partner
 40 # deb-src http://archive.canonical.com/ubuntu trusty partner
 41 
 42 ## This software is not part of Ubuntu, but is offered by third-party
 43 ## developers who want to ship their latest software.
 44 deb http://extras.ubuntu.com/ubuntu trusty main
 45 # deb-src http://extras.ubuntu.com/ubuntu trusty main
 46 
 47 deb http://ppa.launchpad.net/jean-francois-dockes/mpd/ubuntu trusty main #MPD - Music Player Daemon
 48 deb http://ppa.launchpad.net/ubuntuhandbook1/cantata-qt/ubuntu trusty main #Cantata - GUI MPD Client for Linux
 49 deb http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu trusty main #DeaDBeeF - "The Ultimate Music Player"
 50 deb http://ppa.launchpad.net/rvm/smplayer/ubuntu trusty main #SMPlayer - GUI front-end for MPlayer and mpv
 51 deb http://ppa.launchpad.net/andreas-boettger/gmusicbrowser-daily/ubuntu trusty main #GMusicBrowser - customizable open-source jukebox for large music-file collections
 52 deb http://ppa.launchpad.net/lightdm-gtk-greeter-team/stable/ubuntu trusty main #LightDM GTK+ Greeter
 53 # deb http://ppa.launchpad.net/jfi/ppa/ubuntu trusty main #Psensor - GUI hardware temperature monitor
 54 # deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main #Various Multimedia Packages
 55 # deb http://ppa.launchpad.net/micahg/ppa/ubuntu trusty main #VLC Media Player (backported to trusty)
 56 deb http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu trusty main #Stuff needed to either build UbuntuMATE .iso images or provide meta packages
 57 deb http://ppa.launchpad.net/ubuntu-mate-dev/trusty-mate/ubuntu trusty main #To install and configure this MATE 1.8.1 stuff on Trusty you need the PPA above
 58 deb http://ppa.launchpad.net/accessibility-dev/ppa/ubuntu trusty main #Accessibility backports/testing of stuff from the current Ubuntu devlpmnt release
 59 

```
If I un-comment lines 53, 54 and 55, I get dupes for those entries in addition to the dupes for the extras that I get now.

Here is my ***/etc/apt/sources.list/d/*** directory:

```

--> lf sources.list.d  
total 136
4 drwxr-xr-x 2 root root 4096 Sep  7 18:45 ./
4 drwxr-xr-x 6 root root 4096 Sep  7 18:54 ../
4 -rw-r--r-- 1 root root   93 Sep  7 18:54 atareao-atareao-trusty.list
4 -rw-r--r-- 1 root root   93 Sep  7 18:54 atareao-atareao-trusty.list.save
4 -rw-r--r-- 1 root root  123 Sep  7 18:54 bkgaley-ppa-trusty.list
4 -rw-r--r-- 1 root root  123 Sep  7 18:54 bkgaley-ppa-trusty.list.save
4 -rw-r--r-- 1 root root   48 Sep  7 18:44 extra-ppas.list
4 -rw-r--r-- 1 root root   48 Sep  7 18:45 extra-ppas.list.save
4 -rw-r--r-- 1 root root  109 Sep  7 18:54 gezakovacs-ppa-trusty.list
4 -rw-r--r-- 1 root root  109 Sep  7 18:54 gezakovacs-ppa-trusty.list.save
4 -rw-r--r-- 1 root root  200 Sep  7 18:54 google-talkplugin.list
4 -rw-r--r-- 1 root root  200 Sep  7 18:54 google-talkplugin.list.save
4 -rw-r--r-- 1 root root  100 Sep  7 18:54 jfi-ppa-trusty.list
4 -rw-r--r-- 1 root root  100 Sep  7 18:54 jfi-ppa-trusty.list.save
4 -rw-r--r-- 1 root root   97 Sep  7 18:54 mc3man-trusty-media-trusty.list
4 -rw-r--r-- 1 root root   97 Sep  7 18:54 mc3man-trusty-media-trusty.list.save
4 -rw-r--r-- 1 root root  123 Sep  7 18:54 micahflee-ppa-trusty.list
4 -rw-r--r-- 1 root root  123 Sep  7 18:54 micahflee-ppa-trusty.list.save
4 -rw-r--r-- 1 root root  100 Sep  7 18:54 micahg-ppa-trusty.list
4 -rw-r--r-- 1 root root  100 Sep  7 18:54 micahg-ppa-trusty.list.save
4 -rw-r--r-- 1 root root  102 Sep  7 18:54 peterlevi-ppa-trusty.list
4 -rw-r--r-- 1 root root  102 Sep  7 18:54 peterlevi-ppa-trusty.list.save
4 -rw-r--r-- 1 root root  107 Sep  7 18:54 pi-rho-dev-trusty.list
4 -rw-r--r-- 1 root root  107 Sep  7 18:54 pi-rho-dev-trusty.list.save
4 -rw-r--r-- 1 root root  112 Sep  7 18:54 pi-rho-security-trusty.list
4 -rw-r--r-- 1 root root  112 Sep  7 18:54 pi-rho-security-trusty.list.save
4 -rw-r--r-- 1 root root  124 Sep  7 18:54 remmina-ppa-team-remmina-master-trusty.list
4 -rw-r--r-- 1 root root  124 Sep  7 18:54 remmina-ppa-team-remmina-master-trusty.list.save
4 -rw-r--r-- 1 root root   88 Sep  7 18:54 system76-dev-stable-trusty.list
4 -rw-r--r-- 1 root root   88 Sep  7 18:54 system76-dev-stable-trusty.list.save
4 -rw-r--r-- 1 root root   92 Sep  7 18:54 xorg-edgers-ppa-trusty.list
4 -rw-r--r-- 1 root root   92 Sep  7 18:54 xorg-edgers-ppa-trusty.list.save
4 -rw-r--r-- 1 root root  131 Sep  7 18:54 yannubuntu-boot-repair-trusty.list
4 -rw-r--r-- 1 root root  131 Sep  7 18:54 yannubuntu-boot-repair-trusty.list.save

```

Here is the one-line  **extra-ppas.list **file that is in the* /etc/apt/sources.list.d/* directory: ```
deb http://extras.ubuntu.com/ubuntu trusty main
```
And here's a screenshot of my Software & Updates, with the "Other Software" tab open. The top two items ("Canonical Partners" and its source code line, which is unchecked) are cut off. 
[ATTACH=CONFIG]271025[/ATTACH]This all began when I started writing the comments for each item. I had Software & Updates the way I wanted it, but I noticed the the PPAs  I'd set up weren't being reached for downloading. Thanks for any tips to get these sources installed correctly.

---

### Post by QIII on 2016-09-07
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2336315](https://ubuntuforums.org/showthread.php?t=2336315)

---

### Post by watchpocket on 2016-09-07
So, in general when having a similar problem as someone who's had their solved, I take it it's still better to start a new thread than append to one marked "solved," yes?

---

### Post by QIII on 2016-09-07
Yes.  There are several reasons, not the least of which being that when a thread is marked solved it is more likely to be read by someone hoping to find an answer than by someone ready to offer help.

A couple of other reasons:

Your issue may seem to be similar on the surface, but actually be unrelated.

Threads get jumbled and confusing quickly when people pile on.

This isn't a Stack Exchange forum.  We don't close threads because someone else already asked a question.  Again, we know that similar symptoms do not always stem fom similar conditions.  We would like to provide individual attention and diagnose issues to find solutions.

---

### Post by watchpocket on 2016-09-07
It appears that if a line is in **/etc/apt/sources.list**, say:

deb [http://ppa.launchpad.net/micahg/ppa/ubuntu](http://ppa.launchpad.net/micahg/ppa/ubuntu) trusty main #VLC Media Player (backported to trusty)

and if that same line is in the file **micahg-ppa-trusty.list** in the **/etc/apt/sources.list.d** directory, then I get the duplicate warning when updating.

So, in which of the two places should that line be located?

---

### Post by ian-weisser on 2016-09-07
Which one to keep is entirely up to you.
Keep the one that makes more sense to you.

Here's one more thing to keep in mind:
```
deb http://mysource/ xenial-updates main restricted universe #Remark
```
is equivalent to:
```
#Remark
deb http://mysource/ xenial-updates main

#Remark
deb http://mysource/ xenial-updates restricted

#Remark
deb http://mysource/ xenial-updates universe

```

You have some flexibility in how you arrange and comment upon your souurces.

---

### Post by watchpocket on 2016-09-07
So if I delete, and then re-install
*deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main*

and I see that there's a 2015 version of the ***xserver-xorg-video-nouveau*** package in xorg-edgers when I filter on "Trusty"

and then I update, and also update in synaptic with Edit --> Reload Package Information,  I still see in synaptic only a 2014 package as both installed version and latest version.

Why would the 2015 version in xorg-edgers not be coming in?

---

### Post by ian-weisser on 2016-09-07
Look at:
```
apt-cache policy [COLOR=#000000]xserver-xorg-video-nouveau
```

If more than one is listed, pay close attention to the version numbers.[/COLOR]

---

### Post by watchpocket on 2016-09-07
I only see the 2014 version, still don't understand why I don't see the 2015:```
--> apt-cache policy xserver-xorg-video-nouveau 
xserver-xorg-video-nouveau:
  Installed: 1:1.0.11+git20141030.3fb97d78-0ubuntu0sarvatt~trusty2
  Candidate: 1:1.0.11+git20141030.3fb97d78-0ubuntu0sarvatt~trusty2
  Version table:
 *** 1:1.0.11+git20141030.3fb97d78-0ubuntu0sarvatt~trusty2 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     1:1.0.10-1ubuntu2 0
        500 http://ubuntu.mirror.constant.com/ trusty/main amd64 Packages
apt-cache policy xserver-xorg-video-nouveau  2.56s user 0.13s system 99% cpu 2.695 tota
```

Also:
You wrote:
> **deb [http://mysource/](http://mysource/) xenial-updates main restricted universe #Remark** is equivalent to:
          
> **#Remark**
> [B]deb [http://mysource/](http://mysource/) xenial-updates main 
[/B]
Actually, if you do that in the sources.list file,  it will *remove *that comment remark in Software & Updates.

 Can the /etc/apt/sources.list.d directory just be deleted, as long as I have all the deb entries in the sources.list file?  I gather when adding a new PPA it might get put in the directory, then I'd have to move it to the sources.list file.  But is there any reason not to delete it?

---

### Post by ian-weisser on 2016-09-07
> **watchpocket said:**
> Can the /etc/apt/sources.list.d directory just be deleted, as long as I have all the PPA entries in the sources.list file? I gather when adding a new PPA it might get put in the directory, then I'd have to move it to the sources.list file.  But is there any reason not to delete it?

The purpose of the directory is to make it easy for programs to add/delete sources without editing the original sources.list text file.
When you move sources between the directory and the sources.list file, you defeat that functionality and make it difficult for programs to add/remove sources. So you might wind up cleaning those files manually with a text editor someday.

But ultimately the sources.list file and the directory contents are just a bunch of text files that get concatenated anyway. The magic is all in the deb lines - don't mangle those!
It's your system - if you want to move those deb lines around (without mangling them), go right ahead! Best practice is to create a backup before you start editing...but you knew that already.

---

### Post by watchpocket on 2016-09-07
The only reason I'd want to delete the directory is that I'd like to see everything in one place -- the sources.list file.  But if I have a deb there, and if I also have it in the directory, I seem to get the duplicate warnings.  Why that annoyance happens, I don't quite understand.

Although maybe the right "one place" to see things is in Software & Updates.  I'll have to think about that.  Thanks for the perspective.

---

### Post by ian-weisser on 2016-09-08
> **watchpocket said:**
> Why that annoyance happens, I don't quite understand.
Because all those source files get concatenated together. They are in separate files only for the convenience of the user.

---

