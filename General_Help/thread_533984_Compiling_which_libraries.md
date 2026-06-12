---
title: "Compiling: which libraries???"
date: 2007-08-24
forum: General Help
---

### Post by z-vap on 2007-08-24
I've been an ubuntu/windows dual booter for a few months now.  I've switch my dual boot from windows primary to ubuntu primary.  Loving it.

Here's a nagging question that I've never really figured out, yet.

Many programs that anyone would need are in the repositories, but occasionally there are some that need compiled and built from source.  

I've never really had any success with configuring and compiling, but I've made some recent strides.  There is always some library that I am missing.  And it takes forever to figure out what's messed up and what needs done to correct it.  Sure, coming here is always a big help, but I'd like to better understand what the pro's do, and be a little more independent. I'd like to know that I could do this alot without feeling dependent on others.

My question is this:  When someone like me decides to attempt to build from source, what recommendations would you say are key?  Installing *build-essentials* would be first, i'd imagine.  

What else?  

Thanks
Joe

---

### Post by apetresc on 2007-08-24
> **z-vap said:**
> 
My question is this:  When someone like me decides to attempt to build from source, what recommendations would you say are key?  Installing *build-essentials* would be first, i'd imagine.  

What else?  

Thanks
Joe
Firstly, welcome to the wonderful world of Ubuntu, full-time! :)

You are right, build-essential is an absolutely essential package (pun intended!). Let me introduce you to another wonderful command, "apt-get build-dep". This command takes a package and, instead of installing the package itself, installs every library that you would need to compile that package yourself. So, for example,```
root@petrescu:~ # sudo apt-get build-dep gaim
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  dbus-1
The following NEW packages will be installed:
  cdbs comerr-dev esound-common gamin gconf2 gnome-mime-data imake
  launchpad-integration libao-dev libao2 libaspell-dev libaspell15 libatk1.0-0
  libatk1.0-dev libaudiofile-dev libaudiofile0 libbonobo2-0 libbonobo2-common
  libbonobo2-dev libcairo2 libcairo2-dev libcamel1.2-6 libcamel1.2-dev
  libdbus-1-1 libdbus-glib-1-1 libebook1.2-5 libebook1.2-dev
  libedata-book1.2-2 libedata-book1.2-dev libedataserver1.2-4
  libedataserver1.2-dev libegroupwise1.2-8 libesd0 libesd0-dev libexpat1-dev
  libfontconfig1-dev libfontenc1 libfreetype6-dev libgamin0 libgconf2-4
  libgconf2-dev libgcrypt11-dev libglib2.0-dev libgnome2-0 libgnome2-common
  libgnome2-dev libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-dev
  libgnutls11-dev libgpg-error-dev libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgtk2.0-dev libgtkspell-dev libgtkspell0 libhal-storage1 libhal1
  libhesiod0 libice-dev libidl-dev libidl0 libkadm55 libkrb5-dev
  liblaunchpad-integration-dev liblaunchpad-integration0 libltdl3 libltdl3-dev
  libnspr-dev libnspr4 libnss-dev libnss3 libopencdk8-dev liborbit2
  liborbit2-dev libpango1.0-0 libpango1.0-common libpango1.0-dev libpng12-dev
  libpopt-dev libsm-dev libsmbclient libsoup2.2-8 libstartup-notification0
  libstartup-notification0-dev libsysfs1 libtasn1-2-dev libtiff4 libx11-dev
  libxau-dev libxcursor-dev libxcursor1 libxext-dev libxfixes-dev libxfixes3
  libxft-dev libxft2 libxi-dev libxi6 libxinerama-dev libxinerama1 libxml2-dev
  libxrandr-dev libxrandr2 libxrender-dev libxrender1 libxss-dev libxss1
  libxt-dev libzephyr-dev libzephyr3 makedepend pkg-config pmount sessreg
  shared-mime-info tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev x-dev x11proto-core-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-scrnsaver-dev x11proto-xext-dev
  x11proto-xinerama-dev xcursorgen xfonts-utils xmkmf xutils zlib1g-dev
The following packages will be upgraded:
  libgnutls11 libkrb53
2 upgraded, 136 newly installed, 1 to remove and 29 not upgraded.
Need to get 31.2MB of archives.
After unpacking 117MB of additional disk space will be used.
Do you want to continue [Y/n]?

```
Yes, that's a lot of libraries ;) If the package you are trying to build from source exists in apt, even if it's a slightly different version, build-dep will pull in everything you need to compile it. If it's not, then usually when you run ./configure, it will tell you which library it's missing. To install it, usually you just need to do ```
sudo apt-get install library library-dev
``` (where "library" is the name of the library, obviously.) So if a package complained that you need GTK2+ installed, I would type ```
sudo apt-get install libgtk2.0 libgtk2.0-dev
```
Simple as that :) If you can't figure out what you need for a specific package, you can check its webpage which usually lists dependencies, or you can ask here and we'd be glad to help out out.

Good luck!

---

### Post by RedSquirrel on 2007-08-24
The 'apt-get build-dep ...' mentioned above is a lifesaver.

Here are a few more suggestions:

The source tarball usually contains the files README and INSTALL. It's a good idea to read those.

You can also look at the different options you can use with the configure script:

```
./configure -h
```or to save in a text file:

```
./configure -h > fancy_configure_options.txt
```Then just open *fancy_configure_options.txt* with your favorite text editor.

You may also be able to use **checkinstall** to make a deb. 

See:

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

