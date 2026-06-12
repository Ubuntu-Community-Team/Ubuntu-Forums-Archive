---
title: "package autoconf"
date: 2007-05-10
forum: General Help
---

### Post by hadeel on 2007-05-10
i try to install ns2.31 on ubuntu 7.04. when i write this command " sudo apt-get install build-essential autoconf automake libxmu-dev " i got this error
" E: package autoconf has no installation candidate "
plz help me

---

### Post by jimbob on 2007-05-10
I just tried to install autoconf and it found it straight away with no problem.

Check to see if you have the archive main library in your /etc/apt/menu.lst.

apt-cache policy autoconf should look like this:

 apt-cache policy autoconf
autoconf:
  Installed: 2.61-3
  Candidate: 2.61-3
  Version table:
 *** 2.61-3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
        100 /var/lib/dpkg/status

________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by hadeel on 2007-05-10
i try to find menu.list but i don't find it 
and when try apt-cache policy autoconf i have this 
autoconf:
Installed: (none)
Candidate: (none)
Version table:

can you help me ?

---

### Post by jimbob on 2007-05-11
Sorry, it should be /etc/apt/sources.list  (not menu.lst).

Here is a copy of mine before I ran Automatix.  Make sure you have all the entries that are uncommented, then run apt-get update followed by apt-get upgrade and then repeat your apt-cache policy to see if it has appeared.

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse


```

---

### Post by hadeel on 2007-05-12
thnx for ur replay :D
my /etc/apt/sources.list look like yours but i have an extra uncommented line 
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

and all line have "eg" yours are "us"  like deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) feisty main restricted
i think because of the location 

but also it still not work and i dont know what to do??????

---

### Post by jimbob on 2007-05-12
The eg. and us. notations point to different server mirrors - ie us. refers to the United States, etc.

You could comment out the line referring to the cdrom if you want to.  I usually do so it doesn't keep bothering me about mounting it each time I update.

When you run synaptic does it show autoconf as being there and not installed or is it not there at all?

Why don't you go through and remove all eg. stuff on all of the lines which will point it to the main Ubuntu servers wherever they are and then run apt-get update and apt-get upgrade again to see if you can pick up autoconf. 

If that fails consider running automatix and selecting everything you think would be related to script building, development, etc.

Other than that I don't know what to tell you.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

