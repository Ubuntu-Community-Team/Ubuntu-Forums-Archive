---
title: "Error message E:Type'&quot;deb' is not known on line 42"
date: 2007-05-16
forum: General Help
---

### Post by alanhilditch on 2007-05-16
When I click on a red icon top right of screen a message is displayed,

A error occured, please run Package manager from the right click menu or apt-get on a terminal to see what is wrong.
The error message was: 'Error: Opening the Cache (E:Type'"deb' is not known on line 42 in source lit/etc/apt/sources/list. E: The list of sources could not be read)

I am running 6.10lts and have no idea what to do next being a newbie. I was trying to install a progam that threw up this fault. Not sure which progam though.
 Help Please!

---

### Post by carlosqueso on 2007-05-16
please type ```
cat /etc/apt/sources.list
``` and post the output.

---

### Post by alanhilditch on 2007-05-16
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiversedeb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://mirror3.ubuntulinux.nl/](http://mirror3.ubuntulinux.nl/) dapper-seveas freenx
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”

---

### Post by carlosqueso on 2007-05-16
Okay, what you need to do is edit your sources list with ```
gksudo gedit /etc/apt/sources.list
``` and remove the quotes from the  ```
&#8220;deb http://www.getautomatix.com/apt dapper main&#8221;
```  If you're trying to comment it out and not use it, use the # symbol.  If you do want to use it, then just remove the quotes and it'll work

---

### Post by alanhilditch on 2007-05-16
sources.list came up, deleted quotes, pressed enter then nothing happened, should anything happen?

---

### Post by taurus on 2007-05-16
Just save it (after removing the " " from the last line) and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by DoktorSeven on 2007-05-16
When you delete the quotes use gedit to save the file back (File->Save).  Next time apt updates itself it should be fixed.

If you don't want to wait, run **gksudo synaptic** and hit Reload (or **sudo apt-get update** from the Terminal).

---

### Post by alanhilditch on 2007-05-16
Thank You all, it seems to have worked okay

---

