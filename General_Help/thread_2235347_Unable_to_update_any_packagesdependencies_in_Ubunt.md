---
title: "Unable to update any packages/dependencies in Ubuntu 12.04"
date: 2014-07-20
forum: General Help
---

### Post by casey9 on 2014-07-20
Hello,

I am having major trouble understanding why my Ubuntu 12.04 server will not upgrade the latest packages/dependencies. Whenever I run the Update Manager in Unity, I receive the following errors:

[ATTACH=CONFIG]254865[/ATTACH]

Also, whenever I run the "sudo apt-get install -f" command in the terminal I receive the following output:

```
caseone@ixcel-ubuntu:~$ !585
sudo apt-get install -f
[sudo] password for caseone: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libva-x11-1 libxcb-xv0 libtar0 libsdl-image1.2 gir1.2-unique-3.0 libxcb-keysyms1 libxcb-composite0 libxcb-randr0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libnss3:i386
The following packages will be upgraded:
  libnss3:i386
1 upgraded, 0 newly installed, 0 to remove and 290 not upgraded.
7 not fully installed or removed.
Need to get 0 B/1,292 kB of archives.
After this operation, 12.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libnss3:i386 (--configure):
 libnss3:i386 3.15.3.1-0ubuntu0.12.04.1 cannot be configured because libnss3:amd64 is in a different version (3.15.4-0ubuntu0.12.04.2)
dpkg: error processing libnss3 (--configure):
 libnss3:amd64 3.15.4-0ubuntu0.12.04.2 cannot be configured because libnss3:i386 is in a different version (3.15.3.1-0ubuntu0.12.04.1)
dpkg: dependency problems prevent configuration of libnss3-1d:
 libnss3-1d depends on libnss3 (= 3.15.4-0ubuntu0.12.04.2); however:
  Package libnss3 is not configured yet.
dpkg: error processing libnss3-1d (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-6-jre-headless:
 openjdk-6-jre-headless depends on libnss3-1d (>= 3.12.9+ckbi-1.82-0ubuntu4); however:
  Package libnss3-1d is not configured yet.
dpkg: error processing openjdk-6-jre-headless (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-cNo apport report written because the error message indicates its a followup error from a previous failure.
             No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                       No apport report written because MaxReports is reached already
                      No apport report written because MaxReports is reached already
                                                                                    No apport report written because MaxReports is reached already
                                                                                                                                                  acao:

 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b30-1.13.1-1ubuntu2~0.12.04.3); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-cacao (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icedtea-6-jre-jamvm:
 icedtea-6-jre-jamvm depends on openjdk-6-jre-headless (= 6b30-1.13.1-1ubuntu2~0.12.04.3); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing icedtea-6-jre-jamvm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-6-jre-lib:
 openjdk-6-jre-lib depends on openjdk-6-jre-headless (>= 6b27); however:
  Package openjdk-6-jre-headless is not configured yet.
dpkg: error processing openjdk-6-jre-lib (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libnss3:i386
 libnss3
 libnss3-1d
 openjdk-6-jre-headless
 icedtea-6-jre-cacao
 icedtea-6-jre-jamvm
 openjdk-6-jre-lib
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have a very good understanding of my machine and how it works but for the past few months, I have not been able to figure out what happened and why I cannot upgrade my packages. Can someone please walk me through this process? I'm sure it's something easy but I can't place it right now.

Please let me know if you need any further logs or output.

Thanks in advance!

---

### Post by Bucky Ball on 2014-07-20
Welcome. Try these in a terminal:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Report any and all error messages.

---

### Post by bapoumba on 2014-07-20
libnspr4 4.9.5-0ubuntu0.12.04.3 is for Precise and you have 12.04.2 installed. Which Ubuntu release are you running ? 

```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by casey9 on 2014-07-20
_**BuckyBall**_ here are the error messages from the following:

Result of running sudo apt-get upgrade
--------------------------------
caseone@ixcel-ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libnss3 : Breaks: libnss3:i386 (!= 3.15.4-0ubuntu0.12.04.2) but 3.15.3.1-0ubuntu0.12.04.1 is installed
 libnss3:i386 : Breaks: libnss3 (!= 3.15.3.1-0ubuntu0.12.04.1) but 3.15.4-0ubuntu0.12.04.2 is installed
E: Unmet dependencies. Try using -f.


Result of running sudo apt-get dist-upgrade
-------------------------------
caseone@ixcel-ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libnss3 : Breaks: libnss3:i386 (!= 3.15.4-0ubuntu0.12.04.2) but 3.15.3.1-0ubuntu0.12.04.1 is installed
 libnss3:i386 : Breaks: libnss3 (!= 3.15.3.1-0ubuntu0.12.04.1) but 3.15.4-0ubuntu0.12.04.2 is installed
