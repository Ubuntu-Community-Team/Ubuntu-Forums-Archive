---
title: "Trying to rip mp3s"
date: 2005-05-05
forum: General Help
---

### Post by ppyvras on 2005-05-05
I have liblame0 installd already and am trying to add gstreamer0.8-lame so that I can complete the required packages so that I can start encoding mp3s.  However I get the following message when installing it:

gstreamer0.8-lame:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

According to synaptic libc6 cannot be upgraded so I am stuck.  The posts I have read suggest that this can be.

My /etc/apt/sources.list looks like:

[HTML]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


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

deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted[/HTML]

and I have apt-get updated recently.  The repositories were the gb equivalents but changed to the us versions from the ubuntu starters guide.

If there is another (better) way that would be good too.

Cheers in advance for any advice.

---

### Post by Alexander Kirillov on 2005-05-05
[QUOTE=ppyvras]I have liblame0 installd already and am trying to add gstreamer0.8-lame so that I can complete the required packages so that I can start encoding mp3s.  However I get the following message when installing it:

gstreamer0.8-lame:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

According to synaptic libc6 cannot be upgraded so I am stuck.  The posts I have read suggest that this can be.

My /etc/apt/sources.list looks like:

[HTML]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


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

deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted[/HTML]

and I have apt-get updated recently.  The repositories were the gb equivalents but changed to the us versions from the ubuntu starters guide.

If there is another (better) way that would be good too.

Cheers in advance for any advice.[/QUOTE]
 I have installed gstreamer-lame 0.8.7-3.gismo from 

deb [http://luca.pca.it/debian/](http://luca.pca.it/debian/) ./
deb-src [http://luca.pca.it/debian/](http://luca.pca.it/debian/) ./

and had no dependency problems (it requires libc6 (>=2.3.2.ds1-4) )

---

### Post by ppyvras on 2005-05-05
I have added the repositories to my list but what line should I use

apt-get install gstreamer0.8-lame gives the same error as before

I have tried a load of combinations but no luck

---

### Post by jiyuu0 on 2005-05-05
[http://ubuntuguide.org/#goobox](http://ubuntuguide.org/#goobox)

---

