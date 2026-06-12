---
title: "Where's glipper in synaptic?"
date: 2007-04-03
forum: General Help
---

### Post by JoeCool1986 on 2007-04-03
Doesn't show up in synaptic, and when I use apt-get install glipper I get "E: Couldn't find package glipper".

Here are my sources in case you want to check:

```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse universe
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://ubuntu.beryl-project.org edgy main
deb-src http://ubuntu.beryl-project.org edgy main
```

---

### Post by Maestro23 on 2007-04-03
I believe it's in "universe". Try enabling your universe sources.

---

### Post by louieb on 2007-04-03
Ubuntu repositories don't have it or didn't, may have now. but anyway you can get it here  .  [http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglipper%2Fglipper_0.95.1-1_i386.deb&md5sum=8731568a7318f43cc3e150782e63343a&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglipper%2Fglipper_0.95.1-1_i386.deb&md5sum=8731568a7318f43cc3e150782e63343a&arch=i386&type=main)
This is for the .95  version. I am running Ubuntu Dapper and I had dependency problems installing it, so I use the .86 version. Works for me with no problems.

---

### Post by Maestro23 on 2007-04-03
I'm running Feisty and its in there.  Sorry, don't know about Dapper.

---