E: Unmet dependencies. Try using -f.


 	[**[COLOR=#990303][B]bapoumba**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=171805") - Below are the results of the commands you asked me to enter. Also the release information is here:

caseone@ixcel-ubuntu:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise


caseone@ixcel-ubuntu:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/
     2    
     3    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
     4    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted
     5    
     6    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     7    # newer versions of the distribution.
     8    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
     9    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
    10    
    11    ## Major bug fix updates produced after the final release of the
    12    ## distribution.
    13    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    14    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    15    
    16    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17    ## team. Also, please note that software in universe WILL NOT receive any
    18    ## review or updates from the Ubuntu security team.
    19    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    20    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    21    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    22    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    23    
    24    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25    ## team, and may not be under a free licence. Please satisfy yourself as to 
    26    ## your rights to use the software. Also, please note that software in 
    27    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    28    ## security team.
    29    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    30    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    31    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    32    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    33    
    34    ## N.B. software from this repository may not have been tested as
    35    ## extensively as that contained in the main release, although it includes
    36    ## newer versions of some applications which may provide useful features.
    37    ## Also, please note that software in backports WILL NOT receive any review
    38    ## or updates from the Ubuntu security team.
    39    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    40    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    41    
    42    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    43    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    44    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    45    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    46    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    47    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    48    
    49    ## Uncomment the following two lines to add software from Canonical's
    50    ## 'partner' repository.
    51    ## This software is not part of Ubuntu, but is offered by Canonical and the
    52    ## respective vendors as a service to Ubuntu users.
    53    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    54    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    55    
    56    ## This software is not part of Ubuntu, but is offered by third-party
    57    ## developers who want to ship their latest software.
    58    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    59    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

caseone@ixcel-ubuntu:~$ ls -la /etc/apt/sources.list.d
total 60
drwxr-xr-x 2 root root 4096 Apr 26 17:40 .
drwxr-xr-x 6 root root 4096 Apr 26 17:40 ..
-rw-r--r-- 1 root root  136 Apr 26 17:40 banshee-team-ppa-precise.list
-rw-r--r-- 1 root root  176 Apr 26 17:40 google-chrome.list
-rw-r--r-- 1 root root  176 Apr 26 17:40 google-chrome.list.save
-rw-r--r-- 1 root root  175 Apr 26 17:40 google-earth.list
-rw-r--r-- 1 root root  175 Apr 26 17:40 google-earth.list.save
-rw-r--r-- 1 root root  168 Apr 26 17:40 indicator-multiload-stable-daily-precise.list
-rw-r--r-- 1 root root  168 Apr 26 17:40 indicator-multiload-stable-daily-precise.list.save
-rw-r--r-- 1 root root  126 Apr 26 17:40 shutter-ppa-precise.list
-rw-r--r-- 1 root root  126 Apr 26 17:40 shutter-ppa-precise.list.save
-rw-r--r-- 1 root root  130 Apr 26 17:40 tualatrix-ppa-precise.list
-rw-r--r-- 1 root root  130 Apr 26 17:40 tualatrix-ppa-precise.list.save
-rw-r--r-- 1 root root  136 Apr 26 17:40 webupd8team-java-precise.list
-rw-r--r-- 1 root root  136 Apr 26 17:40 webupd8team-java-precise.list.save

caseone@ixcel-ubuntu:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/banshee-team-ppa-precise.list <==
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) precise main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

==> /etc/apt/sources.list.d/google-earth.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main

==> /etc/apt/sources.list.d/google-earth.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable main

==> /etc/apt/sources.list.d/indicator-multiload-stable-daily-precise.list <==
deb [http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu](http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu) precise main
deb-src [http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu](http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu) precise main

==> /etc/apt/sources.list.d/indicator-multiload-stable-daily-precise.list.save <==
deb [http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu](http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu) precise main
deb-src [http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu](http://ppa.launchpad.net/indicator-multiload/stable-daily/ubuntu) precise main

==> /etc/apt/sources.list.d/shutter-ppa-precise.list <==
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) precise main

==> /etc/apt/sources.list.d/shutter-ppa-precise.list.save <==
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) precise main

==> /etc/apt/sources.list.d/tualatrix-ppa-precise.list <==
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main

==> /etc/apt/sources.list.d/tualatrix-ppa-precise.list.save <==
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main

==> /etc/apt/sources.list.d/webupd8team-java-precise.list <==
deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main

==> /etc/apt/sources.list.d/webupd8team-java-precise.list.save <==
deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main

---

### Post by bapoumba on 2014-07-20
OK, that is quite a bit of ppa and third party repos..
```
apt-cache policy libnss3
apt-cache policy libnspr4
apt-cache policy zlib1g
apt-cache policy libnss3:i386
```

Edit : libnss3:i386 is a dependency of ca-certificates-java which in turn is a dependency of ca-certificates, openjdk-7-jre-headless and openjdk-6-jre-headless. I suspect your java install from webupd8team-java-precise.list.

