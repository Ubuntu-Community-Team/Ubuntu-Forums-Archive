---
title: "I Broke Update Manager - &quot;Broken Count&quot;"
date: 2007-07-30
forum: General Help
---

### Post by mjpatey on 2007-07-30
I just tried installing Compiz Fusion using this tutorial:

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

When I tried to run Compiz Fusion, it reported an error, saying the virtual package, "compiz," was not installed, and that it couldn't be installed.  The Update Manager tray icon reported "Error: BrokenCount > 0" so I ran sudo apt-get install -f... with the following results:

> $ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  qt4-doc libcaca-dev libaudio-dev libexiv2-0.12 libqt4-qt3support
  libxmu-headers libart2 libdirectfb-extra gdk-imlib1 libogg-dev libcucul-dev
  libsqlite0-dev libdirectfb-dev qt4-dev-tools libxt-dev libxmu-dev
  libasound2-dev imlib-base liblcms1-dev libpq-dev libslang2-dev gdk-imlib11
  libncurses5-dev libartsc0-dev libmng-dev libvorbis-dev libaa1-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B/170kB of archives.
After unpacking 1323kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 181921 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any idea what I need to do now?  Update Manager still reports what it reported before.  I don't care too much about compiz-fusion at this point; just trying to get the Update Manager working again!

Thanks for any help you may have.

-Mark

---

### Post by scapalexis888 on 2007-07-30
I would suggest taking a note of all the packages that caused errors, go into synaptic and completely remove all of them. Then follow this guide:

[http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz-fushion+howto](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz-fushion+howto)

This one is the "official" ubuntu-forum feisty fawn version. (I assume you are using feisty fawn?)

Also, what video card and how much RAM are you using? maybe that is the problem.

---

### Post by mjpatey on 2007-07-30
1.5 GB RAM, GeForce 6200 card with 256 MB video RAM, so that's not the problem.  I've also been able to run the built-in "Desktop Effects" of Feisty, as well as a Beryl install with great results... just hoping to check out some of the new plug-ins that compiz-fusion is offering.

Hmmm... tried uninstalling everything that caused an error, but ended up in some sort of dependency loop.  Here's a snippet of what happened:

> ~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  qt4-doc libcaca-dev libaudio-dev libexiv2-0.12 libqt4-qt3support
  libxmu-headers libart2 libdirectfb-extra gdk-imlib1 libogg-dev libcucul-dev
  libsqlite0-dev libdirectfb-dev qt4-dev-tools libxt-dev libxmu-dev
  libasound2-dev imlib-base liblcms1-dev libpq-dev libslang2-dev gdk-imlib11
  libncurses5-dev libartsc0-dev libmng-dev libvorbis-dev libaa1-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B/170kB of archives.
After unpacking 1323kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 181921 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mjpatey@shekk-o-tronix:~$ sudo apt-get remove compiz-gnome
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mjpatey@shekk-o-tronix:~$ sudo apt-get remove compiz-decorator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz-decorator is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mjpatey@shekk-o-tronix:~$ sudo apt-get remove compiz-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz-gtk is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mjpatey@shekk-o-tronix:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mjpatey@shekk-o-tronix:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  qt4-doc libcaca-dev libaudio-dev libexiv2-0.12 libqt4-qt3support
  libxmu-headers libart2 libdirectfb-extra gdk-imlib1 libogg-dev libcucul-dev
  libsqlite0-dev libdirectfb-dev qt4-dev-tools libxt-dev libxmu-dev
  libasound2-dev imlib-base liblcms1-dev libpq-dev libslang2-dev gdk-imlib11
  libncurses5-dev libartsc0-dev libmng-dev libvorbis-dev libaa1-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 0B/170kB of archives.
After unpacking 1323kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 181921 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mjpatey@shekk-o-tronix:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not installed
E: Unmet dependencies. Try using -f.
mjpatey@shekk-o-tronix:~$ sudo apt-get install -f compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mjpatey@shekk-o-tronix:~$ sudo apt-get -f install compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Sorry for the long terminal paste, but hoping this will; shed some light for someone!

Thanks again,

-Mark

---

