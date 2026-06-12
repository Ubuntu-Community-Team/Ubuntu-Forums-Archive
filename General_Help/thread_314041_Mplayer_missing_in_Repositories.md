---
title: "Mplayer missing in Repositories"
date: 2006-12-06
forum: General Help
---

### Post by odin277 on 2006-12-06
Using Dapper - Kubuntu but can't find mplayer in adept or synaptic. It is in Add/Remove but it is grayed out. All repositories un-commented  in /etc/apt/sources.list.   Also can't locate sun java JRE 1.5 - sources list as follows: 
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper non-free 
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper non-free 
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free 
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free 
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted 
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted 
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe 
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 

Just added the PLF sites. Did I miss something????

---

### Post by odin277 on 2006-12-07
Should also mention I tried sudo apt-get update, apt-get upgrade, apt-get install -f also tried same with aptitude just in case. Nothing to update/change

---

### Post by drphilngood on 2006-12-07
> **odin277 said:**
> Should also mention I tried sudo apt-get update, apt-get upgrade, apt-get install -f also tried same with aptitude just in case. Nothing to update/change

Did you select ¨all available applications¨ in the top right hand corner where it says, ¨Show¨?  It is showing in my Add/Remove.

---

### Post by RAOF on 2006-12-07
You don't have **multiverse** in there anywhere.  MPlayer is full of code that implements patented techniques, so that's where it ends up.

Basically, you want to add **multiverse** to the end of each of these lines:
```
deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

```
like this:
```
deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe multiverse

```

---

### Post by odin277 on 2006-12-07
drphilngood - thanks for the reply - yes I had it checked off and still wasn't showing.
RAOF - That did the trick. Thanks for the help, hopefully I'll be able to stumble along for a little while now.

---

