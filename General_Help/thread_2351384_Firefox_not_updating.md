---
title: "Firefox not updating"
date: 2017-02-02
forum: General Help
---

### Post by barbarian818 on 2017-02-02
Recently I have noticed that many sites are telling me my browser is out of date and that I should update. I checked the "About Firefox" menu option and found I am using version 44.0 Mozilla Firefox for Ubuntu canonical -1.0 
Firefox is now up to 51.0 in the stable branch, so obviously I have missed several update cycles. The thing is, I have all the official Ubuntu Software and Ubuntu partner packaged software (except for source code) enabled in my software sources. Package upgrade behaviour is set to "Always prefer the highest version", direct connection to the Internet, check daily for updates, other updates to display weekly and include unsupported updates (vivid-backports)
I've been getting all other Ubuntu software updates as far as I know. I prefer to use Synaptic Package Manager, and when I check for Firefox there, it says that 44.0_build3-0ubuntu0.15.04.1 is the latest version on the repository and is already installed. As far as I know, Firefox version 51 should be available on the repository by now.

Steps taken so far:
made sure to reload package information = No change in available version on the repo.

sudo apt-get update; apt-get upgrade = found some updates for other software that I had manually added ppa repos for, no changes in Firefox version

manually added [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) to my Other Software sources list, reloaded Synaptic = no change in Firefox version available. I WAS able to see this ppa scroll by in the terminal when running apt-get update, so apt-get seems to be hitting that repo but not finding anything relevant.

based on something read elsewhere, I disabled the Ubuntu Modifications plugin hoping to enable the update function in the Firefox Help menu = Firefox update does not appear

used the terminal to add "ppa:mozillateam/firefox-next to see if I could bypass the main upgrade path by going to the daily beta build, made sure to do apt-get update and apt-get upgrade = The terminal response did NOT show any difference in available packages. I.E. despite apparently hitting ppa:mozillateam/firefox-next, it didn't find a package. I then removed that ppa.

Changed from server for Canada to Main server and reloaded= no change

Used Synaptic to run Fix Broken Packages an clear package cache. = no change

used a terminal command to concatenate etc/apt/sources.list and the contents of /etc/apt/sources.list.c and export to a text file. (pasted below) I went through the resulting file and confirmed that nothing was commented out that shouldn't be. 

System:
Ubuntu 15.04
Gnome 3.14.1 
3.19.0-79-generic 

```
CONCATENATED SOURCES LIST
# deb cdrom:[Ubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422)]/ vivid main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) vivid-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) vivid partner

deb [http://repos.codelite.org/wx3.0.2/ubuntu/](http://repos.codelite.org/wx3.0.2/ubuntu/) utopic universe
# deb-src [http://repos.codelite.org/wx3.0.2/ubuntu/](http://repos.codelite.org/wx3.0.2/ubuntu/) utopic universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) vivid-security main multiverse
deb [http://apt.insynchq.com/ubuntu](http://apt.insynchq.com/ubuntu) vivid non-free contrib
# deb-src [http://apt.insynchq.com/ubuntu](http://apt.insynchq.com/ubuntu) vivid non-free contrib
deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) vivid main
# deb-src [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) vivid main
# deb-src [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu) vivid main
deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) vivid main
# deb-src [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) vivid main
deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) vivid main
deb [http://ppa.launchpad.net/fyrmir/livewallpaper-daily/ubuntu](http://ppa.launchpad.net/fyrmir/livewallpaper-daily/ubuntu) vivid main
# deb-src [http://ppa.launchpad.net/fyrmir/livewallpaper-daily/ubuntu](http://ppa.launchpad.net/fyrmir/livewallpaper-daily/ubuntu) vivid main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/musicmanager/deb/](http://dl.google.com/linux/musicmanager/deb/) stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://ppa.launchpad.net/i2p-maintainers/i2p/ubuntu](http://ppa.launchpad.net/i2p-maintainers/i2p/ubuntu) vivid main
deb [http://ppa.launchpad.net/i2p.packages/i2p/ubuntu](http://ppa.launchpad.net/i2p.packages/i2p/ubuntu) vivid main
# deb-src [http://ppa.launchpad.net/i2p.packages/i2p/ubuntu](http://ppa.launchpad.net/i2p.packages/i2p/ubuntu) vivid main
deb [http://ppa.launchpad.net/opensync/opensync-0.22/ubuntu](http://ppa.launchpad.net/opensync/opensync-0.22/ubuntu) precise main
# deb-src [http://ppa.launchpad.net/opensync/opensync-0.22/ubuntu](http://ppa.launchpad.net/opensync/opensync-0.22/ubuntu) precise main
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) vivid main
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) vivid main
deb [http://ppa.launchpad.net/ubuntuhandbook1/dvdstyler/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/dvdstyler/ubuntu) vivid main
# deb-src [http://ppa.launchpad.net/ubuntuhandbook1/dvdstyler/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/dvdstyler/ubuntu) vivid main
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) vivid main
# deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) vivid main
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) vivid main
# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) vivid main
```

---

### Post by barbarian818 on 2017-02-02
adding reply so as to change my notification setting

---

### Post by bcschmerker on 2017-02-02
Sorry, but ubuntu® 15.04 is no longer supported - support ended October 2015 soon after the release of 15.10.  A dist-upgrade to 16.04.1-LTS or 16.10 is a Pre-Depend.

Mozilla® Firefox® 51.0.1 is available for ubuntu® 14.04.6-LTS, 16.04.2-LTS, 16.10, and 17.02b2; 12.04.8-LTS will be end-of-support-life April 2017.

---

### Post by Impavidus on 2017-02-03
Ubuntu 15.04 reached end of life a year ago. You haven't received any updates for a year, except some PPAs that may still support your version of Ubuntu. I suggest a clean install of Ubuntu 16.04 LTS, which will be supported until April 2021.

Don't try a release upgrade. With another unsupported release inbetween, a lot of PPAs and a system in a poor state, a release upgrade will probably fail.

---

