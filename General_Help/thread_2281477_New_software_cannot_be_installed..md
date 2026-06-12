---
title: "New software cannot be installed."
date: 2015-06-07
forum: General Help
---

### Post by leonic455 on 2015-06-07
Hi,
I installed Ubuntu a few days ago and I tried installing Codeblocks, via the .deb on their website. I tried installing the deb files through Terminal and it seemed to be having trouble install it. It showed up on my program list, but when I tried opening it doesn't do anything. The next thing I did was try to remove it via Terminal, but it printed this:

```

leonic@LeonicUbuntuPad:~$ sudo apt-get remove codeblocks
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 codeblocks-contrib : Depends: libwxsmithlib0 (= 13.12-1) but 13.12-3 is to be installed
                      Depends: codeblocks (= 13.12-1) but it is not going to be installed
                      Recommends: valgrind but it is not going to be installed
                      Recommends: cppcheck but it is not going to be installed
                      Recommends: cscope but it is not going to be installed
                      Recommends: cccc but it is not going to be installed
 codeblocks-dbg : Depends: codeblocks (= 13.12-3) but it is not going to be installed
                  Depends: codeblocks-contrib (= 13.12-3) but 13.12-1 is to be installed
 libwxsmithlib0 : Depends: libcodeblocks0 (= 13.12-3) but 13.12-1 is to be installed
                  Recommends: codeblocks-contrib (= 13.12-3) but 13.12-1 is to be installed
 libwxsmithlib0-dev : Depends: libwxsmithlib-dev (= 13.12-3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

As it said try running, apt-get -f install. But when I do that, it prints this:
```

leonic@LeonicUbuntuPad:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  account-plugin-windows-live libappindicator1 libindicator7 libkeybinder0
  libupstart1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  codeblocks codeblocks-contrib codeblocks-dev libcodeblocks0
  libwxsmithlib-dev
Suggested packages:
  libwxgtk2.8-dev wx-common
Recommended packages:
  valgrind
The following packages will be REMOVED
  codeblocks-headers
The following NEW packages will be installed
  libwxsmithlib-dev
The following packages will be upgraded:
  codeblocks codeblocks-contrib codeblocks-dev libcodeblocks0
