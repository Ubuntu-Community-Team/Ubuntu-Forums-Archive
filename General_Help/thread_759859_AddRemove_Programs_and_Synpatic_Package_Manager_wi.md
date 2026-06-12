---
title: "Add/Remove Programs and Synpatic Package Manager will not work."
date: 2008-04-19
forum: General Help
---

### Post by enazguy on 2008-04-19
Synpatic and Add/Remove suddenly stopped working. Add/Remove says it cannot retrieve the list of programs. What do I do?

---

### Post by enazguy on 2008-04-19
this is the error message i get when trying to open the package manager

E: Type '&#8220;deb' is not known on line 78 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

please help

---

### Post by bodhi.zazen on 2008-04-19
post the output of 

```
cat -n /etc/apt/sources.list | grep 78
```

---

### Post by enazguy on 2008-04-19
78  “deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main”

the result

---

### Post by diablo75 on 2008-04-19
Assuming you're using version 7.10, this line needs to be removed.

Do this:

```
sudo gedit /etc/apt/sources.list
```

And find the line that was output from that grep statement in the previous post, delete the line, save the file, then try again.

You could also open up your System>Admin>Software Sources and find the line that says "feisty" in it, and remove it.

---

### Post by bodhi.zazen on 2008-04-19
I think the problem is the quotes

Change 
> “deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main”

to

```
deb http://packages.dfreer.org feisty main
```

NO QUOTES

---

### Post by enazguy on 2008-04-19
What do you mean by take out the line from the last thing?

---

### Post by bodhi.zazen on 2008-04-19
We are both referring to the line 

> **[color=red]“[/color]**deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main**[color=red]”[/color]**

in /etc/apt/sources.list

You can edit the file with

```
gksu gedit /etc/apt/surces.list
```

The problem, I think, is that you have quotes around it. Remove the quotes. The line should read :

```
deb http://packages.dfreer.org feisty main
```

You can just delete the line, or comment it out with a #

```
**[color=blue]#[/color]** “deb http://packages.dfreer.org feisty main”
```

---

### Post by enazguy on 2008-04-19
i deleted the line and the package manager still will not open and i get the same error message

---

### Post by bodhi.zazen on 2008-04-19
were you adding repos ?

Either look at the file /etc/apt/sources for syntax errors or if you can not spot any, post the contents for us to look at.

---

### Post by game_plan on 2008-04-25
I have the same issue but heven't changed the repo list file. I've been using the beta of hardy for a while(3 weeks about), and everything was fine until I added the commands to /etc/rc.local to start m wireless, now package manager wont open and update manager says it cant access some of the repos?

---

### Post by nyscreenwriter on 2008-04-25
I'm having the same problem.  Here is my source list, if any of you can tell me what's wrong.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse



Not only can I not use  add remove, synaptic, or upgrade manager, I cannot upgrade to Ubuntu 8.04

---

