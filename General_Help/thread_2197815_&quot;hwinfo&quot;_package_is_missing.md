---
title: "&quot;hwinfo&quot; package is missing"
date: 2014-01-05
forum: General Help
---

### Post by osmoma on 2014-01-05
Hello,
I want to install "hwinfo" utility on my Ubuntu 64bit Saucy. The system seems to know about the tool, but it does not exist in the package archive. 

```
$ **hwinfo**
The program 'hwinfo' is currently not installed. You can install it by typing: sudo apt-get install hwinfo.
```

$ **sudo apt-get update** 
$ **sudo apt-get install hwinfo**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package hwinfo is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'hwinfo' has no installation candidate
---------

Of course, my package list may have screwed up.

This system is:
$ **lsb_release -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

$ **uname -a**
Linux ubuntu64 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Linux has several similar tools, such as "lshw", Hardinfo, and I-nex.
------

"hwinfo" package was available in Ubuntu 13.04
[hwinfo]("http://packages.ubuntu.com/raring/hwinfo") (16.0-2.2) [**universe**]Hardware identification system
Ref: [http://packages.ubuntu.com/raring/allpackages](http://packages.ubuntu.com/raring/allpackages)

---

### Post by mc4man on 2014-01-05
Likely the result of efforts to totally remove hal 
(there is someone who is keeping hal alive, at least thru trusty
[https://launchpad.net/~mjblenner/+archive/ppa-hal/+packages](https://launchpad.net/~mjblenner/+archive/ppa-hal/+packages)

---

### Post by osmoma on 2014-01-05
Hello,
Ok, that explains why the package is missing. Hal is neither used nor work on Saucy.
Ref: [https://answers.launchpad.net/ubuntu/+source/hwinfo/+question/237733](https://answers.launchpad.net/ubuntu/+source/hwinfo/+question/237733)

Why does the APT say that it can be installed?
*[COLOR=#000000]"The program 'hwinfo' is currently not installed. You can install it by typing: sudo apt-get install hwinfo."[/COLOR]*

---

### Post by mc4man on 2014-01-05
> **osmoma said:**
> Hello,
Ok, that explains why the package is missing. Hal is neither used nor work on Saucy.
Ref: [https://answers.launchpad.net/ubuntu/+source/hwinfo/+question/237733](https://answers.launchpad.net/ubuntu/+source/hwinfo/+question/237733)

Why does the APT say that it can be installed?
*[COLOR=#000000]"The program 'hwinfo' is currently not installed. You can install it by typing: sudo apt-get install hwinfo."[/COLOR]*

Not sure - likely the info about the command "hwinfo" still exists with 'info' about what package supplies that command
(somewhere on one's install there is a 'db' or whatever that contains all currently used commands & I gather some info about packages that supply (or starts command-not-found, ect.

I remember locating once out of curiosity & related to creating custom commands (not wanting to take an existing one
Over all in that regard just decided that all custom commands I use or set up always end in a number as I believe when searching thru the 'db' didn't find any that ended in a number

---

### Post by philinux on 2014-01-05
Out of curiosity what does

apt-cache policy hwinfo

Report?

---

### Post by Bashing-om on 2014-01-05
Guys, on my system - upgraded from 13.04 :
```

sysop@1310mini:~$ apt-cache policy hwinfo
hwinfo:
  Installed: 16.0-2.2
  Candidate: 16.0-2.2
  Version table:
 *** 16.0-2.2 0
        100 /var/lib/dpkg/status
sysop@1310mini:~$ 

```

hwinfo continues to be functionable !

[INDENT][INDENT]my bit to add to our pool of knowledge
[/INDENT][/INDENT]

---

### Post by mc4man on 2014-01-05
> **Bashing-om said:**
> Guys, on my system - upgraded from 13.04 :
```

sysop@1310mini:~$ apt-cache policy hwinfo
hwinfo:
  Installed: 16.0-2.2
  Candidate: 16.0-2.2
  Version table:
 *** 16.0-2.2 0
        100 /var/lib/dpkg/status
sysop@1310mini:~$ 

```

hwinfo continues to be functionable !

[INDENT][INDENT]my bit to add to our pool of knowledge
[/INDENT][/INDENT]
My impression from the bug report on getting rid of hal is that while it was stated to no longer work it in fact does. (or at least in limited ways
The reason for the ppa is that some Amazon video service needs hal for authentication, that's why the ppa was set up

---

### Post by osmoma on 2014-01-05
On Ubuntu 13.10 Saucy:
```
$ apt-cache policy hwinfo
     hwinfo:
     Installed: (none)
     Candidate: (none)
     Version table:
```

About the "command-not-found" cache on the bash-prompt: 
Please see: [https://apps.ubuntu.com/cat/applications/saucy/command-not-found/](https://apps.ubuntu.com/cat/applications/saucy/command-not-found/)
And: [https://launchpad.net/command-not-found](https://launchpad.net/command-not-found)

The command cache (db) is maintained here.
[http://bignay.canonical.com/~mvo/command-not-found/](http://bignay.canonical.com/~mvo/command-not-found/)
Seems like the db is same for Ubuntu 13.04, 13.10 and 14.04.

---

### Post by pqwoerituytrueiwoq on 2014-01-05
[http://www.ubuntuupdates.org/package/core/raring/universe/base/hwinfo](http://www.ubuntuupdates.org/package/core/raring/universe/base/hwinfo)
you can download the deb from there, it does run on 13.10

---

### Post by philinux on 2014-01-05
@osmoma lets have a look at your sources.

cat /etc/apt/sources.list

---

### Post by osmoma on 2014-01-07
Sorry for my delayed reply.
 
$ cat /etc/apt/sources.list
```
[SIZE=2]# deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy-updates main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy universe
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy-updates universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy multiverse
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy-updates multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy-backports main restricted universe multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) saucy-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) saucy main
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) saucy-proposed universe main multiverse restricted[/SIZE]
```

---

### Post by mc4man on 2014-01-07
There is no hwinfo package in saucy, nor will there be in trusty so sources list is a moot point. 
If anyone had it installed in < saucy & upgraded then they would have as the upgrade process would have no reason to remove

---

### Post by osmoma on 2014-01-08
[COLOR=#000000]This is is not a big deal, but 
what is the reason for mis-information about "hwinfo" in Ubuntu 13.10 and 14.04? [/COLOR]
```
$ hwinfo
The program 'hwinfo' is currently not installed. You can install it by typing: sudo apt-get install hwinfo.
```

This message is shown because:
o...Maybe hwinfo is required by Hal and Hal is still used on some systems?
o...Or maybe there is an error in the command-not-found database?  ---> Send a bug report.

---

