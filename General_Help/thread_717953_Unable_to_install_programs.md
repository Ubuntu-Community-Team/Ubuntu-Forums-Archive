---
title: "Unable to install programs"
date: 2008-03-07
forum: General Help
---

### Post by Aaron_Griffiths_92 on 2008-03-07
I have downloaded a theme installer and i have absolutely no idea on how i can install it, i double click the .exe file and it gives me options, which none of actually do anything, i dont know what i should do and i want themes.

---

### Post by taurus on 2008-03-07
.exe is windows program.  You can't install .exe in Linux unless you install wine first!  What exactly are you trying to install?

Maybe this guide would explain a little better on how to install stuff in Ubuntu, [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/).

---

### Post by paul.matthijsse on 2008-03-07
hello, an exe-file is usually for Windows and can not be run/installed on Linux. If you want themes in Ubuntu, go to System - Preferences - Apparence (the last word is French, don't know the English word by heart).

---

### Post by Aaron_Griffiths_92 on 2008-03-07
ok so its not an exe file then, its just the actual executable, and i dont know how to install wine either! im so frustrated and ive had the program under an hour!

---

### Post by justsomedude on 2008-03-07
If you want to know how to install something on Ubuntu, read the link taurus posted.

If you tell us exactly what are you trying to install (link please), it's likely we can help you.

If you want themes, go to [www.gnome-look.org](www.gnome-look.org).

---

### Post by Aaron_Griffiths_92 on 2008-03-07
synaptic wont even let me find the file, why is linux so HARD?!?! I cant install wine, or anything, im getting very frustrated, when i search and specifically type the folder name i get NOTHING. I appreciate youre trying to help me but im boiling over at the moment

---

### Post by taurus on 2008-03-07
Do you have all the repos enable in /etc/apt/sources.list?

Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

p.s.  I can tell you right now.  if you start getting mad or frustrated, you are not going to go very far with it.  Just have to relax and start learning how to do things in Ubuntu!

---

### Post by PeterJS on 2008-03-07
Synaptic is for installing packages from the package management system. It doesn't know (or care) about local files. If you posted where you got the theme from we could take a look at the readme file and figure out what is what.

---

### Post by Aaron_Griffiths_92 on 2008-03-08
well could anyone just post a nice- easy to install theme?


Command results:
aaron@aaron-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
aaron@aaron-desktop:~$

---

### Post by Aaron_Griffiths_92 on 2008-03-08
anyone?

---

### Post by PeterJS on 2008-03-08
If you're looking for themes, Gnome-look.org was suggested above, and it pretty much the standard place to go for all your theming needs. If you're intent on using the theme that you started this thread about, please post where you got it from so we can see what format it's in and any documentation.

Synaptic really has nothing to do with installing themes, and I'm not entirely clear how we got side tracked there. On the upside thought your sources are all set up correctly.

---

### Post by MattBD on 2008-03-08
If you're looking for a nice easy theme (I'm assuming you're using Ubuntu, rather than Kubuntu or Xubuntu here), I recommend the Blubuntu theme. Just install the blubuntu-look package. You can either do this in Synaptic by searching for blubuntu-look, or open the command line and enter sudo apt-get install blubuntu-look.

You can then just go into Appearance and change the theme to Blubuntu. It includes a wallpaper, theme and everything.

---

### Post by Aaron_Griffiths_92 on 2008-03-08
well, thank you all and especially to matt BD for finding me a theme, just need to find one i want to pick now

---

