---
title: "tzdata update for dapper"
date: 2007-03-07
forum: General Help
---

### Post by LORDs_diakonos on 2007-03-07
I need to update tzdata so the latest DST will take.  The server is running 6.06 Dapper Drake.  How do I get it.  When I do an apt-get instal tzdata it says it is not installed.  I also did a apt-cache search tzdata and found nothing.  This is my sources

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by markitect on 2007-03-07
The update should be done automatically with an apt-get update apt-get upgrade

if you want to check though pop open a terminal and :
```

zdump -v EST5EDT|grep 2007

EST5EDT  Sun Mar 11 06:59:59 2007 UTC = Sun Mar 11 01:59:59 2007 EST isdst=0 gmtoff=-18000
EST5EDT  Sun Mar 11 07:00:00 2007 UTC = Sun Mar 11 03:00:00 2007 EDT isdst=1 gmtoff=-14400
EST5EDT  Sun Nov  4 05:59:59 2007 UTC = Sun Nov  4 01:59:59 2007 EDT isdst=1 gmtoff=-14400
EST5EDT  Sun Nov  4 06:00:00 2007 UTC = Sun Nov  4 01:00:00 2007 EST isdst=0 gmtoff=-18000

```
with the first line being the command and the rest the result, make sure it has March 11th as the new date to change and substitute your timezone in for EST5EDT

---

### Post by Bad Penguin on 2007-03-08
> **markitect said:**
> The update should be done automatically with an apt-get update apt-get upgrade

if you want to check though pop open a terminal and :
```

zdump -v EST5EDT|grep 2007


Doing the zdump above only tells you that you have the updated timezone data files ;)

To be absolutely sure everything is going to work, cut and paste this shell script and run it.  Of course, if you are in EDT it should say EST/EDT not CST/CDT, just pay attention to the DT/ST.

[code]
#!/bin/sh
echo "This should say CST: " `date -d "2007-03-11 01:59:00"`
echo "This should say CDT: " `date -d "2007-03-11 03:00:00"`
echo "This should say CDT: " `date -d "2007-11-04 01:59:00"`
echo "This should say CST: " `date -d "2007-11-04 02:01:00"`

```

---

### Post by fragos on 2007-03-08
Auto updates for Edgy have already happened.  I did notice a new tzdata data in the upgrade list as well.  Should be soon for Dapper if it didn't happen already.

---

