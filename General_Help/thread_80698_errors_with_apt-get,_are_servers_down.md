---
title: "errors with apt-get, are servers down?"
date: 2005-10-22
forum: General Help
---

### Post by thewax on 2005-10-22
hello, im having lots of errors when using apt for example when i search for "nvidia" i get:

wim@ubuntu:~$ apt-cache search nvidia
linux-restricted-modules-2.6.12-9-386 - Non-free Linux 2.6.12 modules on 386
xserver-xorg-driver-nv - X.Org X server -- NV driver
nvidia-glx - NVIDIA binary XFree86 4.x/X.Org driver
nvidia-kernel-common - NVIDIA binary kernel module common files
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packa ges (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_ Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted  Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe P ackages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bina ry-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse  Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packa ges (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_ Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/ma in Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_m ain_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/re stricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-upd ates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-securi ty_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy- security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-se curity_universe_binary-i386_Packages) - stat (2 No such file or directory)
wim@ubuntu:~$

i figured there must be something wrong with my sources.list so i checked these forums and eventually copy-pasted the source.list from [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)
 so now it looks like this: 

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main


what did i do wrong? im running Ubuntu Breezy 5.10
thanks in advance

---

### Post by rjwood on 2005-10-22
looks like you have some mis-spellings and such in your source list

Do you know how to fix it?

looks like you fixed it already

---

### Post by thewax on 2005-10-22
the sources.list i posted is the one that gives me all the errors :)
so no i didnt fix it :)
i find it very strange that it doesnt work because its copy-pasted exactly from [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)
thtas why i started thinking the servers may be down?

---

### Post by rjwood on 2005-10-22
here is mine:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted



## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted  
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://soulmachine.net/breezy](http://soulmachine.net/breezy) unstable/

you probably don't want the soulmachine line as it is for enlightenment e17

---

### Post by thewax on 2005-10-22
thanks, im using your sources/list now & it works.. wel partially :)
when i do apt-get update it hangs at 
99% [Connecting to security.ubuntu.com (82.211.81.138)]

and finally gives up connecting and says :
E: Some index files failed to download, they have been ignored, or old ones used instead.

so i still get some crap like:

root@ubuntu:~# apt-cache search mplayer
mga-vid-source - Kernel driver for the back-end scaler on Matrox cards (source)
acidrip - ripping and encoding DVD tool using mplayer and mencoder
libpostproc0 - Mplayer postproc shared libraries
mencoder-586 - MPlayer's Movie Encoder
mencoder-custom - MPlayer's Movie Encoder
mencoder-k6 - MPlayer's Movie Encoder
mozilla-mplayer - MPlayer-Plugin for Mozilla
mplayer-386 - The Ultimate Movie Player For Linux
mplayer-586 - The Ultimate Movie Player For Linux
mplayer-686 - transitional dummy package which can be safely removed
mplayer-custom - The Ultimate Movie Player For Linux
mplayer-doc - Documentation for mplayer
mplayer-fonts - Fonts for mplayer
mplayer-k6 - The Ultimate Movie Player For Linux
mplayer-k7 - transitional dummy package which can be safely removed
mplayer-nogui - The Ultimate Movie Player For Linux
xmms-xmmplayer - XMMS plugin that uses MPlayer to play video files
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
root@ubuntu:~#

---

### Post by drdnl on 2005-10-23
Getting the same security server errors, no idea what's causing it..

---

