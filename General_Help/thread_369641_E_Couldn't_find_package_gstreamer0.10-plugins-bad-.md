---
title: "E: Couldn't find package gstreamer0.10-plugins-bad-multiverse"
date: 2007-02-24
forum: General Help
---

### Post by FuturePilot on 2007-02-24
I was trying to install the restricted formats following [this]("https://help.ubuntu.com/community/RestrictedFormats") guide and I keep getting this error
```
E: Couldn't find package gstreamer0.10-plugins-bad-multiverse

```
Is there a temporary problem with the repos?

---

### Post by CocoAUS on 2007-02-24
Does doing 'sudo aptitude update' fix anything?  If you can do that without errors, then it should work just fine.  Make sure your repositories are enabled, make sure you've done either 'apt-get update' or 'aptitude update' after enabling your repositories, and make sure you downloaded any keys you need.

If you can't get the repos to work, I suggest replacing your repositories with the ones found on the following site, and then using the install command for restricted codecs on the same site:

[http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#replacerepositories]("http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#replacerepositories")

---

### Post by FuturePilot on 2007-02-24
Sudo apt-get update didn't do anything. It worked but no errors or anything. I'm not really sure if I like to idea of replacing my whole sources list.

---

### Post by FuturePilot on 2007-02-24
Can anyone confirm that it's the repos?

---

### Post by FuturePilot on 2007-02-25
There's something wrong with one of the repos. I tried this on a different computer and it did the same thing.

---

### Post by yabbadabbadont on 2007-02-25
Please post the contents of your /etc/apt/sources.list file.

---

### Post by FuturePilot on 2007-02-25
```

deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
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

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe main restricted
```
I added this one```
deb http://nl.archive.ubuntu.com/ubuntu/ dapper multiverse
```
and installed some codecs with
```
sudo apt-get install gstreamer0.10-plugins-ugly libxine-extracodecs
```
But it didn't work before I added that.

---

### Post by smokey edgy on 2007-03-24
Pilot:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Automatix appears to do the trick. Takes care of updating your sources.list with the appropriate repos and such

smokey edgy

---

