---
title: "Wine Install Issues (Hoary 5.04)"
date: 2005-07-14
forum: General Help
---

### Post by cagey cretin on 2005-07-14
So I want to install wine. Wouldn't it indeed be cool?

Tried installing wine, but it needs flex and bison.

Tried installing flex, but it needs m4. m4 needs texi2html. texi2html needs perl (I have it) and suggests latex2html. latex2html needs 5 items, one of which I have (perl). So I skip trying latex2html. That means I work backwards starting with texi2html.

```

joe@ubuntu:~/Desktop/texi2html-1.66$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for perl... /usr/bin/env perl
checking for makeinfo... no
checking for install-info... /usr/sbin/install-info
checking for texi2dvi... no
checking for dvips... no
checking for ps2pdf... /usr/bin/ps2pdf
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
config.status: creating texi2html.1
config.status: creating texi2html
config.status: creating doc/Makefile
joe@ubuntu:~/Desktop/texi2html-1.66$ sudo make check
Making check in doc
make[1]: Entering directory `/home/joe/Desktop/texi2html-1.66/doc'
cd . \
  &&    \
       `echo texi2html.texi | sed 's,.*/,,'`
/bin/sh: texi2html.texi: command not found
make[1]: *** [texi2html.info] Error 127
make[1]: Leaving directory `/home/joe/Desktop/texi2html-1.66/doc'
make: *** [check-recursive] Error 1
joe@ubuntu:~/Desktop/texi2html-1.66$ sudo make install
Making install in doc
make[1]: Entering directory `/home/joe/Desktop/texi2html-1.66/doc'
cd . \
  &&    \
       `echo texi2html.texi | sed 's,.*/,,'`
/bin/sh: texi2html.texi: command not found
make[1]: *** [texi2html.info] Error 127
make[1]: Leaving directory `/home/joe/Desktop/texi2html-1.66/doc'
make: *** [install-recursive] Error 1
joe@ubuntu:~/Desktop/texi2html-1.66$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets ${MAKE}... yes
checking for perl... /usr/bin/env perl
checking for makeinfo... no
checking for install-info... /usr/sbin/install-info
checking for texi2dvi... no
checking for dvips... no
checking for ps2pdf... /usr/bin/ps2pdf
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
config.status: creating texi2html.1
config.status: creating texi2html
config.status: creating doc/Makefile
joe@ubuntu:~/Desktop/texi2html-1.66$ sudo make
Making all in doc
make[1]: Entering directory `/home/joe/Desktop/texi2html-1.66/doc'
cd . \
  &&    \
       `echo texi2html.texi | sed 's,.*/,,'`
/bin/sh: texi2html.texi: command not found
make[1]: *** [texi2html.info] Error 127
make[1]: Leaving directory `/home/joe/Desktop/texi2html-1.66/doc'
make: *** [all-recursive] Error 1
joe@ubuntu:~/Desktop/texi2html-1.66$ sudo make check
Making check in doc
make[1]: Entering directory `/home/joe/Desktop/texi2html-1.66/doc'
cd . \
  &&    \
       `echo texi2html.texi | sed 's,.*/,,'`
/bin/sh: texi2html.texi: command not found
make[1]: *** [texi2html.info] Error 127
make[1]: Leaving directory `/home/joe/Desktop/texi2html-1.66/doc'
make: *** [check-recursive] Error 1
joe@ubuntu:~/Desktop/texi2html-1.66$ sudo make install
Making install in doc
make[1]: Entering directory `/home/joe/Desktop/texi2html-1.66/doc'
cd . \
  &&    \
       `echo texi2html.texi | sed 's,.*/,,'`
/bin/sh: texi2html.texi: command not found
make[1]: *** [texi2html.info] Error 127
make[1]: Leaving directory `/home/joe/Desktop/texi2html-1.66/doc'
make: *** [install-recursive] Error 1
joe@ubuntu:~/Desktop/texi2html-1.66$

```
 
OK....So I tried just installing flex, then bison, then apt-get wine. I get it, but can't find the winecfg anywhere. The instructions say to copy it from another folder, but the file is nowhere in the filesystem.

Looks broken to me. :-(

I was so glad to see a distro that could:

1) List my windows and other linux partitions listed in grub (with me having to re-write the grub.conf file)
2) Recognize my wireless nic (ibm/atheros/phillips 5211 minipci a/b/g)

Unless someone can point me in the right direction, I guess I'll still be using my windows partition for applications not already in the pipeline, which is kinda sad...

Regards to all,

cc

---

### Post by Dogmeat on 2005-07-14
Holy shit man you just came back to this forum after a first degree contact with the dreadful dependency hell!

The same apt-get is in charge of leaving just bad memories... something's wrong! I installed with one command: apt-get wine

Maybe you didn't update your sources.list? make a backup of your own, and add the backports from ubuntuguide.org.... or just try mine:

/etc/apt/sources.list
```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330)]/ hoary main restricted

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

## Slow Backports
#deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-backports main universe multiverse restricted
#deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-backports-staging main universe multiverse restricted
#deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-extras main universe multiverse restricted
#deb http://public.planetmirror.com/pub/ubuntu-backports/ hoary-extras-staging main universe multiverse restricted

#deb http://acm.cs.umn.edu/ubp/ hoary-backports main universe multiverse restricted
#deb http://acm.cs.umn.edu/ubp/ hoary-extras main universe multiverse restricted
## Average Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

## Fast Backports (down)
#deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
#deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted

## Marillat
deb ftp://ftp.nerim.net/debian-marillat testing main

deb http://br.archive.ubuntu.com/ubuntu/ hoary main restricted
deb-src http://br.archive.ubuntu.com/ubuntu/ hoary main restricted
```

Some of the commented ones were down last I checked, but feel free to tamper if it still doesnt work  ;-)

---

### Post by cagey cretin on 2005-07-14
Thanks for answering Dogmeat. :) I went ahead and used your sources.list, because I had failures when I ran it with mine. I still had errors even with your sources.list:
```
joe@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Preview%20i386%20Binary-1%20(20050330)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Preview%20i386%20Binary-1%20(20050330)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://br.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/br.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://br.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/br.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Preview%20i386%20Binary-1%20(20050330)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Preview%20i386%20Binary-1%20(20050330)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://br.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/br.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://br.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/br.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package wine has no installation candidate

```

No installation candidate? Ouch!

---

### Post by Dogmeat on 2005-07-15
I forgot to tell, you must run apt-get update after replacing your sources.list   :-P

---

### Post by Muk on 2005-07-15
Gosh thx for the source files. it was a pain trying to compile wine from scratch >.<  ](*,)

---

### Post by cagey cretin on 2005-07-16
[QUOTE=Dogmeat]I forgot to tell, you must run apt-get update after replacing your sources.list   :-P[/QUOTE]

Thanks Dogmeat. :-)

(two OS installs later)

I appreciate you taking the time to write. I think I have installed correctly. Now I will work on installing using wine.

Thanks again,

cc

---

### Post by SpEcIeS on 2005-07-18
No problems here with regards to installing the latest wine, however trying to install internet explorer does not seem to work. I have tried several methods and they all fail, or better yet stick at 47%. <- Winetools   :?

---