4 to upgrade, 1 to newly install, 1 to remove and 10 not to upgrade.
6 not fully installed or removed.
Need to get 6,617 kB of archives.
After this operation, 119 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe codeblocks-dev amd64 13.12-3 [350 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe codeblocks-contrib amd64 13.12-3 [3,018 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe codeblocks amd64 13.12-3 [1,366 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe libcodeblocks0 amd64 13.12-3 [1,807 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe libwxsmithlib-dev amd64 13.12-3 [75.1 kB]
Fetched 6,617 kB in 1s (4,498 kB/s)         
(Reading database ... 206728 files and directories currently installed.)
Preparing to unpack .../codeblocks-dev_13.12-3_amd64.deb ...
Unpacking codeblocks-dev (13.12-3) over (13.12-1) ...
dpkg: error processing archive /var/cache/apt/archives/codeblocks-dev_13.12-3_amd64.deb (--unpack):
 trying to overwrite '/usr/include/codeblocks/externaldepsdlg.h', which is also in package codeblocks-headers 13.12-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/codeblocks-dev_13.12-3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Next I tried to remove it via the software store, but when I opened it this showed up.
[IMG]https://dl.dropboxusercontent.com/s/b9imfiepxx3ty0s/error.png[/IMG]

I clicked repair and it came up with a dialog saying it failed and it had a log:
```

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 206728 files and directories currently installed.) 
Preparing to unpack .../codeblocks-dev_13.12-3_amd64.deb ... 
Unpacking codeblocks-dev (13.12-3) over (13.12-1) ... 
dpkg: error processing archive /var/cache/apt/archives/codeblocks-dev_13.12-3_amd64.deb (--unpack): 
 trying to overwrite '/usr/include/codeblocks/externaldepsdlg.h', which is also in package codeblocks-headers 13.12-1 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/codeblocks-dev_13.12-3_amd64.deb 
Error in function:  
dpkg: dependency problems prevent configuration of codeblocks: 
 codeblocks depends on codeblocks-common (= 13.12-1); however: 
  Version of codeblocks-common on system is 13.12-3. 
 
dpkg: error processing package codeblocks (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of codeblocks-contrib: 
 codeblocks-contrib depends on libwxsmithlib0 (= 13.12-1); however: 
  Version of libwxsmithlib0 on system is 13.12-3. 
 codeblocks-contrib depends on codeblocks (= 13.12-1); however: 
  Package codeblocks is not configured yet. 
 
dpkg: error processing package codeblocks-contrib (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libwxsmithlib0-dev: 
 libwxsmithlib0-dev depends on libwxsmithlib-dev (= 13.12-3); however: 
  Package libwxsmithlib-dev is not installed. 
 
dpkg: error processing package libwxsmithlib0-dev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of codeblocks-dbg: 
 codeblocks-dbg depends on codeblocks (= 13.12-3); however: 
  Version of codeblocks on system is 13.12-1. 
 codeblocks-dbg depends on codeblocks-contrib (= 13.12-3); however: 
  Version of codeblocks-contrib on system is 13.12-1. 
 
dpkg: error processing package codeblocks-dbg (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libwxsmithlib0: 
 libwxsmithlib0 depends on libcodeblocks0 (= 13.12-3); however: 
  Version of libcodeblocks0 on system is 13.12-1. 
 
dpkg: error processing package libwxsmithlib0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of codeblocks-contrib-dbg: 


```

Next I tried apt-get clean and nothing was printed, so I assumed it worked.
Then I tried apt-get autoremove and it said this:

```

leonic@LeonicUbuntuPad:~$ sudo apt-get remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 codeblocks : Depends: codeblocks-common (= 13.12-1) but 13.12-3 is installed
 codeblocks-contrib : Depends: libwxsmithlib0 (= 13.12-1) but 13.12-3 is installed
                      Recommends: valgrind but it is not installed
                      Recommends: cppcheck but it is not installed
                      Recommends: cscope but it is not installed
                      Recommends: cccc but it is not installed
 codeblocks-dbg : Depends: codeblocks (= 13.12-3) but 13.12-1 is installed
                  Depends: codeblocks-contrib (= 13.12-3) but 13.12-1 is installed
 libwxsmithlib0 : Depends: libcodeblocks0 (= 13.12-3) but 13.12-1 is installed
                  Recommends: codeblocks-contrib (= 13.12-3) but 13.12-1 is installed
 libwxsmithlib0-dev : Depends: libwxsmithlib-dev (= 13.12-3) but it is not installed
E: Unmet dependencies. Try using -f.

```

And now I have no idea. I have looked on the internet and it says pretty much the same thing and I am stumped.
Thanks in advanced.
**EDIT: **I'm using Ubuntu 14.04 LTS

---

### Post by speartip on 2015-06-07
May sound a silly question, but why didn't you just install codeblocks from the official repos?
Installing from external sources can often cause dependency problems.

---

### Post by leonic455 on 2015-06-07
Really? Well I guess I messed up with that. :/
But do you have and any idea how to fix it, because I can't install anything now.

---

### Post by mc4man on 2015-06-07
Maybe get a sense of how many of those .debs got installed originally 
```
apt-cache policy codeblocks* libwxsmithlib0 wxsmith*
```

---

### Post by leonic455 on 2015-06-07
Well I did it and it looks like it installed most of the libraries.
```

leonic@LeonicUbuntuPad:/media$ apt-cache policy codeblocks* libwxsmithlib0 wxsmith*
codeblocks-contrib-dbg:
  Installed: 13.12-3
  Candidate: 13.12-3
  Version table:
 *** 13.12-3 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
codeblocks-libwxcontrib0:
  Installed: 13.12-1
  Candidate: 13.12-1
  Version table:
 *** 13.12-1 0
        100 /var/lib/dpkg/status
codeblocks-dbg:
  Installed: 13.12-3
  Candidate: 13.12-3
  Version table:
 *** 13.12-3 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
codeblocks-dev:
  Installed: 13.12-1
  Candidate: 13.12-3
  Version table:
     13.12-3 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
 *** 13.12-1 0
        100 /var/lib/dpkg/status
codeblocks:
  Installed: 13.12-1
  Candidate: 13.12-3
  Version table:
     13.12-3 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
 *** 13.12-1 0
        100 /var/lib/dpkg/status
codeblocks-headers:
  Installed: 13.12-1
  Candidate: 13.12-1
  Version table:
 *** 13.12-1 0
        100 /var/lib/dpkg/status
libcodeblocks0:
  Installed: 13.12-1
  Candidate: 13.12-3
  Version table:
     13.12-3 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
 *** 13.12-1 0
        100 /var/lib/dpkg/status
codeblocks-contrib:
  Installed: 13.12-1
  Candidate: 13.12-3
  Version table:
     13.12-3 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
 *** 13.12-1 0
        100 /var/lib/dpkg/status
codeblocks-contrib-common:
  Installed: 13.12-1
  Candidate: 13.12-1
  Version table:
 *** 13.12-1 0
        100 /var/lib/dpkg/status
codeblocks-wxcontrib-headers:
  Installed: 13.12-1
  Candidate: 13.12-1
  Version table:
 *** 13.12-1 0
        100 /var/lib/dpkg/status
codeblocks-wxcontrib-dev:
  Installed: 13.12-1
  Candidate: 13.12-1
  Version table:
 *** 13.12-1 0
        100 /var/lib/dpkg/status
codeblocks-common:
  Installed: 13.12-3
  Candidate: 13.12-3
  Version table:
 *** 13.12-3 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
libwxsmithlib0:
  Installed: 13.12-3
  Candidate: 13.12-3
  Version table:
 *** 13.12-3 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
libwxsmithlib0:
  Installed: 13.12-3
  Candidate: 13.12-3
  Version table:
 *** 13.12-3 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
libwxsmithlib0-dev:
  Installed: 13.12-3
  Candidate: 13.12-3
  Version table:
 *** 13.12-3 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
libwxsmithlib-dev:
  Installed: (none)
  Candidate: 13.12-3
  Version table:
     13.12-3 0
        500 http://gb.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages


```

---

### Post by mc4man on 2015-06-07
Try this, copy & paste this **1** complete command into a terminal
```
sudo apt-get purge codeblocks-contrib-dbg codeblocks-libwxcontrib0 codeblocks-dbg \
codeblocks-dev codeblocks codeblocks-headers libcodeblocks0  codeblocks-contrib \
codeblocks-contrib-common codeblocks-wxcontrib-headers codeblocks-wxcontrib-dev \
codeblocks-common libwxsmithlib0 libwxsmithlib0 libwxsmithlib0-dev
```

---

### Post by leonic455 on 2015-06-07
Thanks, that fixed it! Thanks for the help!

---

### Post by slovos on 2015-10-29
I had the same exact problem and this post saved me... thanks!!

---

