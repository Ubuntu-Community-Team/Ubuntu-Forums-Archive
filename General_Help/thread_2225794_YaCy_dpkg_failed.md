---
title: "YaCy dpkg failed"
date: 2014-05-23
forum: General Help
---

### Post by coljohnhannibalsmith on 2014-05-23
While trying to update YaCy, which is available in Synaptic Package Manager, there was a dpkg error. Synapic shows YaCy 1.73.9056 installed, but I cannot pull up the search page.

Thanks, Hannibal

---

### Post by bapoumba on 2014-05-24
Had to search about YaCy :)

How did you install it ? If you have it in synaptic, I guess you used a repo, which one ? 
[http://www.yacy-websuche.de/wiki/index.php/En:DebianInstall](http://www.yacy-websuche.de/wiki/index.php/En:DebianInstall) < this one ?
[http://yacy.net/en/index.html](http://yacy.net/en/index.html) < here is a direct install without a repo.

---

### Post by coljohnhannibalsmith on 2014-05-28
I have Ubuntu 12.04 Precise Pangolin, and I Installed it from synaptic.  I don't know what the repo is.

Thanks, Hannibal

---

### Post by bapoumba on 2014-05-28
To know what is in your sources.list and if you have additional repositories enabled :
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

Do you know the exact package name ? Could you please post the dpkg error ? Thanks.

---

### Post by coljohnhannibalsmith on 2014-05-30
```

```
sophie@sophie-Inspiron-5520:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://debian.yacy.net](http://debian.yacy.net) ./
# deb-src [http://debian.yacy.net](http://debian.yacy.net) ./
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) precise main
# deb-src [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) precise main
deb [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) precise main
# deb-src [http://www.remastersys.com/ubuntu](http://www.remastersys.com/ubuntu) precise main
sophie@sophie-Inspiron-5520:~$ ^C
sophie@sophie-Inspiron-5520:~$ 
```

```

```

```
sophie@sophie-Inspiron-5520:~$ ls /etc/apt/sources.list.d
danielrichter2007-grub-customizer-precise.list
danielrichter2007-grub-customizer-precise.list.save
google-earth.list
google-earth.list.save
thomas_tsai-ubuntu-tuxboot-precise.list
thomas_tsai-ubuntu-tuxboot-precise.list.save
sophie@sophie-Inspiron-5520:~$ 
```

```

[h=3][Installation Error in YaCy 1.73.9056]("http://www.yacy-forum.org/viewtopic.php?f=12&t=9896#p16717")[/h] 			[[IMG]http://www.yacy-forum.org/styles/prosilver/imageset/icon_post_target.gif[/IMG]]("http://www.yacy-forum.org/viewtopic.php?p=16717#p16717")by **[johnw54321]("http://www.yacy-forum.org/memberlist.php?mode=viewprofile&u=1099")** » Fri May 23, 2014 3:40 pm 
  			  			I get the following error: E: yacy: subprocess installed post-installation script returned error exit status 1.

The package is broken and I cannot connect to the search page.

Thanks

---

### Post by bapoumba on 2014-05-30
OK thanks, sorry I missed the dpkg error the other day.

I'm still unsure where the package is coming from as you said you found it in synaptic ..
This page shows how to use a repository : [http://www.yacy-websuche.de/wiki/index.php/En:DebianInstall](http://www.yacy-websuche.de/wiki/index.php/En:DebianInstall) but is does not show in your /etc/apt/sources.list.d where your third party repos are located.

[http://ubuntuforums.org/showthread.php?t=2155261](http://ubuntuforums.org/showthread.php?t=2155261)
Looks like they downloaded from this page : [http://yacy.net/en/index.html](http://yacy.net/en/index.html) and just unpacked it. Is that what you did ?

Anyway, here is a thread with the same error on debian, from their forums, that might help you : [http://www.yacy-forum.org/viewtopic.php?f=2&t=584](http://www.yacy-forum.org/viewtopic.php?f=2&t=584)

---

### Post by coljohnhannibalsmith on 2014-06-01
[LIST]
[*]
[*]
[*]
[*]
[/LIST]
 			  			[h=3][Re: I Can't Install From The Debian Package On Ubuntu 12.04]("http://www.yacy-forum.org/viewtopic.php?f=12&t=10154&p=16984#p16984")[/h] 			[[IMG]http://www.yacy-forum.org/styles/prosilver/imageset/icon_post_target.gif[/IMG]]("http://www.yacy-forum.org/viewtopic.php?p=16984#p16984")by **[johnw54321]("http://www.yacy-forum.org/memberlist.php?mode=viewprofile&u=1099")** » Sun Jun 01, 2014 6:48 am 
  			  			Hello, 

I purged YaCy and I reinstalled it with no errors; but I couldn't pull the search page up.

Thanks, Hannibal

---

### Post by bapoumba on 2014-06-01
Just to note I cannot view the threads at YaCY forums you linked to in both your previous post as they require to be logged in.

---

### Post by coljohnhannibalsmith on 2014-06-02
Hello,

I installed from synaptic, also I've finally gotten it to install correctly.

Here is the error:
Starting YaCy P2P Web Search: failed.
invoke-rc.d: initscript yacy, action "start" failed.
dpkg: error processing yacy (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 yacy
E: Sub-process /usr/bin/dpkg returned an error code (1)
sophie@sophie-Inspiron-5520:~$

---

### Post by bapoumba on 2014-06-02
The install process exited with an error, the package is not correctly installed. Is it supposed to work with your Ubuntu release ?

---

### Post by coljohnhannibalsmith on 2014-06-02
I believe any package greater than 1.72 requires JDK-7. I believe I have JDK-6.  How can I change it without breaking anything?

Thanks, John

---

### Post by bapoumba on 2014-06-03
> **coljohnhannibalsmith said:**
> I believe any package greater than 1.72 requires JDK-7. I believe I have JDK-6.  How can I change it without breaking anything?

Thanks, John
May be here :
[http://ubuntuforums.org/showthread.php?t=1969338](http://ubuntuforums.org/showthread.php?t=1969338)
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by coljohnhannibalsmith on 2014-06-05
Yes,

I got it from my Ubuntu Repository and it has been working for years.  One caveat is that YaCy updates about twice a week.

Thanks, Hannibal

---

