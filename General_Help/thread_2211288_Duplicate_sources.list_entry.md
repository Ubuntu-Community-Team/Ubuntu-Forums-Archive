---
title: "Duplicate sources.list entry"
date: 2014-03-15
forum: General Help
---

### Post by nabz0r on 2014-03-15
Hi guys, 
I have these duplicates/errors when I do apt-get update/upgrade. I have tried to modify the source.list but it got worse, before I had only few duplicates and now I get these. Can anyone help me fix this? I'd appreciate your help and thank you in advanced! 

Edit: added my source.list

```

wwk@ubt:~$sudo apt-get update
W: Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)/dists/saucy/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMsW: Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)/dists/saucy/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
W: Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)/dists/saucy/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
W: Failed to fetch cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)/dists/saucy/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
E: Some index files failed to download. They have been ignored, or old ones used instead.

wwk@ubt:~$ sudo nano /etc/apt/sources.list

wwk@ubt:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Duplicate sources.list entry http://www.ubnt.com/downloads/unifi/distros/deb/squeeze/ squeeze/ubiquiti amd64 Packages (/var/lib/apt/lists/www.ubnt.com_downloads_unifi_distros_deb_squeeze_dists_squeeze_ubiquiti_binary-amd64_Packages)
W: Duplicate sources.list entry http://www.ubnt.com/downloads/unifi/distros/deb/squeeze/ squeeze/ubiquiti amd64 Packages (/var/lib/apt/lists/www.ubnt.com_downloads_unifi_distros_deb_squeeze_dists_squeeze_ubiquiti_binary-amd64_Packages)
W: Duplicate sources.list entry http://www.ubnt.com/downloads/unifi/distros/deb/squeeze/ squeeze/ubiquiti i386 Packages (/var/lib/apt/lists/www.ubnt.com_downloads_unifi_distros_deb_squeeze_dists_squeeze_ubiquiti_binary-i386_Packages)
W: Duplicate sources.list entry http://www.ubnt.com/downloads/unifi/distros/deb/squeeze/ squeeze/ubiquiti i386 Packages (/var/lib/apt/lists/www.ubnt.com_downloads_unifi_distros_deb_squeeze_dists_squeeze_ubiquiti_binary-i386_Packages)
W: Duplicate sources.list entry http://downloads-distro.mongodb.org/repo/ubuntu-upstart/ dist/10gen amd64 Packages (/var/lib/apt/lists/downloads-distro.mongodb.org_repo_ubuntu-upstart_dists_dist_10gen_binary-amd64_Packages)
W: Duplicate sources.list entry http://downloads-distro.mongodb.org/repo/ubuntu-upstart/ dist/10gen amd64 Packages (/var/lib/apt/lists/downloads-distro.mongodb.org_repo_ubuntu-upstart_dists_dist_10gen_binary-amd64_Packages)
W: Duplicate sources.list entry http://downloads-distro.mongodb.org/repo/ubuntu-upstart/ dist/10gen i386 Packages (/var/lib/apt/lists/downloads-distro.mongodb.org_repo_ubuntu-upstart_dists_dist_10gen_binary-i386_Packages)
W: Duplicate sources.list entry http://downloads-distro.mongodb.org/repo/ubuntu-upstart/ dist/10gen i386 Packages (/var/lib/apt/lists/downloads-distro.mongodb.org_repo_ubuntu-upstart_dists_dist_10gen_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

```

deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://se.archive.ubuntu.com/ubuntu/ saucy main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ saucy main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://se.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ saucy-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ saucy universe
deb-src http://se.archive.ubuntu.com/ubuntu/ saucy universe
deb http://se.archive.ubuntu.com/ubuntu/ saucy-updates universe
deb-src http://se.archive.ubuntu.com/ubuntu/ saucy-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://se.archive.ubuntu.com/ubuntu/ saucy multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ saucy multiverse
deb http://se.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ saucy-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu saucy-security main restricted
deb-src http://security.ubuntu.com/ubuntu saucy-security main restricted
deb http://security.ubuntu.com/ubuntu saucy-security universe
deb-src http://security.ubuntu.com/ubuntu saucy-security universe
deb http://security.ubuntu.com/ubuntu saucy-security multiverse
deb-src http://security.ubuntu.com/ubuntu saucy-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu saucy partner
# deb-src http://archive.canonical.com/ubuntu saucy partner
```

---

### Post by matt_symes on 2014-03-15
Hi

It looks like the problem may be with your PPAs. 

Can you post back the output of this command so we can take a look 

```
grep -n "^[^#]" /etc/apt/sources.list.d/*
```

Kind regards

---

### Post by nabz0r on 2014-03-15
Here you go.

```
wwk@ubt:~$ grep -n "^[^#]" /etc/apt/sources.list.d/*
/etc/apt/sources.list.d/20ubiquiti.list:1:deb http://www.ubnt.com/downloads/unifi/distros/deb/squeeze squeeze ubiquiti
/etc/apt/sources.list.d/20ubiquiti.list:2:deb http://www.ubnt.com/downloads/unifi/distros/deb/precise precise ubiquiti
/etc/apt/sources.list.d/20ubiquiti.list:3:deb http://www.ubnt.com/downloads/unifi/distros/deb/squeeze squeeze ubiquiti
/etc/apt/sources.list.d/20ubiquiti.list:4:deb http://www.ubnt.com/downloads/unifi/distros/deb/squeeze squeeze ubiquiti
/etc/apt/sources.list.d/20ubiquiti.list.save:1:deb http://www.ubnt.com/downloads/unifi/distros/deb/squeeze squeeze ubiquiti
/etc/apt/sources.list.d/20ubiquiti.list.save:2:deb http://www.ubnt.com/downloads/unifi/distros/deb/precise precise ubiquiti
/etc/apt/sources.list.d/21mongodb.list:1:deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen
/etc/apt/sources.list.d/21mongodb.list:2:deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen
/etc/apt/sources.list.d/21mongodb.list:3:deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen
/etc/apt/sources.list.d/21mongodb.list.save:1:deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen
/etc/apt/sources.list.d/ehoover-compholio-saucy.list:1:deb http://ppa.launchpad.net/ehoover/compholio/ubuntu saucy main
/etc/apt/sources.list.d/ehoover-compholio-saucy.list.save:1:deb http://ppa.launchpad.net/ehoover/compholio/ubuntu saucy main
/etc/apt/sources.list.d/gns3-ppa-saucy.list:1:deb http://ppa.launchpad.net/gns3/ppa/ubuntu saucy main
/etc/apt/sources.list.d/gns3-ppa-saucy.list.save:1:deb http://ppa.launchpad.net/gns3/ppa/ubuntu saucy main
/etc/apt/sources.list.d/google-chrome.list:3:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:3:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/mqchael-pipelight-saucy.list:1:deb http://ppa.launchpad.net/mqchael/pipelight/ubuntu saucy main
/etc/apt/sources.list.d/mqchael-pipelight-saucy.list.save:1:deb http://ppa.launchpad.net/mqchael/pipelight/ubuntu saucy main
/etc/apt/sources.list.d/pipelight-stable-saucy.list:1:deb http://ppa.launchpad.net/pipelight/stable/ubuntu saucy main
/etc/apt/sources.list.d/pipelight-stable-saucy.list.save:1:deb http://ppa.launchpad.net/pipelight/stable/ubuntu saucy main
/etc/apt/sources.list.d/steam.list:1:deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
/etc/apt/sources.list.d/steam.list:2:deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
/etc/apt/sources.list.d/steam.list.save:1:deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
/etc/apt/sources.list.d/steam.list.save:2:deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
/etc/apt/sources.list.d/team-xbmc-ppa-saucy.list:1:deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu saucy main
/etc/apt/sources.list.d/team-xbmc-ppa-saucy.list.save:1:deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu saucy main
/etc/apt/sources.list.d/tualatrix-ppa-saucy.list:1:deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu saucy main
/etc/apt/sources.list.d/tualatrix-ppa-saucy.list.save:1:deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu saucy main



```

---

### Post by matt_symes on 2014-03-15
Hi

As suspected, the problem is with your PPAs. 

Apt is also trying to update from your CDRom. You may or may not want to continue to let apt do this. 

As for the other errors, open a terminal and copy and paste this command into it.

```
sudo sed -i '2,$d' /etc/apt/sources.list.d/{20ubiquiti.list,21mongodb.list}
```

It will delete all the lines of the two files apart from the first line, so removing the duplicates.

Then type

```
sudo apt-get update
```

Do you want it to check the CDRom each time ?

Kind regards

---

### Post by nabz0r on 2014-03-15
Thank you, the errors are gone now. No I don't want to check CDRom for updating from CDRom. Is that an easy fix too? Thanks once again for the huge help!

Edit: I did the following: 
#deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted
And the error is gone for CDRom, is that correct?

Best Regards
nabz0r

---

### Post by matt_symes on 2014-03-15
Hi

> **nabz0r said:**
> Thank you, the errors are gone now. No I don't want to check CDRom for updating from CDRom. Is that an easy fix too? Thanks once again for the huge help!

Regards

That's a simple fix as well.

Copy and paste this into a terminal

```
sudo sed -i '/cdrom/s/^/#/' /etc/apt/sources.list
```

The above command will comment out (add a # at the start of) the line containing the word cdrom.

After that type

```
sudo apt-get update
```

You should then be good to go.

**EDIT:**

Just seen your edit to your above post.

What you did was fine and will stop apt checking the cdrom on each update.

Kind regards

---

### Post by nabz0r on 2014-03-15
Thanks man! I even entered your command in the terminal though I didn't get any CDRom question whilte updating/upgrading.

Br
nabz0r

---

