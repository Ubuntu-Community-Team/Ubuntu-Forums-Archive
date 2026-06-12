---
title: "Everything that looks for packages is now broken."
date: 2007-11-02
forum: General Help
---

### Post by XanderVincent on 2007-11-02
Well, I was trying to do this:

[http://www.ubuntugeek.com/install-popular-applications-in-ubuntu-feisty-fawn-using-automatix2.html](http://www.ubuntugeek.com/install-popular-applications-in-ubuntu-feisty-fawn-using-automatix2.html)

Which may have broke my Synaptic Package Manager.

For one, when I do the sudo apt-get update it returns with this error:

E: Type '“deb' is not known on line 50 in source list /etc/apt/sources.list

It also does this when trying to open Synaptic Package Manager, and everything else that looks for packages.

Alls I wanted was Frostwire + Java to work, so I thought that automatix was a good idea, but now my linux isn't looking in the right spot for packages.

Help?

---

### Post by Pumalite on 2007-11-02
Read this:

[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)
[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)
[http://ubuntuforums.org/showthread.php?t=519872](http://ubuntuforums.org/showthread.php?t=519872)
[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by Pumalite on 2007-11-02
Post your /etc/apt/sources.list

---

### Post by XanderVincent on 2007-11-02
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
#See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
#newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

#Major bug fix updates produced after the final release of the
#distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

#N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
#team, and may not be under a free licence. Please satisfy yourself as to
#your rights to use the software. Also, please note that software in
#universe WILL NOT receive any review or updates from the Ubuntu security
#team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

#N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
#team, and may not be under a free licence. Please satisfy yourself as to 
#your rights to use the software. Also, please note that software in 
#multiverse WILL NOT receive any review or updates from the Ubuntu
#security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

#Uncomment the following two lines to add software from the 'backports'
#repository.
#N.B. software from this repository may not have been tested as
#extensively as that contained in the main release, although it includes  newer versions of some applications which may provide useful features.
#Also, please note that software in backports WILL NOT receive any review
#or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

As you can see, there is no line 50.

---

### Post by XanderVincent on 2007-11-02
I mean I don't exactly need automatix, so fixing this back to normal would be better than fixing it to get me automatix.

The whole reason for automatix for me was to get java + frostwire. Those are my main priority.

---

### Post by Pumalite on 2007-11-02
There is a package stuck and we need the name. I think this might work:

sudo dpkg --remove --force-remove-reinstreq <packagename>

Check in /var/lib/dpkg/status and see which one it is.

---

### Post by XanderVincent on 2007-11-02
That file is a few thousand lines long.

Would it be one that doesn't say "Status: installed ok installed" or is there some easy way to find which one it is.

---

### Post by Pumalite on 2007-11-02
Exactly. The one saying installed ok installed is OK: The others are not.

---

### Post by dcstar on 2007-11-02
> **XanderVincent said:**
> deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

**deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted**
......
As you can see, there is no line 50.

In a terminal:
```
gksudo gedit /etc/apt/sources.list
```
and delete the duplicate CDROM line and save the changed file.

This won't be the issue, but saving the edited file might just fix a possible corruption that is giving you the "line 50" error.

---

