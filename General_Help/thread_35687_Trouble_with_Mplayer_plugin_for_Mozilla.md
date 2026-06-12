---
title: "Trouble with Mplayer plugin for Mozilla"
date: 2005-05-19
forum: General Help
---

### Post by Nick Post on 2005-05-19
Yeah, it's repositories agian.  Here's the instructions from Ubuntu Starter Guide

> sudo apt-get -t hoary install mplayer-386
sudo apt-get -t hoary install mplayer-fonts
sudo apt-get -t hoary install mozilla-mplayer
sudo cp /etc/mplayer/mplayer.conf /etc/mplayer/mplayer.conf_backup
sudo gedit /etc/mplayer/mplayer.conf

Here's the responses I get (and yes, I just entered them in even though I knew it wouldn't work, just to show)

> mark@postagulous:~$ sudo apt-get -t hoary install mplayer-386
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-386: Depends: libavcodeccvs (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
               Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
               Depends: xmms (>= 1.2.10+cvs20050209) but 1.2.10-2ubuntu1 is to be installed
E: Broken packages
mark@postagulous:~$ sudo apt-get -t hoary install mplayer-fonts
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-fonts: Depends: mplayer
E: Broken packages
mark@postagulous:~$ sudo apt-get -t hoary install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mozilla-mplayer
mark@postagulous:~$ sudo cp /etc/mplayer/mplayer.conf /etc/mplayer/mplayer.conf_backup
cp: cannot stat `/etc/mplayer/mplayer.conf': No such file or directory
mark@postagulous:~$



And here are my current repositories:

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

# From the Ubuntu howcome page, these are the backport repositories, like
# for mp3 decoders and other greyware
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

# From help  at ubuntuforums
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

# From the breakmyUbuntu (so, risky eh) page
#deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free

So, where are the libs I'm looking for?  Anyone?

---

### Post by harryc on 2005-05-19
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

---

### Post by Nick Post on 2005-05-20
[QUOTE=harryc]deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse[/QUOTE]

Thanks, you're a saint.

---

### Post by harryc on 2005-05-20
[QUOTE=Nick Post]Thanks, you're a saint.[/QUOTE]Not really ;)...but I'm glad it worked for you.

---

### Post by bobby555 on 2005-06-12
I already have those repositories added, and for me it still doesn't work. I get the messages about dependencies not working out, and I'm not sure what it means or what I should do..

AM

---

