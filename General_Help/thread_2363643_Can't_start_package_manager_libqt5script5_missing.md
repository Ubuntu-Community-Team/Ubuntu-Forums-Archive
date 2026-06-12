---
title: "Can't start package manager libqt5script5 missing"
date: 2017-06-12
forum: General Help
---

### Post by JamButty on 2017-06-12
Just did a wipe and reload of Xerus (16.04).  While loading an optional package (Tellico), dpkg (I assume - was using software center) hung. Would not complete, did not generate any error that it displayed, and would not allow any further programs to be installed. rebooted to continue loading apps. This may or may not be related to what is now happening a day later. After a bleachbit wipe, a warning icon appeared in the top bar with a message;
> E: The package libqt5script5 needs to be reinstalled, but I can't find an archive for it.

Synaptic won't start for the same reason. Warning icon message indicates this may be due to missing dependencies, but if I can't start the package manager, how can I proceed?

thanks.

---

### Post by ajgreeny on 2017-06-12
It is in the xenial 16.04 repos so I am unsure why you can't find it.

It is in universal repos so make sure from software sources that you have them enabled; I was under the impression that they were always enabled by default but perhaps that is not so any more.

---

### Post by monkeybrain20122 on 2017-06-12
Try to install it from the terminal

```
sudo apt update && sudo apt install libqt5script5
```

You might have removed your cache with bleachbit, so you need to run apt update first or packages may not show up.

---

### Post by JamButty on 2017-06-12
I have xenial universe and xenial multiverse. That should cover it yes?

here is my /etc/apt/sources.list
```
#deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
```

Monkeybrain20122

I have the output from that, but it goes on for many pages. Hopefully this is the critical part
```
dpkg: error processing package libqt5script5:amd64 (--configure): package libqt5script5:amd64 is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: dependency problems prevent configuration of libkf5i18n5:amd64:
 libkf5i18n5:amd64 depends on libqt5script5 (>= 5.0.2); however:
  Package libqt5script5:amd64 is not installed.


dpkg: error processing package libkf5i18n5:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    dpkg: dependency problems prevent configuration of libkf5configwidgets5:amd64:
 libkf5configwidgets5:amd64 depends on libkf5i18n5 (>= 4.97.0); however:
  Package libkf5i18n5:amd64 is not configured yet.



```
this is followed by many pages of dependency errors (can't do this cuz of that)
also at the end it lists everything it had an issue with. It ends with the app that hung on installation - Tellico
```
libqt5script5:amd64 libkf5i18n5:amd64
 libkf5configwidgets5:amd64
 libkf5iconthemes5:amd64
 libkf5style5:amd64
 kde-style-breeze
 kde-style-breeze-qt4
 kde-runtime
 k3b
 libkf5service5:amd64
 libkf5service-bin
 libkf5kiocore5:amd64
 libkf5kiowidgets5:amd64
 libkf5package5:amd64
 kpackagetool5
 libkf5declarative5:amd64
 qml-module-org-kde-kquickcontrols:amd64
 libkf5quickaddons5:amd64
 qml-module-org-kde-kquickcontrolsaddons:amd64
 libkf5textwidgets5:amd64
 libkf5xmlgui5:amd64
 libkf5plasma5:amd64
 libkf5plasmaquick5:amd64
 plasma-framework
 qml-module-org-kde-activities:amd64
 kactivities
 libkf5kcmutils5:amd64
 libkf5bookmarks5:amd64
 libkf5kiofilewidgets5:amd64
 libkf5parts5:amd64
 libkf5kdelibs4support5:amd64
 libkwalletbackend5-5:amd64
 libkf5wallet5:amd64
 libkf5wallet-bin
 libkf5khtml5:amd64
 libkf5khtml-bin
 khelpcenter
 khelpcenter4
 kpackagelauncherqml
 libkf5iconthemes-bin
 libkf5kdelibs4support5-bin
 libkf5parts-plugins
 libkf5xmlgui-bin
 tellico
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

hmmm...good news that makes no sense. cold pizza.
Despite generating 20-30 pages of error messages,  all things apt are apt again.
Thanks!

Can I ask for advice? Since rebooting to clear a hung install seems to have been the offense against our Great Squirrel, any tips on how to better deal with a hung install that prevents all other attempts to install anything?

no cold pizza, hot rancid porridge. Synaptic loaded and updater looked ok initially, but 4 install attempts have all failed. Screw this, I will wipe reload again. I have to do it about once a season with this damn Xerus anyway.

---

### Post by ajgreeny on 2017-06-13
> **JamButty said:**
> no cold pizza, hot rancid porridge. Synaptic loaded and updater looked ok initially, but 4 install attempts have all failed. Screw this, I will wipe reload again. I have to do it about once a season with this damn Xerus anyway.
It should not normally be necessary to reinstall your system as often as you suggest you have to, so I wonder if you are doing something that causes these problems.

Are you adding a lot of PPA repos, or installing packages from source that you have compiled and installed manually? That can on occasion give the sort of dependency problem that you have seen as a result of library package version incompatibilities.

---

### Post by JamButty on 2017-06-13
Nope, very simple user, I wouldn't know how to compile a dossier. The only non-universe bits I install are nauty-hacks1 and caffeine. Standard install from DVD media, nothing creative.
I am back up after secondary wipe/reload and all looks normal so far.

The need to wipe and reload 3-4 times a year since upgrading to Xerus is an issue I have posted about twice to no response. I have found a few other people describing similar problems also to no response, so I am guessing it is not so widespread (boots to splash background only, no Unity launcher. Access to terminal via right click but that is about it. This occurs spontaneously after some months of use and no unusual use. I have found no pattern to it). 
I have come to accept it as unavoidable, but it is frustrating when new issues complicate that further.
Thanks ajgreeny. You've pulled my cookies out of the fire before and I do appreciate your input.

---

