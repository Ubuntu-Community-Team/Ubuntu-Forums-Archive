---
title: "Package manager/ update manager problems"
date: 2013-06-17
forum: General Help
---

### Post by ppalmer347 on 2013-06-17
I just upgraded to Ubuntu 12.04 LTS (from version 10 LTS).  I tried to install acrobat reader from Adobe's site, and messed everything up.

I have been running Ubuntu since Dec. 2007 on two Dell Optiplex 755's, one at home and one at work.  Both are now in the same state.  We had an IT guy who installed it for me originally, and I have been doing nothing more suble than upgrading every other release since, so please go easy on me.

The error message in the Red Warning icon was 'Error.  Broken count > 0' 
This usually means that your installed packages have unmet dependancies 

so I tried again with apt-get install -f
nothing changed

I tried the repair box in the window that popped up, but it apparently couldn't repair it.
I tried again with apt-get (I think) :

Do you want to continue [Y/n]? Y 
(Reading database ... 748538 files and directories currently installed.) 
Unpacking libtiff4:i386 (from .../libtiff4_3.9.5-2ubuntu1.5_i386.deb) ... 
dpkg: error processing  /var/cache/apt/archive/libtiff4_3.9.5-2ubuntu1.5_i386.de 
b (--unpack): 
 './usr/share/doc/libtiff4/TODO' is different from the same file on the  system 
No apport report written because MaxReports is reached already 
Errors were encountered while processing: 
 /var/cache/apt/archives/libtiff4_3.9.5-2ubuntu1.5_i386.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1) 

Then I tried to examine the file it seems to complain about (TODO): 

susi> ls -lt /usr/share/doc/libtiff4/ 
total 132 
drwxr-xr-x    2 root root   4096 Jun 16 10:07 ./ 
drwxr-xr-x 2926 root root 118784 Jun 11 18:04 ../ 
lrwxrwxrwx    1 root root     31 May 13 13:22 changelog.Debian.gz ->  ../libtiff4/changelog.Debian.gz 
lrwxrwxrwx    1 root root     18 May 13 13:22 README -> ../libtiff4/README 
lrwxrwxrwx    1 root root     16 May 13 13:22 TODO -> ../libtiff4/TODO 
-rw-r--r--    1 root root   1187 Aug 21  2009 README.Debian 
-rw-r--r--    1 root root   1914 Mar 20  2005 copyright 

when I try to look at TODO, more says too many levels of symbolic 
links.  The above directory listing looks circular to me. 

The system tells me I can neither add nor get rid of anything until th package manager is fixed.  How can I do this?

Sorry to be verbose, but I am really a beginner at dealing with this level of problem.

---

### Post by Cheesehead on 2013-06-18
I think we need *more* verbosity.

Please look at /var/log/apt/term.log. Each session it timestamped. Copy-and-paste one entire representative session here (in CODE tags)

Please look at /var/log/apt/term.log. Each session it timestamped. Copy-and-paste the same session here (in CODE tags)

Please look at /etc/apt/sources.list.  Copy-and-paste the entire contents here (in CODE tags)

---

### Post by ppalmer347 on 2013-06-18
(I am not certain what CODE tags are, so hope I figured it out below.)

Here are the log sections cheesehead asked for:
from /var/log/apt/term.log
[CODE] Log started: 2013-06-16  10:07:43
(Reading database ... 55%
(Reading database ... 748538 files and directories currently installed.)
Unpacking libtiff4:i386 (from .../libtiff4_3.9.5-2ubuntu1.5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libtiff4_3.9.5-2ubuntu1.5_i386.deb
 (--unpack):
 './usr/share/doc/libtiff4/TODO' is different from the same file on the system
Errors were encountered while processing:
 /var/cache/apt/archives/libtiff4_3.9.5-2ubuntu1.5_i386.deb
Log ended: 2013-06-16  10:07:46
[\CODE]

I don't understand the second request as it it is the same as the first request.  Maybe somethign got lost.

The third request is:
susi> more /etc/apt/sources.list
[CODE]
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted univer
se multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://us.archive.ubuntu.com/ubuntu/ precise-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ precise-security universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-proposed restricted main multive
rse universe
[\CODE]

---

