---
title: "Repository Sources Recommendations"
date: 2008-01-01
forum: General Help
---

### Post by Officer Dibble on 2008-01-01
Would it help to have a list of Recommended Repository Resources? Or... doesn't it work like that?

It's just that I like to browse through the apps list now and again and wonder if there was anything I was missing out on because of not having some of the more fruitful lists some of you may have. :)

---

### Post by taurus on 2008-01-01
The only extra one that you need besides those already in /etc/apt/sources.list is this, [http://medibuntu.org/](http://medibuntu.org/).

But of you want to look around for all the packages, then have fun.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by ~LoKe on 2008-01-01
I've used Medibuntu and Trevino's repositories.  Medibuntu has all the codecs you need, and Trevino's repository has a lot of random stuff (most notable AWN and Compiz).  

Here are some: (some of them may be outdated and/or not work at all.  They're all Feisty, but should work in Gutsy)

>  # Bleeding edge wine packages
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

# The Opera browser (packages) (GPG key: 6A423791)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

## Google picasa packages (GPG key: 7FAC5991 - missing)
#deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

# Medibuntu (Multimedia, Entertainment & Distraction In Ubuntu - ex Penguin Liberation Front)
# GPG key-file: [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

# MythTV Repository for Ubuntu Linux (GPG key: 80DF6D58)
deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) feisty all
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) feisty all

# Skype packages
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## lprod packages: many audio/video apps: avidemux, cinelerra&#8230;
#deb [http://lprod.org/deb/feisty/](http://lprod.org/deb/feisty/) ./
#deb-src [http://lprod.org/deb/feisty/](http://lprod.org/deb/feisty/) ./

## BMPx feisty Repository
## GPG key-file: [http://files.beep-media-player.org/packages/bmp-packages.pubkey](http://files.beep-media-player.org/packages/bmp-packages.pubkey)
#deb [http://files.beep-media-player.org/packages/ubuntu](http://files.beep-media-player.org/packages/ubuntu) feisty main testing
#deb-src [http://files.beep-media-player.org/packages/ubuntu](http://files.beep-media-player.org/packages/ubuntu) feisty main testing

# Morgoth Repository (GPG key: 7E2E4741)
# Provides Monkey&#8217;s Audio, xmms pugins, vlc plugins, gqview, audacius, audacity&#8230;
# GPG key-file: [http://morgoth.free.fr/files/morgoth-signkey.gpg.asc](http://morgoth.free.fr/files/morgoth-signkey.gpg.asc)
deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main
deb-src [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) feisty-backports main

## ATi & nVidia drivers Ubuntu packages
## GPG key: [http://albertomilone.com/drivers/tseliot.asc](http://albertomilone.com/drivers/tseliot.asc)
#deb [http://www.albertomilone.com/drivers/feisty/latest/32bit](http://www.albertomilone.com/drivers/feisty/latest/32bit) binary/

# Automatix repository (GPG key: E23C5FC3)
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

## Firefox 3.0 alpha builds for feisty (unstable)
#deb [http://gnomefreak.youmortals.com/mozilla-testing](http://gnomefreak.youmortals.com/mozilla-testing) feisty main
#deb-src [http://gnomefreak.youmortals.com/mozilla-testing](http://gnomefreak.youmortals.com/mozilla-testing) feisty main

## Swiftfox (enhanced Firefox for linux) packages
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

# Treviño&#8217;s Ubuntu Feisty Fawn Repository (GPG key: 81836EBF - DD800CD9)
# Many "random" bleeding edge software: aMule, aMSN, Mercury, flash&#8230;
# Further informations and complete packages list: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org)
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0

# Treviño&#8217;s Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, compiz and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs&#8230;
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

---

