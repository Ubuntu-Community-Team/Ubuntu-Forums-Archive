---
title: "Hoary final : gnome-alsamixer disapeared?"
date: 2005-04-09
forum: General Help
---

### Post by IdoMcFly on 2005-04-09
I've just done a clean install of hoary in order to do a clean partionning while getting rid of Windows. I was using preview and RC and there was a package named gnome-alsamixer in universe. I can't find it anymore.

My sources.list :
```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://fr.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://fr.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://fr.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://fr.archive.ubuntu.com/ubuntu hoary universe
deb-src http://fr.archive.ubuntu.com/ubuntu hoary universe

deb http://fr.archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://fr.archive.ubuntu.com/ubuntu hoary multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

#deb ftp://ftp.nerim.net/debian-marillat/ testing main

# deb http://ubuntu.tower-net.de/ubuntu/ hoary java
deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted
#deb http://backports.ubuntuforums.org/backports hoary-backports-staging main universe multiverse restricted

```

---

### Post by p!=f on 2005-04-09
Looks like it was removed from some reason or merged with another package.
gnome-applets package contain a mixer, there's also alsamixer, gamix, aumix, ...
If you want to run gnome-alsamixer you may try to install it from here:
[http://packages.debian.org/unstable/gnome/gnome-alsamixer](http://packages.debian.org/unstable/gnome/gnome-alsamixer)

edit: I installed gnome-alsamixer from Debian Sid and it works fine

---

### Post by IdoMcFly on 2005-04-09
[QUOTE=p!=f]Looks like it was removed from some reason or merged with another package.
gnome-applets package contain a mixer, there's also alsamixer, gamix, aumix, ...
If you want to run gnome-alsamixer you may try to install it from here:
[http://packages.debian.org/unstable/gnome/gnome-alsamixer](http://packages.debian.org/unstable/gnome/gnome-alsamixer)

edit: I installed gnome-alsamixer from Debian Sid and it works fine[/QUOTE]
 strange :/ thank you anyway, I've done as you did.

---

### Post by darrenadams on 2005-04-09
Hmm,

It may be a little late (seeing that you've tracked down and installed gnome-alsamixer), but the volume control program that comes with the gnome-media package can also control ALSA devices. You'd need to select the ALSA device first (File -> Change Device -> (list of devices), then decide on the what you want to control (using the preferences window).

In my experience it performs the same functions as gnome-alsamixer did. But if you're more comfortable with that...

---

### Post by filemanager on 2005-07-12
[QUOTE=p!=f]Looks like it was removed from some reason or merged with another package.
gnome-applets package contain a mixer, there's also alsamixer, gamix, aumix, ...
If you want to run gnome-alsamixer you may try to install it from here:
[http://packages.debian.org/unstable/gnome/gnome-alsamixer](http://packages.debian.org/unstable/gnome/gnome-alsamixer)

edit: I installed gnome-alsamixer from Debian Sid and it works fine[/QUOTE]
 Why is that package deemed "unstable"?

---

