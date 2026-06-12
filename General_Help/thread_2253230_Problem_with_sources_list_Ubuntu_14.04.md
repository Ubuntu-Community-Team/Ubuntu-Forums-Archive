---
title: "Problem with sources list Ubuntu 14.04"
date: 2014-11-18
forum: General Help
---

### Post by cal1j on 2014-11-18
Hi,

After the last several installations of Ubuntu that I have done, I have quickly had reoccurring problems with the system not updating correctly when I use apt-get. I can't seem to figure out the issue. Here is the output of```
$ sudo apt-get update | tee /home/$USER/Desktop/log_update.txt
```:

```
Ign http://dl.google.com stable InReleaseIgn http://us.archive.ubuntu.com trusty InRelease
Ign http://security.ubuntu.com trusty-security InRelease
Hit http://dl.google.com stable Release.gpg
Ign http://ppa.launchpad.net trusty InRelease
Ign http://us.archive.ubuntu.com trusty-updates InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Ign http://extras.ubuntu.com trusty InRelease
Ign http://archive.ubuntu.com raring InRelease
Hit http://dl.google.com stable Release
Get:2 http://security.ubuntu.com trusty-security Release [62.0 kB]
Ign http://us.archive.ubuntu.com trusty-backports InRelease
Ign http://ppa.launchpad.net trusty InRelease
Hit http://extras.ubuntu.com trusty Release.gpg
Ign http://archive.ubuntu.com raring Release.gpg
Hit http://us.archive.ubuntu.com trusty Release.gpg
Hit http://extras.ubuntu.com trusty Release
Ign http://ppa.launchpad.net trusty InRelease
Hit http://archive.getdeb.net trusty-getdeb InRelease
Get:3 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Ign http://archive.ubuntu.com raring Release
Hit http://dl.google.com stable/main amd64 Packages
Get:4 http://security.ubuntu.com trusty-security/main Sources [49.5 kB]
Get:5 http://us.archive.ubuntu.com trusty-backports Release.gpg [933 B]
Ign http://ppa.launchpad.net trusty InRelease
Hit http://extras.ubuntu.com trusty/main Sources
Hit http://dl.google.com stable/main i386 Packages
Hit http://us.archive.ubuntu.com trusty Release
Get:6 http://security.ubuntu.com trusty-security/restricted Sources [14 B]
Hit http://archive.getdeb.net trusty-getdeb/apps amd64 Packages
Get:7 http://us.archive.ubuntu.com trusty-updates Release [62.0 kB]
Hit http://extras.ubuntu.com trusty/main amd64 Packages
Ign http://ppa.launchpad.net trusty InRelease
Get:8 http://security.ubuntu.com trusty-security/universe Sources [13.5 kB]
Hit http://extras.ubuntu.com trusty/main i386 Packages
Ign http://ppa.launchpad.net trusty InRelease
Get:9 http://security.ubuntu.com trusty-security/multiverse Sources [702 B]
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages
Get:10 http://security.ubuntu.com trusty-security/main amd64 Packages [153 kB]
Ign http://ppa.launchpad.net trusty InRelease
Get:11 http://us.archive.ubuntu.com trusty-backports Release [62.0 kB]
Ign http://ppa.launchpad.net trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://ppa.launchpad.net trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Get:12 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Hit http://us.archive.ubuntu.com trusty/universe Sources
Get:13 http://security.ubuntu.com trusty-security/universe amd64 Packages [61.7 kB]
Hit http://ppa.launchpad.net trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Get:14 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1,130 B]
Ign http://ppa.launchpad.net trusty Release.gpg
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Get:15 http://security.ubuntu.com trusty-security/main i386 Packages [147 kB]
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://ppa.launchpad.net trusty Release.gpg
Ign http://dl.google.com stable/main Translation-en_US
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://ppa.launchpad.net trusty Release.gpg
Ign http://dl.google.com stable/main Translation-en
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty Release.gpg
Get:16 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Get:17 http://security.ubuntu.com trusty-security/universe i386 Packages [61.7 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty Release
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en
Get:18 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,401 B]
Ign http://extras.ubuntu.com trusty/main Translation-en
Hit http://ppa.launchpad.net trusty Release
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://ppa.launchpad.net trusty Release
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Ign http://ppa.launchpad.net trusty Release
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://ppa.launchpad.net trusty Release
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://ppa.launchpad.net trusty Release
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Get:19 http://us.archive.ubuntu.com trusty-updates/main Sources [136 kB]
Err http://archive.ubuntu.com raring/main amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring/main i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Hit http://ppa.launchpad.net trusty Release
Ign http://archive.ubuntu.com raring/main Translation-en_US
Get:20 http://us.archive.ubuntu.com trusty-updates/restricted Sources [1,408 B]
Get:21 http://us.archive.ubuntu.com trusty-updates/universe Sources [90.7 kB]
Ign http://archive.ubuntu.com raring/main Translation-en
Get:22 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [3,536 B]
Get:23 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [356 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Get:24 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [5,820 B]
Get:25 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [219 kB]
Get:26 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [9,381 B]
Get:27 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [350 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Get:28 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:29 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [219 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en
Get:30 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [9,532 B]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Get:31 http://us.archive.ubuntu.com trusty-backports/main Sources [4,760 B]
Get:32 http://us.archive.ubuntu.com trusty-backports/restricted Sources [14 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Get:33 http://us.archive.ubuntu.com trusty-backports/universe Sources [16.5 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages
Get:34 http://us.archive.ubuntu.com trusty-backports/multiverse Sources [1,883 B]
Hit http://ppa.launchpad.net trusty/main Translation-en
Get:35 http://us.archive.ubuntu.com trusty-backports/main amd64 Packages [6,356 B]
Get:36 http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages [14 B]
Get:37 http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages [19.2 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Get:38 http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,231 B]
Get:39 http://us.archive.ubuntu.com trusty-backports/main i386 Packages [6,379 B]
Hit http://ppa.launchpad.net trusty/main i386 Packages
Get:40 http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages [14 B]
Get:41 http://us.archive.ubuntu.com trusty-backports/universe i386 Packages [19.3 kB]
Get:42 http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,235 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Fetched 2,160 kB in 23s (91.9 kB/s)
```


What the heck am I doing wrong? I can't seem to track down any broken PPA's and this is a fairly new install. Probably a total noob issue even though I've run Ubuntu since 10.04. Thanks in advance.

---

### Post by plucky on 2014-11-18
Post output for ```
cat /etc/apt/sources.list.d/*.list
```

Also ```
Err http://archive.ubuntu.com raring/main amd64 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
Err http://archive.ubuntu.com raring/main i386 Packages
  404  Not Found [IP: 2001:67c:1360:8c01::18 80]
```

Why is there a Raring repository in your sources.list?

Is this an Upgrade?

Post your sources.list ```
cat /etc/apt/sources.list
```

---

### Post by grahammechanical on 2014-11-18
If you disable those PPAs a lot of the errors will go away. Some PPAs provide updates to the software. Other PPAs do not. You can re-enable them one at a time and see which ones are still useful.

Those "404 Not Found" messages mean the same thing as when they appear after trying to access a web page - the URL address is broken.

Regards.

---

### Post by cal1j on 2014-11-20
Sorry for the delay: 

```
cat /etc/apt/sources.list.d/*.list
deb [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) trusty main
deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) trusty main
deb [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu](http://ppa.launchpad.net/fkrull/deadsnakes/ubuntu) trusty main
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) trusty-getdeb apps
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
deb [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu) trusty main
deb [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) trusty main
```
# deb-src [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) trusty main
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) trusty main

---

### Post by cal1j on 2014-11-20
[COLOR=#000000][INDENT]```
[COLOR=#222222]cat /etc/apt/sources.list
[/COLOR][COLOR=#222222]# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted[/COLOR][/INDENT]
[/COLOR]# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://archive.ubuntu.com/ubuntu/ raring main
[COLOR=#000000][INDENT][COLOR=#222222]deb http://download.virtualbox.org/virtualbox/debian trusty contrib[/COLOR][/INDENT]
[/COLOR]
```[COLOR=#000000][INDENT]
[/INDENT]
[/COLOR]

---

### Post by cal1j on 2014-11-20
Wow, that last got garbled on formatting. Sorry!!!

---

### Post by cal1j on 2014-11-20
grahammechanical,

How would I know which PPA's to remove. I checked using the error messages and grep'ed to find matching PPA's and was unable to do so. Probably a dumb question, but obviously I'm missing somethig very basic

---

### Post by plucky on 2014-11-20
```
deb http://ppa.launchpad.net/colingille/freshlight/ubuntu trusty main
deb http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu trusty main
```

Those two don't have "trusty" repositories.

I would remove those two from the list.

Then see if you get the same error.

```
deb http://archive.ubuntu.com/ubuntu/ raring main
```

and put a # at the front of that line.

Good Luck

---

### Post by cal1j on 2014-11-20
Wow, you guys are the greatest coaches. Got rid of all error messages. Thank you so very much.

---