---

### Post by bohmto on 2014-07-20
i think you must sudo apt-get purge openjdk-jre* files and the rest of jre files and then make a new sudo apt-get update : sudo apt-get install -f and sudo apt-get update and then use aptitude for installing java



//Tommy

---

### Post by casey9 on 2014-07-26
Thanks for the help guys but unfortunately I cannot remove any of the packages. I get the following errors when I run the apt-get purge openjdk-jre* command:

caseone@ixcel-ubuntu:~$ sudo apt-get purge openjdk-6-jre*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'openjdk-6-jre-lib' for regex 'openjdk-6-jre*'
Note, selecting 'openjdk-6-jre-headless' for regex 'openjdk-6-jre*'
Note, selecting 'openjdk-6-jre-zero' for regex 'openjdk-6-jre*'
Note, selecting 'openjdk-6-jre' for regex 'openjdk-6-jre*'
Package openjdk-6-jre-zero is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 icedtea-6-jre-cacao : Depends: openjdk-6-jre-headless (= 6b30-1.13.1-1ubuntu2~0.12.04.3)
 icedtea-6-jre-jamvm : Depends: openjdk-6-jre-headless (= 6b30-1.13.1-1ubuntu2~0.12.04.3)
 libnss3 : Breaks: libnss3:i386 (!= 3.15.4-0ubuntu0.12.04.2) but 3.15.3.1-0ubuntu0.12.04.1 is to be installed
 libnss3:i386 : Breaks: libnss3 (!= 3.15.3.1-0ubuntu0.12.04.1) but 3.15.4-0ubuntu0.12.04.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Also when I use the software center to remove it, i get a similiar error.

---

### Post by bapoumba on 2014-07-26
Can you please go to the Software Sources and untick the 2 last ppas (the ones for java) and then run :
```
sudo apt-get update
sudo apt-get upgrade
```
(Close the Software Sources window before running the commands).

---

### Post by casey9 on 2014-07-26
I unticked the two java ppa's and ran the commands.

[ATTACH=CONFIG]255049[/ATTACH]


caseone@ixcel-ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libnss3 : Breaks: libnss3:i386 (!= 3.15.4-0ubuntu0.12.04.2) but 3.15.3.1-0ubuntu0.12.04.1 is installed
 libnss3:i386 : Breaks: libnss3 (!= 3.15.3.1-0ubuntu0.12.04.1) but 3.15.4-0ubuntu0.12.04.2 is installed
E: Unmet dependencies. Try using -f.

Should I delete the libnss3 packages? Last time i did that i screwed things up... My apologies but i'm not sure what's going on with these packages?

---

### Post by bapoumba on 2014-07-26
> Should I delete the libnss3 packages? Last time i did that i screwed things up... My apologies but i'm not sure what's going on with these packages? 
Would you have a link ? I do not see anything on UF (at least not with your account). If not, what did happen ? And how did you get into the same situation again ?

Neither one directly depends on the other as far as I can tell. You can see for yourself :
```
apt-cache rdepends libnss3
apt-cache rdepends libnss3:i386
```
So I would remove both and install them again. This may not work as there may be a higher dependency level involved. For info, I have both installed.
```
sudo dpkg --remove --ignore-depends libnss3
sudo dpkg --remove --ignore-depends libnss3:i386
sudo apr-get install  libnss3  libnss3:i386
```

If this works, see if the package manager is happy again :
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mc4man on 2014-07-26
Probably the most useful thing you *didn't* post was - 
```
apt-cache policy libnss3:i386 libnss3
```
3.15.3.1-0ubuntu0.12.04.1 is fairly old & removed from disk some time ago ([2014-04-04.]("https://launchpad.net/ubuntu/precise/i386/libnss3")

---

### Post by casey9 on 2014-08-20
Thanks everyone for providing assistance on this issue. I was able to remove and re-install the packages using the following commands:

sudo dpkg --force-all -P libnss3
sudo dpkg --force-all -P libnss3:i386

---

### Post by bapoumba on 2014-08-22
Glad to see you fixed it :)
Please mark your thread as Solved (under Thread Tools), thanks.

---

### Post by guillermo7 on 2014-10-05
When you say:

> **bapoumba said:**
> 
```
sudo dpkg --remove --ignore-depends libnss3
sudo dpkg --remove --ignore-depends libnss3:i386
```


I guess you mean:

```
sudo dpkg --remove --force-depends libnss3
sudo dpkg --remove --force-depends libnss3:i386
```

I just had exactly this problem, and solved it with your help, but with that change.

---

### Post by bapoumba on 2014-10-05
@guillermo7 : --ignore-depends is a lighter approach. --force-depends is the next step when --ignore-depends does not work. Glad to see you got it to work :)

---

