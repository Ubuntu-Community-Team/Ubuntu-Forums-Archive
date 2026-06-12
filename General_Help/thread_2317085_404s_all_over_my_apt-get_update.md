---
title: "404s all over my apt-get update"
date: 2016-03-13
forum: General Help
---

### Post by Dauus on 2016-03-13
Hi! 
I just installed Ubuntu 15.10 and have been trying to get it up and running all morning. So far so good. However, whenever I "sudo apt-get update" for my PPAs, I start getting 404'd all over the place. WHAT A BUMMER! I have searched the forums for various solutions (unchecking, removing various PPAs, running clean and autoremove, dealing with them one-by-one) but to no avail.  Here is a print out of my sources list:

```
# deb cdrom:[Ubuntu 15.10 _Wily Werewolf_ - Release amd64 (20151021)]/ wily main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) wily main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) wily main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) wily-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) wily-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) wily universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) wily universe
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) wily-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) wily-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) wily multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) wily multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) wily-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) wily-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) wily-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) wily-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) wily partner
```

Any help will be greatly appreciated!

Thanks!

---

### Post by Dauus on 2016-03-13
I probably should have actually put my errors, right? Boy - a rough morning.  Below are the errors I receive when I run sudo apt-get update:

```
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Sources                                 
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en_US                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                          
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Sources                                 
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                          
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                           
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en_US                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                          
Fetched 2,759 B in 24s (113 B/s)                                               
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/wily/main/source/Sources](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/wily/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/dists/wily/main/source/Sources](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/dists/wily/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/dists/wily/main/binary-amd64/Packages](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/dists/wily/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Bashing-om on 2016-03-13
Dauus; Hello;

Yep .. unsupported PPAs.
In your browser go to :
[http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/)
You see that the last release supported is utopic.
I surmise the same is true for all the other 404's.

Disable the unsupported PPAs, Then work with the authors of the PPA(s) to see what they are going to do.

[INDENT][INDENT]That is all one can say
[/INDENT][/INDENT]

---

### Post by Dauus on 2016-03-13
Hi Bashing!

Thanks for your reply. That really helps. Follow up question here: will these 404 effect anything ie like updates or packages I have currently installed? I noticed that some of my 404s relate to my main repositories (if I am reading my errors right). Basically, how important is it that I resolve these 404s?

---

### Post by Dauus on 2016-03-13
So thanks to Bashing's great help, I tracked down all the PPAs, one by  one, and verified that I had the right PPA - for Pidgin, I had to change  the distro; for Handbrake, I had to point the PPA to the new, updated  PPA and get rid of the old, obsolete PPA.  The last part of this issue  was my Google Chrome install which was throwing a "W: Failed to fetch  [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to  find expected entry 'main/binary-i386/Packages' in Release file (Wrong  sources.list entry or malformed file)"  For this, I used this thread to  solve it:  [http://ubuntuforums.org/showthread.php?t=2315941&highlight=W%3A+Failed+fetch+Unable+find+expected+entry+Release+file+%28Wrong+sources.list+entry+malformed+file%29](http://ubuntuforums.org/showthread.php?t=2315941&highlight=W%3A+Failed+fetch+Unable+find+expected+entry+Release+file+%28Wrong+sources.list+entry+malformed+file%29)

If you run into this same problem, feel free to either start a new thread or PM me!

---

### Post by Bashing-om on 2016-03-13
Dauus; Hey hey !

You do good work.

Package manager all happy now ? ( no mixing distros or release versions !)

[INDENT][INDENT]if the package manager is not happy
[INDENT][INDENT][INDENT]no one is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

