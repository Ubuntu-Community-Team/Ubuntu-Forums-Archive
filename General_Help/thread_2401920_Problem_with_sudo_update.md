---
title: "Problem with sudo update"
date: 2018-09-24
forum: General Help
---

### Post by rfigueira92 on 2018-09-24
Hi!, today i was soing the update, upgrade and dist,upgrade as usual and today and error apper in the terminal

W: El objetivo Sources (partner/source/Sources) está configurado varias veces en /etc/apt/sources.list:53 y /etc/apt/sources.list:54
W: El objetivo Sources (partner/source/Sources) está configurado varias veces en /etc/apt/sources.list:53 y /etc/apt/sources.list:54

i have a week using ubuntu and i do not know how to solve this problem, please help!

---

### Post by mainemojo on 2018-09-24
Looks like you've got a source listed more than once.  vim/nano/pico your /etc/apt/sources.list and see if a repository is in there more than once.  The repositories that count are the lines that do not begin with "#" (# comments the entire line if used as the first character of the line).  

You may want to edit from the terminal as you will need root access to modify the file.  From the terminal, you want to "sudo nano /etc/apt/sources.list" (I personally prefer VIM).

Could you post a copy of your file?

---

### Post by rfigueira92 on 2018-09-24
what file do you need? and also how i get that file (i'm a huge NOOB in ubuntu) i edit using that comand line and works
Thnaks a lot!

---

### Post by mainemojo on 2018-09-24
[LIST=1]
[*]Open up a terminal window (shortcut should be on your desktop).
[*]In the window that appears, type in "less /etc/apt/sources.list".
[*]Copy and paste (click and release left mouse button at the beginning of what you want to select, then drag your mouse to the end of the selection and right mouse click.  To paste, CTRL+V in the browser window).  Make sure you get all of your sources.list file.
[/LIST]

---

### Post by rfigueira92 on 2018-09-24
```
# deb cdrom:[Ubuntu 16.04.5 LTS _Xenial Xerus_ - Release i386 (20180731)]/ xeni
al main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) xenial main restricted
# deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
# deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
# deb-src [http://ve.archive.ubuntu.com/ubuntu/](http://ve.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) xenial partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) xenial partner
```

---

