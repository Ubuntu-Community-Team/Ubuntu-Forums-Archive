---
title: "Missing dependencies"
date: 2005-05-25
forum: General Help
---

### Post by synaptic revolt on 2005-05-25
I'm trying to install dvd::rip, but synaptic says transcode will not be installed.
When I try to install transcode, I get

transcode:
 Depends: libavcodeccvs but it is not going to be installed
 Depends: libdvdread2  but it is not installable
 Depends: libvorbis0 (>=1.0rc3-1) but it is not installable
 Depends: libxvidcore4 but it is not going to be installed

I can keep going, and eventually it wants newer versions of libraries and such that aren't available, such as 

Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

plz help  ](*,) 

source.lst looks like so:

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


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

deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main


deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-backports main universe multiverse restricted
deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-extras main universe multiverse restricted
```

---

### Post by SGC on 2005-05-25
search and install the following packages in synaptic:
libavcodeccvs
libdvdread2
libvorbis0 
libxvidcore4

after that try to install transcode

---

### Post by synaptic revolt on 2005-05-25
[QUOTE=SGC]search and install the following packages in synaptic:
libavcodeccvs
libdvdread2
libvorbis0 
libxvidcore4

after that try to install transcode[/QUOTE]

libavcodeccvs:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
 Depends: libpostproc0 but it is not going to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
  Depends: libvorbisenc2 (>=1.1.0) but 1.0.1-1 is to be installed
 Depends: libxvidcore4 but it is not going to be installed

There is no dvdread2, but I have dvdread3 installed.
There is no libvorbis0, just libvorbis0a, which is installed.

libxvidcore4:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

---

### Post by Hep on 2005-08-23
Always the same issue ...
Can somebody fix it ?

---

