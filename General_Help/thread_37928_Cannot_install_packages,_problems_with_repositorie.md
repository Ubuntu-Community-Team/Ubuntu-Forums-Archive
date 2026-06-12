---
title: "Cannot install packages, problems with repositories"
date: 2005-05-29
forum: General Help
---

### Post by frj on 2005-05-29
Hi,

I noticed that Ubunto does not come with mp3 support. I googled around to find out what packages I needed. People were recommending the Ubuntuguide.org. So I alsow checked that one out.  And yes there was plenty of information.
First of all i had to add extra repositories. So I followed all the steps at ubuntuguide. 

when i ran the apt-get update i got the following messages: ```
Failed to fetch http://backports.ubuntuforums.org/ubp/dists/hoary-extras/restricted/binary-i386/Packages.gz  Could not connect to backports.ubuntuforums.org:80 (66.246.118.209). - connect (111 Connection refused)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
``` 

When iam trying to install a package with apt-get or Synaptic i get a similiar message. Why doesnt these extra repositories work?

Here is my /etc/apt/sources.list file:```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://se.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://se.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://se.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://backports.ubuntuforums.org/ubp hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/ubp hoary-extras main universe multiverse restricted

## Backports - Mirrors
# deb http://public.planetmirror.com/pub/ubuntu-backports hoary-backports main universe multiverse restricted
# deb http://public.planetmirror.com/pub/ubuntu-backports hoary-extras main universe multiverse restricted

## Marillat
deb ftp://ftp.nerim.net/debian-marillat testing main
```

---

### Post by Leif on 2005-05-29
Backports has been running into bandwidth issues, so you need to use a mirror. I use 

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

I'd give you the link, but the backports website doesn't seem to be working right now either.

---

