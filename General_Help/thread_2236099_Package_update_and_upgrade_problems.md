---
title: "Package update and upgrade problems"
date: 2014-07-24
forum: General Help
---

### Post by Grendergon on 2014-07-24
Hello, I am having problems updating my lubuntu 12.10 quantal over to raring and other stable releases.  In addition, I am having trouble installing updates and most other packages.  I have followed tutorials for common problems with the sources.list file and but have been unable to locate the source of my frustrations.  These include running a script for cleaning up 404 messages in the sources list, and checking to make sure checks are next to all the appropriate software sources.  In one tutorial, I read that I should go to the sources file and remove any "ppa's" from the list not ending in "main," but did not find any ppa addresses at all.  Any help is appreciated.

```
will@will-ThinkPad-T61:~$ cat /etc/apt/sources.list# deb cdrom:[Lubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.1)]/ quantal main multiverse restricted universe


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal universe
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security universe
deb-src http://security.ubuntu.com/ubuntu quantal-security universe
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main



```

---

### Post by sudodus on 2014-07-24
Welcome to the Ubuntu Forums :-)

Unfortunately you have waited too long to upgrade via the guided upgrade method. 12.10 as well as 13.04 and 13.10 have passed end of life and are no longer supported. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229730"]
Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.[/URL]

I would recommend that you

0. Backup your whole system or at least all your important data.

1. [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389") 

2. Create a separate home partition (move your current /home directory to a separate partition).

3. Make a fresh installation of a current version of Ubuntu 12.04 LTS or 14.04 LTS or an Ubuntu flavour (Lubuntu and Xubuntu are better for old hardware). Select ***Something else*** at the partitioning screen, and set the installer to use your new home partition and do ***not*** format it.

---

### Post by Dennis N on 2014-07-24
12.10 is not supported any longer, and unfortunately an upgrade is not possible because the only version you can upgrade to - 13.04, is also not supported any longer. Repositories for both are closed and not accessible - hence the 404 messages.

The only good option is to back up your data, and do a fresh install of 14.04.

---

### Post by QIII on 2014-07-24
Hello!

Unfortunately, 12.10, 13.04 and 13.10, which would be your upgrade path to 14.04, are *all *past EOL (End Of Life) and the repos have been moved.

I would feel very uncomfortable advising you how you can upgrade through old versions because the possibility of borking things altogether is just too high.

My recommendation would be to back up any important files (particularly your /home) and do a fresh install of 14.04.

We no longer support requests for help with EOL/Unsupported versions of Ubuntu.  See [this]("http://ubuntuforums.org/showthread.php?t=2229730") sticky.

(Oh, and obviously ninja'd by sudodus!)

---

