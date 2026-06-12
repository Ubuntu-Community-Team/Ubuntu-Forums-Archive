---
title: "Updating Error"
date: 2007-02-02
forum: General Help
---

### Post by Corgana on 2007-02-02
I recently got Ubuntu up and running (god help those who have Radeon™ IGP 320M cards..) After running automatix, and getting the programs I like installed, I restartted, just to be safe, and I had a new update notifcation. But when I Click on the notification icon, the update window flashes quickly and goes away, when I right click and select "check for updates" I get this error:

> Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

I hit "ok" and up pops this error:

> E: Type 'O::deb' is not known on line 38 in source list /etc/apt/sources.list
E: Unable to lock the list directory

I looked around for a solution, but came up with nothing. I know the support here is Excellent so I figured I'd ask. I'm experienced with windows, but still have alot to learn about Linux and Ubuntu, so any help would be appreciated.

Thanks in advance! :) 

Update: the same error occours while trying to access synaptic :confused:

---

### Post by jasutton on 2007-02-02
All of ubuntu's update methods use the same mechanism: that is apt.  So, that's why Synaptic doesn't work either.  Could you post the contents of your /etc/apt/sources.list file?  Automatix can play with that file (which dictates where you pull updates from) if I remember correctly, so if it messed up, it could break your updates.

A good rule of thumb is that all lines that aren't comments (commented lines begin with a '#' sign) should start with the word 'deb', so if you see something else there, I would try commenting that line out and see if that solves the problem.

Keep in mind that any changes to files such as these (anything outside your home directory), require that you do so as root (i.e., with sudo). ;)

---

### Post by Corgana on 2007-02-02
Here's the contents..

> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

O::deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main
FATAL::An apt-based error occured and installation was unsuccessful

O::deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END


---

### Post by jasutton on 2007-02-02
You need to remove the "O::" on those two lines just below "#AUTOMATIX REPOS START".  You can also completely remove the one that says "FATAL::An apt-based error occured and installation was unsuccessful."

I think that should fix your problem.

---

