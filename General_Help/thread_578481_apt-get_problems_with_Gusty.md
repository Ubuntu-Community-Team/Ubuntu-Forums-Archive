---
title: "apt-get problems with Gusty"
date: 2007-10-17
forum: General Help
---

### Post by cliffhanger407 on 2007-10-17
I'm having... issues. I was trying to get packages on a fresh install of Gusty (after my upgrade from Feisty got botched somehow :(), and nothing seems to be working.

For instance:```
sudo apt-get vim-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package vim-gnome is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vim-gnome has no installation candidate

```This shouldn't be, though, as it's clearly listed in the gusty packages. So I'm confused... I think to myself, maybe it's already installed and doesn't need a package, but nope, that's not right. ```
mornc@mornc-e1405:~$ gvim
The program 'gvim' can be found in the following packages:
 * vim
 * vim-perl (You will have to enable component called 'universe')
 * vim-ruby (You will have to enable component called 'universe')
 * vim-full (You will have to enable component called 'universe')
 * vim-python (You will have to enable component called 'universe')
 * vim-tcl (You will have to enable component called 'universe')
** * vim-gnome**
 * vim-tiny
 * vim-gtk (You will have to enable component called 'universe')
Try: sudo apt-get install <selected package>
bash: gvim: command not found

```
Ok, that's weird.
```
apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release Candidate i386 (20071010) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release Candidate i386 (20071010) gutsy/restricted Translation-en_US
Reading package lists... Done

```

I'm at a loss for what to do. What's the deal with the lgn cdrom://* being in my package lists? I'm fairly sure this is why nothing is working, I just don't know how to fix it as I'm a bit new at this. Any help is greatly appreciated.

---

### Post by bapoumba on 2007-10-17
Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by cliffhanger407 on 2007-10-17
```
mornc@mornc-e1405:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release Candidate i386 (20071010)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```
I installed without network, so maybe that's why? Looks like I just need to reconfigure this file, but before I mess around, I'll listen to advice. Thanks!

---

### Post by bapoumba on 2007-10-17
Yeah, probably :)
Comment the cdrom line (at the top) and uncomment the other ones.
It may be quicker you compare to mine, rather than I point out all the lines to uncomment:

```
# Base.
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

## Bug fix updates.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

# Security.
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
```

---

### Post by cliffhanger407 on 2007-10-17
Well that was a quick problem resolution! Thanks so much for your help.

---

### Post by bapoumba on 2007-10-17
Your're welcome, glad to see you got it to work :)

---

### Post by cosmiccharles on 2007-10-21
I seem to be having the same exact problem with my apt get that cliffhanger had but I am way more of a newbie!!!! I am not really sure what I need to change with my  etc/apt/sources.list but mine seems to be exactly like cliffhanger's. I don't want to mess around with my files without any  type of help because I know that will probably just make it worse. If anyone could, cliffhanger or anyone, please help a newbie out! Thank you!



Here is what my sources.list reads: 

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by bapoumba on 2007-10-22
@ cosmiccharles: the **sources.list** file tells the package managers where to fetch packages. This is a text file that can be edited with any text editor, provided you use it with root access because the file is in the system part of the tree. When a line starts with a **#**, it is not taken into account (ie it is commented).

If you look at your own file, you will see that only the cdrom line is uncommented (all the other lines stating with deb.. are in comment with a **#**). What the other person did was simply **replacing** the whole sources.list file with mine. You can also look at mine, and uncomment the proper lines in yours

Basically, first save your current file, if anything goes wrong you can restore it:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_bak
```

Then edit the file. I like** nano**,  small text editor working from the terminal:
```
sudo nano /etc/apt/sources.list
```
Modify the file.
Save it with CTRL-O (hit <enter> to save it with the same name)
Exit nano with CTRL-X.
All the commands for nano are displayed at the bottom of the screen.

Reload the file, so the package managers take it into account:
```
sudo aptitude update
```

You are all set. You probably need to run:
```
sudo aptitude dist-upgrade
```
to make sure your distribution is up to date.

---

### Post by Phette on 2007-12-16
Great explanation!!

I have a few questions just for clarity on this subject.

For one...is there a way using nano to copy and paste your text into my sources.list file, or would I have to just type everything out?

Also, could you explain what it means and why the installer is failing to verify?  I installed the latest version (7.10 gutsy gibbons), and have just been messing with it recently.  Why does this problem arise in the first place?

---

### Post by ugm6hr on 2007-12-16
> **Phette said:**
> For one...is there a way using nano to copy and paste your text into my sources.list file, or would I have to just type everything out?

Also, could you explain what it means and why the installer is failing to verify?  I installed the latest version (7.10 gutsy gibbons), and have just been messing with it recently.  Why does this problem arise in the first place?

I am not sure about nano's advanced editing shortcuts, but you can paste by clicking both mouse buttons at the same time over where you want to insert the text.

For GUI editing (e.g. right-click for editing menu on screen etc), try this instead:
```
gksudo gedit /etc/apt/sources.list
```

As for why it happens - I am no expert on the inner workings of Ubuntu, but if you install without a live internet connection presumably Ubuntu does not activate the network repos (in case you don't have internet at all, to prevent errors when you run Synaptic).  You can activate these repos from within Synaptic (rather than editing a text file), which should have the same effect:
From Synaptic Package Manager - go to Settings Menu -> Repositories - in the new window tick the top 4 entries in the Ubuntu Software tab and the top 2 in the Updates tab.

---

### Post by bapoumba on 2007-12-16
You can paste into nano:
- highlight a text then middle mouse click to paste
- highlight a text, <ctrl><c> to copy, <shift><ctrl><v> to paste.

And +1 for ugm6hr's explanation of the installation without internet.

---

