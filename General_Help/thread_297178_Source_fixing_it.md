---
title: "Source fixing it"
date: 2006-11-10
forum: General Help
---

### Post by Tobster on 2006-11-10
I tried to install Burryl a number of time but failed I know my source list is messed up so how do I fix it?

This is what I got so far:


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy main-edgy-amd64




#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edg

Thanks 

Toby

---

### Post by taurus on 2006-11-10
Don't you have backup copy in /etc/apt/sources.list!!!

```
ls -la /etc/apt
```

---

### Post by Tobster on 2006-11-10
You mean this: 

toby@toby-desktop:~$ ls -la /etc/apt
total 84
drwxr-xr-x   4 root root 4096 2006-11-06 22:13 .
drwxr-xr-x 127 root root 8192 2006-11-10 22:12 ..
-rw-r--r--   1 root root   30 2006-10-31 19:07 apt.conf
drwxr-xr-x   2 root root 4096 2006-10-31 21:11 apt.conf.d
-rw-------   1 root root    0 2006-05-31 01:51 secring.gpg
-rw-r--r--   1 root root 3004 2006-11-06 22:13 sources.list
-rw-r--r--   1 root root 2953 2006-11-04 21:05 sources.list~
-rw-r--r--   1 root root 1821 2006-10-31 22:19 sources.list_backup_200610311719
-rw-r--r--   1 root root 2883 2006-11-03 01:08 sources.list_backup_200611030108
-rw-r--r--   1 root root 2953 2006-11-04 21:12 sources.list_backup_200611042112
-rw-r--r--   1 root root 2953 2006-11-04 21:15 sources.list_backup_200611042115
-rw-r--r--   1 root root 2883 2006-11-09 23:05 sources.list_backup_200611092305
-rw-r--r--   1 root root 2883 2006-11-10 02:10 sources.list_backup_200611100210
-rw-r--r--   1 root root 2883 2006-11-10 16:17 sources.list_backup_200611101617
drwxr-xr-x   2 root root 4096 2006-04-18 20:47 sources.list.d
-rw-r--r--   1 root root 1784 2006-10-31 19:39 sources.list.distUpgrade
-rw-r--r--   1 root root 2106 2006-11-09 19:05 sources.list.save
-rw-------   1 root root 1200 2006-05-31 01:51 trustdb.gpg
-rw-r--r--   1 root root 4766 2006-11-04 20:45 trusted.gpg
-rw-r--r--   1 root root 3595 2006-10-31 22:11 trusted.gpg~
toby@toby-desktop:~$

---

### Post by taurus on 2006-11-10
> **Tobster said:**
> You mean this: 

toby@toby-desktop:~$ ls -la /etc/apt
total 84
drwxr-xr-x   4 root root 4096 2006-11-06 22:13 .
drwxr-xr-x 127 root root 8192 2006-11-10 22:12 ..
-rw-r--r--   1 root root   30 2006-10-31 19:07 apt.conf
drwxr-xr-x   2 root root 4096 2006-10-31 21:11 apt.conf.d
-rw-------   1 root root    0 2006-05-31 01:51 secring.gpg
-rw-r--r--   1 root root 3004 2006-11-06 22:13 sources.list
-rw-r--r--   1 root root 2953 2006-11-04 21:05 sources.list~
-rw-r--r--   1 root root 1821 2006-10-31 22:19 sources.list_backup_200610311719
-rw-r--r--   1 root root 2883 2006-11-03 01:08 sources.list_backup_200611030108
-rw-r--r--   1 root root 2953 2006-11-04 21:12 sources.list_backup_200611042112
-rw-r--r--   1 root root 2953 2006-11-04 21:15 sources.list_backup_200611042115
-rw-r--r--   1 root root 2883 2006-11-09 23:05 sources.list_backup_200611092305
-rw-r--r--   1 root root 2883 2006-11-10 02:10 sources.list_backup_200611100210
-rw-r--r--   1 root root 2883 2006-11-10 16:17 sources.list_backup_200611101617
drwxr-xr-x   2 root root 4096 2006-04-18 20:47 sources.list.d
-rw-r--r--   1 root root 1784 2006-10-31 19:39 sources.list.distUpgrade
-rw-r--r--   1 root root 2106 2006-11-09 19:05 sources.list.save
-rw-------   1 root root 1200 2006-05-31 01:51 trustdb.gpg
-rw-r--r--   1 root root 4766 2006-11-04 20:45 trusted.gpg
-rw-r--r--   1 root root 3595 2006-10-31 22:11 trusted.gpg~
toby@toby-desktop:~$
If you remember when you started messing around with Beryl, then use the sources.list with the time/date before that.

---

### Post by Tobster on 2006-11-10
Better then that I just remember I copy and paste it onto Open Office :)

So I'd just copy and paste it back

I guess that would work right?

Toby

---

### Post by taurus on 2006-11-10
Yes, open the current version and remove everything.  Then, paste whatever you want back to it and save the change.  Otherwise, you can also copy the old list to the current list with the "sudo cp" command from a terminal...

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Tobster on 2006-11-10
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security univers

---

### Post by Tobster on 2006-11-10
Thanks,

As you can see I think we fixed it...

Ubuntu is such a good GUI the staff must be angels :) (kidding) 

Toby

---

### Post by taurus on 2006-11-10
> **Tobster said:**
> Thanks,

As you can see I think we fixed it...

Yip.  You got the original /etc/apt/sources.list back.  Now, you can remove the # sign in front of the universe & multiverse so you can install more goodies.

> Ubuntu is such a good GUI the staff must be angels :) (kidding) 

Toby

If not, then they're real close...

---

### Post by Tobster on 2006-11-10
Like this :)

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security univers

---

### Post by taurus on 2006-11-10
Or like this.

```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security univers

```

---

### Post by arnieboy on 2006-11-10
The sources.list that the OP had posted was fine (except for the beryl repo). If one noticed carefully, he would have seen that Automatix had "**completed**" the user's incomplete sources.list by adding all the official repos which were missing in the OP's original sources.list.
The beryl repo that the user added manually was wrong. Instead of 
> deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edg
it should have been
> deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy

---

