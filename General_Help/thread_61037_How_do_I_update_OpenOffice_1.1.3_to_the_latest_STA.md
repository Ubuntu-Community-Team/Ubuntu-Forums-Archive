---
title: "How do I update OpenOffice 1.1.3 to the latest STABLE version?"
date: 2005-08-30
forum: General Help
---

### Post by kayas80 on 2005-08-30
Hi

I was wondering if someone could please let me know how I can update version 1.1.3 of OpenOffice to the latest stable version. I don't want to update to the Beta version - I prefer stability over bleeding edge. BTW what version is the latest stable release?

Do I need to add extra repositries to my sources.list???

Thanks in advance

Oliver

---

### Post by ispmarin on 2005-08-30
I think that you can do a 
apt-get -t stable install <package>
This should install the stable version of any package.

Hope it helps, this is a guess... it works for the unstable.

Ivan

---

### Post by Lambert on 2005-08-30
the latest stable version is 1.1.4. 

You'll want to check your sources.lst and look for open office in the repositories to see what the latest version is there.

If it's not in the repositories you can look for a .deb package and download and install via dpkg. 

Here's some reading.

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

from a terminal window do 

```
man dpkg
``` 

this will give you information on how to use dpkg if you download a package outside of the repository.

you can also google search for dpkg and open office for more information.

---

### Post by kayas80 on 2005-08-30
[QUOTE=Lambert]You'll want to check your sources.lst and look for open office in the repositories to see what the latest version is there.
[/QUOTE]

Here is my currect sources.list. Could you please let me know what needs adding to get the latest stable version.

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## Staging Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

## Bibus
deb [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./
deb-src [http://switch.dl.sourceforge.net/sourceforge/bibus-biblio](http://switch.dl.sourceforge.net/sourceforge/bibus-biblio) ./

---

### Post by manicka on 2005-08-30
The latest beta is very stable. I've been using for production for quite a while and haven't had a single isssue for at least a month.

The latest release includes some debs which work beautifully. I got them here

[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/)

---

### Post by kayas80 on 2005-08-30
[QUOTE=manicka]The latest beta is very stable. I've been using for production for quite a while and haven't had a single isssue for at least a month.

The latest release includes some debs which work beautifully. I got them here

[ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/](ftp://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/SRC680_m125/Build-1/)[/QUOTE]


I'm only new to linux/ubuntu and am not that sure about debs. Can't I just add the required repositries and type apt-get update to get the latest stable version?

---

