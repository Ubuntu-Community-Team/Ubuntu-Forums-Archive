---
title: "Some packages in Edgy: I'm getting segmentation fault installing them"
date: 2006-11-02
forum: General Help
---

### Post by reztho on 2006-11-02
EDIT: I rebooted and all is ok... I don't know what happened. Sorry.

So I have a fresh edgy installation here, and because of the programs i compile i've gathered a super-line for installing some packages:

sudo aptitude -r -y install build-essential gcc-3.4 checkinstall libxv-dev libxvmc-dev libx11-dev libsmbclient-dev libxext-dev libasound2-dev libfreetype6-dev libxt-dev libxaw8-dev libzvbi-dev libimlib2-dev libcaca-dev libaa1-dev libgtk2.0-dev libgtk-dev libesd0-dev libsdl-dev libtheora-dev libwxgtk2.6-dev binutils-dev gettext libgtkmm-2.4-dev libglademm-2.4-dev libao-dev doxygen libspeex-dev libstk0-dev libvorbis-dev libflac-dev libmng-dev libmodplug-dev libdvdnav-dev libreadline5-dev libcurl-dev libmpcdec-dev flex libgd2-dev libfaac-dev libmad0-dev ladspa-sdk-dev liblzo-dev libcdparanoia0-dev libsvga1-dev libxxf86dga-dev libdirectfb-dev libggi2-dev libggiwmh0-dev libqt3-mt-dev qca-dev dbus-1-utils k3blibs-dev libbluetooth-dev python-wxgtk2.6 libgconf2-dev libgnomeuimm2.0-dev libmagic-dev libsdl-mixer1.2-dev libmpeg2-4-dev libfluidsynth-dev nasm libxvidcore4-dev libdts-dev libdv-dev

That's the line i used for dapper, and used in edgy too. I know now some packages changed their names or are dissappeared. But that is not the problem... the problem is many of them are making segmentation fault when installing so i have those packages broken and i can't remove them. Here is some of the packages:

Configurando libwxbase2.6-dev (2.6.3.2.1.5) ...
Segmentation fault (core dumped)

Configurando m4 (1.4.4-1) ...
Segmentation fault (core dumped)

There is many more...

I need some help here. How do i debug this?

Thanks in advance.

Here is my current /etc/apt/sources.list:

# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

# amarok 1.44
deb [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse

---

