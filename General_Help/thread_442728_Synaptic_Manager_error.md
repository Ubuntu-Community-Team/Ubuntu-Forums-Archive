---
title: "Synaptic Manager error"
date: 2007-05-13
forum: General Help
---

### Post by sondratheloser on 2007-05-13
When I try to go into my synaptic manager, I get this error:

E: Malformed line 44 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read
Go to the repository dialog to correct the problem
E:_cache>open failed, please report
 
also when I type apt-get update in the terminal, I get a similar error (pretty much just the first line of this error)

I just installed today, and things were going ok for a while.  I installed the restricted stuff, edited my xorg.conf since I'm on a laptop, and my 1440x900 wasn't showing up in the screen resolution list.

I think it has something to do with beryl, because I was messing around with that, and things started to get kind of weird and I had to reboot.

I'm pretty much a complete n00b, so I'm not sure what things mean yet...

Thanks, Sondra

---

### Post by Nythain on 2007-05-13
in terminal type
cat /etc/apt/sources.list
and let us see what it looks like

---

### Post by sondratheloser on 2007-05-13
Here it is:

```
pandora@pandora-laptop:~$ cat /etc/apt/sources.list
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
deb bzr branch http://glatzor.de/bzr/displayconfig-gtk/sebi feisty main
pandora@pandora-laptop:~$ 

```

I'm kinda thinkin' I should erase that last line..  I was trying to install that GUI xorg.conf editor.. and it wasn't working, so I finally figured out how to edit it normally and got my screen res. fixed....

also what does "cat" stand for/do?

---

### Post by Nythain on 2007-05-13
ok, your problem lies in the very last entry... i dont know what you put that repo in there for, but it isnt normal... remove it and sudo apt-get update in terminal should fix things

as for cat... not sure what it stands for exactly, but its used for outputting the contents of a file in terminal

---

### Post by sondratheloser on 2007-05-13
Thank you, it worked... :D

Like I said, I am a complete n00b, so that is why that repository entry was in there and was all screwed up and weird.

*toddles off to try and make photoshop work*

---

