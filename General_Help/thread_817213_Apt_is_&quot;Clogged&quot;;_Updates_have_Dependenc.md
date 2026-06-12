---
title: "Apt is &quot;Clogged&quot;; Updates have Dependency Problems"
date: 2008-06-03
forum: General Help
---

### Post by navneeth on 2008-06-03
It started with two updates refusing to install. One was python-4suite-xml, and the other serpentine. Now this list has piled to so many updates, that it makes me crazy. That 139 error keeps showing up.

Here's the output from the terminal. 

[after updating packages]...

**apt-get upgrade** and **apt-get dist-upgrade** and **apt-get -f install** ...more or less show the same stuff. I think I may have uninstalled evolution, but I don't see that might have affected all the GNOME updates. 

I'd appreciate any help. 

```
navneeth@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
19 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up gnome-applets-data (2.22.2-0ubuntu1) ...
dpkg: error processing gnome-applets-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-panel-data (1:2.22.2-0ubuntu1) ...
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 1:2.22); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.23); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.22); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.23); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-panel (>= 2.13.4); however:
  Package gnome-panel is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
Setting up ekiga (2.0.12-0ubuntu2) ...
dpkg: error processing ekiga (--configure):
 subprocess post-installation script returned error exit status 139
Setting up eog (2.22.2-0ubuntu1) ...
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evince (2.22.2-0ubuntu1) ...
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evolution-common (2.22.1.1-0ubuntu3) ...
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 2.22.1.1-0ubuntu3); however:
  Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
Setting up f-spot (0.4.3.1-0ubuntu1) ...
dpkg: error processing f-spot (--configure):
 subprocess post-installation script returned error exit status 139
Setting up file-roller (2.22.3-0ubuntu1) ...
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gcalctool (5.22.2-0ubuntu1) ...
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gdm (2.20.6-0ubuntu2) ...
 * Reloading GNOME Display Manager configuration...                                                                             * Changes will take effect when all current X sessions have ended.
                                                                                                                        [ OK ]
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gedit-common (2.22.3-0ubuntu1) ...
dpkg: error processing gedit-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on gedit-common (>= 2.22); however:
  Package gedit-common is not configured yet.
 gedit depends on gedit-common (<< 2.23); however:
  Package gedit-common is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
Setting up gthumb (3:2.10.8-0ubuntu1) ...
dpkg: error processing gthumb (--configure):
 subprocess post-installation script returned error exit status 139
Setting up python-4suite-xml (1.0.2-1ubuntu1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-4suite-xml (--configure):
 subprocess post-installation script returned error exit status 1
Setting up seahorse (2.22.2-0ubuntu1) ...
dpkg: error processing seahorse (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of serpentine:
 serpentine depends on python-4suite-xml; however:
  Package python-4suite-xml is not configured yet.
dpkg: error processing serpentine (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 gnome-applets-data
 gnome-panel-data
 gnome-panel
 gnome-applets
 ekiga
 eog
 evince
 evolution-common
 evolution
 f-spot
 file-roller
 gcalctool
 gdm
 gedit-common
 gedit
 gthumb
 python-4suite-xml
 seahorse
 serpentine
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

**dpkg --configure -a**

```
navneeth@ubuntu:~$ sudo dpkg --configure -a
Setting up python-4suite-xml (1.0.2-1ubuntu1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-4suite-xml (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gdm (2.20.6-0ubuntu2) ...
 * Reloading GNOME Display Manager configuration...                                                                             * Changes will take effect when all current X sessions have ended.
                                                                                                                        [ OK ]
dpkg: error processing gdm (--configure):
 subprocess post-installation script returned error exit status 139
Setting up eog (2.22.2-0ubuntu1) ...
dpkg: error processing eog (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gedit-common (2.22.3-0ubuntu1) ...
dpkg: error processing gedit-common (--configure):
 subprocess post-installation script returned error exit status 139
Setting up seahorse (2.22.2-0ubuntu1) ...
dpkg: error processing seahorse (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on gedit-common (>= 2.22); however:
  Package gedit-common is not configured yet.
 gedit depends on gedit-common (<< 2.23); however:
  Package gedit-common is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
Setting up gcalctool (5.22.2-0ubuntu1) ...
dpkg: error processing gcalctool (--configure):
 subprocess post-installation script returned error exit status 139
Setting up evince (2.22.2-0ubuntu1) ...
dpkg: error processing evince (--configure):
 subprocess post-installation script returned error exit status 139
Setting up file-roller (2.22.3-0ubuntu1) ...
dpkg: error processing file-roller (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gnome-applets-data (2.22.2-0ubuntu1) ...
dpkg: error processing gnome-applets-data (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of serpentine:
 serpentine depends on python-4suite-xml; however:
  Package python-4suite-xml is not configured yet.
dpkg: error processing serpentine (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-panel-data (1:2.22.2-0ubuntu1) ...
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 139
Setting up gthumb (3:2.10.8-0ubuntu1) ...
dpkg: error processing gthumb (--configure):
 subprocess post-installation script returned error exit status 139
Setting up f-spot (0.4.3.1-0ubuntu1) ...
dpkg: error processing f-spot (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gnome-applets-data (>= 2.22); however:
  Package gnome-applets-data is not configured yet.
 gnome-applets depends on gnome-applets-data (<< 2.23); however:
  Package gnome-applets-data is not configured yet.
dpkg: error processing gnome-applets (--configure):
 dependency problems - leaving unconfigured
Setting up evolution-common (2.22.1.1-0ubuntu3) ...
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 139
Setting up ekiga (2.0.12-0ubuntu2) ...
dpkg: error processing ekiga (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (>= 1:2.22); however:
  Package gnome-panel-data is not configured yet.
 gnome-panel depends on gnome-panel-data (<< 1:2.23); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 2.22.1.1-0ubuntu3); however:
  Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 python-4suite-xml
 gdm
 eog
 gedit-common
 seahorse
 gedit
 gcalctool
 evince
 file-roller
 gnome-applets-data
 serpentine
 gnome-panel-data
 gthumb
 f-spot
 gnome-applets
 evolution-common
 ekiga
 gnome-panel
 evolution

```

---

### Post by navneeth on 2008-06-03
Bump!

---

### Post by wootah on 2008-06-03
Can you post your sources.list ?

---

### Post by navneeth on 2008-06-03
Sure. 

(I just realised that I have forgotten to remove the Automatix repos after the upgrade to Hardy. :oops:)

```
#
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
deb http://in.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://in.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

# deb http://kubuntu.org/packages/amarok-145 edgy main

#AUTOMATIX REPOS START

# deb http://www.getautomatix.com/apt gutsy main

deb http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu hardy-updates universe multiverse

# deb http://www.getautomatix.com/apt feisty main

# deb http://archive.canonical.com/ubuntu feisty-commercial main

# deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

# deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

# deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

# deb http://kent.dl.sourceforge.net/sourceforge/ skychart/
# deb http://nchc.dl.sourceforge.net/sourceforge/ skychart/
```

---

### Post by wootah on 2008-06-03
Have you tried:
```
sudo apt-get purge && sudo apt-get autoremove
```

---

### Post by navneeth on 2008-06-04
> **wootah said:**
> Have you tried:
```
sudo apt-get purge && sudo apt-get autoremove
```

Don't I have to supply some package name as an argument? If I don't need to do that, could you please tell me what this command does? Thanks.

---

### Post by iaculallad on 2008-06-04
Try changing your "Download From" to equal "Main Server" under "Ubuntu Software" tab of Software Sources. Click on close and do:

System->Administration->Software Sources

On your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by zvacet on 2008-06-04
You can make your source list look better by removing repos you don´t need anymore.

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

Save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

There is no Automatix for Hardy.You can add Medibuntu repos in your source list by typing 

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by navneeth on 2008-06-04
> **iaculallad said:**
> Try changing your "Download From" to equal "Main Server" under "Ubuntu Software" tab of Software Sources. Click on close and do:

System->Administration->Software Sources

On your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

Thanks for the reply. I Did that. Nothing has changed.  :(

There were some updates for the Linux kernel today, and I had downloaded them before changing the software source. Now they also won't install.

---

### Post by navneeth on 2008-06-04
UPDATE: I think I have the kernel images installed. I cleared /var/cache/apt and did a apt-get -f install. The rest of the packages are still stuck, though.

---

### Post by wootah on 2008-06-04
Eck sorry for the late reply--purge and autoremove clears your package cache and removes unmet dependencies. Neither require additional arguments. After looking at everything else that has happened in this thread, I'm not sure that will help you though. You can still give it a try though :)

---

### Post by navneeth on 2008-06-05
Nope, that didn't work. Thanks, anyway. There were a bunch of updates just now. It went smoothly, except for Rythmbox, which joined the list as #20. :) But the weird thing is, if I type the install command for any of those packages, I get a message saying that it has already been installed and it is **the latest version**.

---

### Post by wootah on 2008-06-05
> **navneeth said:**
> Nope, that didn't work. Thanks, anyway. There were a bunch of updates just now. It went smoothly, except for Rythmbox, which joined the list as #20. :) But the weird thing is, if I type the install command for any of those packages, I get a message saying that it has already been installed and it is **the latest version**.

This is a strange problem indeed .... so is it still broke... or ?

---

### Post by navneeth on 2008-06-05
Yes...sort of. I still get the error messages and the list of applications causing all the trouble when I do apt-get (dist-)upgrade, but I don't see the "Something is broken" icon in the panel.

---

### Post by zvacet on 2008-06-05
Try with 

```
sudo dpkg --configure -a
```

or 
 
```
sudo apt-get -f install
```

---

### Post by navneeth on 2008-06-06
zvacet, I tried that. (please refer to post #1.)

---

