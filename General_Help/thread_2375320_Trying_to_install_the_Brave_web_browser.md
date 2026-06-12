---
title: "Trying to install the Brave web browser"
date: 2017-10-23
forum: General Help
---

### Post by nachrimata on 2017-10-23
Hi all. I'm pretty new to Ubuntu and I'm having trouble trying to download the Brave web browser through the terminal. 

```
~$ sudo apt install brave
[sudo] password for astrohalcyon: 
E: Type 'dep' is not known on line 1 in source list /etc/apt/sources.list.d/brave-xenial.list
E: The list of sources could not be read.
E: Type 'dep' is not known on line 1 in source list /etc/apt/sources.list.d/brave-xenial.list
E: The list of sources could not be read.

```

I think I did something wrong... I just followed the instructions on this [website]("https://www.addictivetips.com/ubuntu-linux-tips/install-brave-browser-on-linux/").

Sorry if I seem ignorant of something.

EDIT: Sorry, wrong website.

---

### Post by jeremy31 on 2017-10-23
The link you posted shows nothing about the Brave web browser, just atom text editor.  Post results for ```
cat /etc/apt/sources.list.d/brave-xenial.list
```

---

### Post by nachrimata on 2017-10-23
Oh, sorry about that. I know I was trying to download Atom too at the same time and I got mixed up between the two. 

This is what popped up:
```
~$ cat /etc/apt/sources.list.d/brave-xenial.list
dep [arch=amd64] https://s3-us-west-2.amazonaws.com/brave-apt xenial main
deb [arch=amd64] https://s3-us-west-2.amazonaws.com/brave-apt xenial main

```

---

### Post by oldos2er on 2017-10-23
There's a typo in the first line, "dep" should be "deb."

---

### Post by nachrimata on 2017-10-23
Sorry, is it this?
```

# deb cdrom:[Ubuntu 16.04.3 LTS _Xenial Xerus_ - Release amd64 (20170801)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
```

---

### Post by nachrimata on 2017-10-23
I wanna know how to fix it though...

---

### Post by deadflowr on 2017-10-24
Try
```
sudo sed -i 's/dep/#dep/g' /etc/apt/sources.list.d/brave-xenial.list
```
that should disable that entry.
You have the correct entry already, and only need the one.

The correct entry is the
```
deb [arch=amd64] https://s3-us-west-2.amazonaws.com/brave-apt xenial main
```
ftr

---

### Post by nachrimata on 2017-10-24
Thanks!

---

### Post by vasa1 on 2017-10-25
[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

