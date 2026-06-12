---
title: "Not All Updates Can Be Installed"
date: 2008-06-14
forum: General Help
---

### Post by bluewhale on 2008-06-14
Hello   

I upgraded 7.10 to 8.04 a week or two ago. Since then I have been unable to get any updates. When Update manager starts it throws an error message stating 

Not all updates can be installed.  Run a partial upgrade, to install as many updates as possible. 


When I try to do the partial upgrade the mouse pointer turns to a rotating circle then just disappears. No updates are done. Have tried a few things found mostly on this web site, but no luck thus far. 

Could someone kindly point me toward the fix?

---

### Post by LeoSolaris on 2008-06-14
Try this one.

In Software Sources, do you have proposed updates marked? If so, try unmarking it, refreshing the list, then updating.

If that doesn't work, you can force the update to go through with synaptic, by using the "mark all upgrades" then applying them. Synaptic doesn't have some of the built in safeties that Update manager has. This has a likelihood of removing something that you do not wish to remove. Synaptic will say it is removing software before you give the final ok, so check the remove list if there is one.

Leo

---

### Post by bluewhale on 2008-06-16
Hi Leo. 

No, the same thing occurs when I try to start Software Sources... a box appears on the task bar stating an admin program is starting, the mouse turns into a circling wheel for 20 seconds then nothing else occurs.  

Dug a bit. sources.list will not open manually using software sources, however it does open in a text editor. Any thoughts on making a change in this file to solve the problem?

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

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
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

As you indicated, I'd like to avoid using synaptic if possibly. 


paul

---

### Post by azurepancake on 2008-06-16
I really don't know if this will help you. It is just an idea that I thought I might share.

You might want to open up a terminal session and try typing the following..

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade 

``` 

I think the key here is the "dist-upgrade" part. Here is a summary from the man page..

```

dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new
versions of packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important
packages at the expense of less important ones if necessary. The /etc/apt/sources.list file contains a list of locations
from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general
settings for individual packages.

```

I hope this helps. If not, hey I tried! :)

---

### Post by oldos2er on 2008-06-16
All your sources are commented out, so until that changes, no update or upgrade commands will work.

 Try this in a terminal: sudo cp /etc/apt/sources.list /etc/apt/sources.list.bk

 That will make a backup copy of sources.list. Then use the command: gksudo gedit /etc/apt/sources.list, and remove the comment mark (#) from in front of lines beginning with deb and deb-src. You can safely skip the backports section, and the deb cdrom lines at the top. Save the file, exit, then again in a terminal, run: sudo aptitude update && sudo aptitude upgrade .

 Let us know how it turns out.

---

### Post by bluewhale on 2008-06-16
Azurepancake:  THANK YOU  \\:D/   
Your suggestion worked perfectly. I did reboot in between the first and second steps because soooooo many updates were processed. Then steps 2 and 3 went just fine. 

After that I checked for updates in the GUI Update Manager: none available. (!!!) 

Oldos2er: Thanks for the thoughts, however the command line above worked fine. I was curious about almost all sources having been commented out... Just FYI below is the CLI commentary for the second and third updates if of any interest. 

paul@PaulT:~$ sudo apt-get upgrade
sudo: unable to resolve host PaulT
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libgtk1.2 xmms-xmmplayer
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
paul@PaulT:~$ sudo apt-get dist-upgrade
sudo: unable to resolve host PaulT
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libglib1.2 xmms xmms-volnorm
The following NEW packages will be installed:
  libglib1.2ldbl
The following packages will be upgraded:
  libgtk1.2 xmms-xmmplayer
2 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 1124kB of archives.
After this operation, 6697kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libgtk1.2 1.2.10-18.1build2 [961kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse xmms-xmmplayer 0.3.3-1build1 [25.6kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libglib1.2ldbl 1.2.10-19build1 [138kB]
Fetched 1124kB in 6s (181kB/s)                                                 
(Reading database ... 113970 files and directories currently installed.)
Removing xmms-volnorm ...
Removing xmms ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 113855 files and directories currently installed.)
Preparing to replace libgtk1.2 1.2.10-18 (using .../libgtk1.2_1.2.10-18.1build2_amd64.deb) ...
Unpacking replacement libgtk1.2 ...
Preparing to replace xmms-xmmplayer 0.3.3-1 (using .../xmms-xmmplayer_0.3.3-1build1_amd64.deb) ...
Unpacking replacement xmms-xmmplayer ...
(Reading database ... 113853 files and directories currently installed.)
Removing libglib1.2 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package libglib1.2ldbl.
(Reading database ... 113841 files and directories currently installed.)
Unpacking libglib1.2ldbl (from .../libglib1.2ldbl_1.2.10-19build1_amd64.deb) ...
Setting up libglib1.2ldbl (1.2.10-19build1) ...

Setting up libgtk1.2 (1.2.10-18.1build2) ...

Setting up xmms-xmmplayer (0.3.3-1build1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
paul@PaulT:~$ 



Paul

---

### Post by azurepancake on 2008-06-16
Nice work Bluewhale, I'm very glad that I could be of help! :)

---

### Post by plucky on 2008-06-16
> paul@PaulT:~$ sudo apt-get upgrade
[color=red]sudo: unable to resolve host PaulT[/color]
[sudo] password for paul: 


See the sticky [thread](http://ubuntuforums.org/showthread.php?t=723361) for a workaround for the highlighted line.



Good Luck

---

