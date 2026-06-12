---
title: "Broken pacakges?"
date: 2013-09-07
forum: General Help
---

### Post by kiddykoff on 2013-09-07
If anyone can help me with my problem i'll greatly appreciate it. The problem is that i have broken packages, but i am unable to figure out what they are, but i know they're there because i'm trying to install sound-juicer and am confronted with this message.```
$ sudo apt-get install sound-juicer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 sound-juicer:i386 : Depends: libatk1.0-0:i386 (>= 1.12.4) but it is not installable
                     Depends: libbrasero-media3-1:i386 (>= 2.91.91) but it is not installable
                     Depends: libcanberra-gtk3-0:i386 (>= 0.25) but it is not installable
                     Depends: libdiscid0:i386 (>= 0.2.2) but it is not installable
                     Depends: libgconf-2-4:i386 (>= 2.31.1) but it is not installable
                     Depends: libgstreamer-plugins-base1.0-0:i386 (>= 1.0.0) but it is not installable
                     Depends: libgstreamer1.0-0:i386 (>= 1.0.0) but it is not installable
                     Depends: libgtk-3-0:i386 (>= 3.0.0) but it is not installable
                     Depends: libmusicbrainz5-0:i386 but it is not going to be installed
                     Depends: libpango1.0-0:i386 (>= 1.14.0) but it is not installable
                     Depends: gstreamer1.0-plugins-base:i386 but it is not installable
                     Depends: gstreamer1.0-plugins-good:i386 but it is not installable
E: Unable to correct problems, you have held broken packages.

```
so i try this
```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I've unchecked extra repositories i've had. My /etc/apt/sources.list now looks like this

```
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted
deb-src http://archive.ubuntu.com/ubuntu raring main restricted universe #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring multiverse restricted main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ raring multiverse
deb http://us.archive.ubuntu.com/ubuntu/ raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu raring-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu raring-security multiverse restricted main universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu raring partner
deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main
```

I ran sudo apt-get update, then sudo  apt-get  install sound-juicer and had no change. Using synaptic manager's fix broken packages button doesn't help either.

---

### Post by ibjsb4 on 2013-09-07
Synaptic should show any broken packages (Custom Filters>Broken).

What do you have in /etc/apt/sources.list.d ?

---

### Post by kiddykoff on 2013-09-07
yeah, synaptic doesn't show any broken packages

i have various files in that folder

ehoover-compholio-raring.list
ehoover-compholio-raring.list.save
google-chrome.list.save
google-chrome.list.save
opera.list
opera.list.save
private-ppa.launchpad.net_commerical-ppauploaders_master-pdef-editor_ubuntu.list
private-ppa.launchpad.net_commerical-ppauploaders_master-pdef-editor_ubuntu.list.save
steam.list
steam.list.save

---

### Post by ibjsb4 on 2013-09-08
It could be a ppa causing this problem.

You could temporary disable your ppa's in "Software Sources>Other Software" by unchecking them and then try to install sound-juicer.

---

### Post by ian-weisser on 2013-09-08
> **kiddykoff said:**
> ```

The following packages have unmet dependencies:
 sound-juicer:i386 : Depends: libatk1.0-0:i386 (>= 1.12.4) but it is not installable
                     Depends: libbrasero-media3-1:i386 (>= 2.91.91) but it is not installable
                     Depends: libcanberra-gtk3-0:i386 (>= 0.25) but it is not installable
                     Depends: libdiscid0:i386 (>= 0.2.2) but it is not installable
                     Depends: libgconf-2-4:i386 (>= 2.31.1) but it is not installable
                     Depends: libgstreamer-plugins-base1.0-0:i386 (>= 1.0.0) but it is not installable
                     Depends: libgstreamer1.0-0:i386 (>= 1.0.0) but it is not installable
                     Depends: libgtk-3-0:i386 (>= 3.0.0) but it is not installable
                     Depends: libmusicbrainz5-0:i386 but it is not going to be installed
                     Depends: libpango1.0-0:i386 (>= 1.14.0) but it is not installable
                     Depends: gstreamer1.0-plugins-base:i386 but it is not installable
                     Depends: gstreamer1.0-plugins-good:i386 but it is not installable

```

All of those packages have ":i386" appended. Usually, that means you have multiarch installed.
You may have those packages already installed, but not the i386 version.
Is there a reason you have specified the i386 version of sound-juicer? Other architectures are available.
What arch are you running? i386? amd64? armhf? powerpc? other?

---

### Post by kiddykoff on 2013-09-08
> **ibjsb4 said:**
> It could be a ppa causing this problem.

You could temporary disable your ppa's in "Software Sources>Other Software" by unchecking them and then try to install sound-juicer.

I've already unchecked those. The only ones i have checked are: Canonical Partners, Canonical Partners (source), Independent, and Independent (Source Code)
For all of those ppas Canonical or Ubuntu are the host, so they are supported and shouldn't be the cause of my problems.

---

### Post by kiddykoff on 2013-09-08
> **ian-weisser said:**
> All of those packages have ":i386" appended. Usually, that means you have multiarch installed.
You may have those packages already installed, but not the i386 version.
Is there a reason you have specified the i386 version of sound-juicer? Other architectures are available.
What arch are you running? i386? amd64? armhf? powerpc? other?

I haven't tried to specify any version over another, but here is what i'm running it is 64 bit

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring

```

---

### Post by kiddykoff on 2013-09-19
well, I'm just going to do a fresh install when saucy comes out next month. I won't be calling myself an expert in Linux anytime soon.

---

### Post by ian-weisser on 2013-09-19
Fair warning: You may wind up doing the same thing to your reinstalled system. It's not a mysterious one-time system error - you *told* the system to install multiarch for some purpose (skype, netflix, steam, PPAs, something else.)

---

