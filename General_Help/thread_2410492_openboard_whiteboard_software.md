---
title: "openboard whiteboard software"
date: 2019-01-16
forum: General Help
---

### Post by pkoukoulis-r on 2019-01-16
I am trying to install an open source whiteboard software, openboard, on 64 bit Ubuntu 18.04 LTS.
I hope to use the software for teaching purposes.

After [downloading]("http://openboard.ch/download.en.html") I attempted the install as follows:

```
$ sudo dpkg -i openboard_ubuntu_16.04_1.5.1_amd64.deb(Reading database ... 334060 files and directories currently installed.)
Preparing to unpack openboard_ubuntu_16.04_1.5.1_amd64.deb ...
Unpacking openboard (1.5.1) over (1.5.1) ...
dpkg: dependency problems prevent configuration of openboard:
 openboard depends on libavformat-ffmpeg56 (>= 7:2.8.15); however:
  Package libavformat-ffmpeg56 is not installed.
 openboard depends on libavcodec-ffmpeg56 (>= 7:2.8.15) | libavcodec-ffmpeg-extra56 (>= 7:2.8.15); however:
  Package libavcodec-ffmpeg56 is not installed.
  Package libavcodec-ffmpeg-extra56 is not installed.
 openboard depends on libswresample-ffmpeg1 (>= 7:2.8.15); however:
  Package libswresample-ffmpeg1 is not installed.
 openboard depends on libswscale-ffmpeg3 (>= 7:2.8.15); however:
  Package libswscale-ffmpeg3 is not installed.
 openboard depends on libavutil-ffmpeg54 (>= 7:2.8.15); however:
  Package libavutil-ffmpeg54 is not installed.
 openboard depends on onboard; however:
  Package onboard is not installed.
 openboard depends on libqt5multimedia5-plugins; however:
  Package libqt5multimedia5-plugins is not installed.


dpkg: error processing package openboard (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.60ubuntu1) ...
Errors were encountered while processing:
 openboard

```

Could somebody help me with getting it installed?
Thanks

---

### Post by Holger_Gehrke on 2019-01-16
'dpkg' can only install a package if all the dependencies are satisfied. To install a package and it's dependencies use 'apt install path-and-package-file-name' (to install a package located in the current working directory give a path of './'; if there's no path, 'apt' assumes you want to install a package from the repositories and won't even look for local files). But even this won't work. The package is meant for Ubuntu 16.04 and the packages it depends on do not exist in 18.04 (they have either been renamed or replaced with newer versions with a new naming scheme). The only alternative I see is to either use a system running Ubuntu 16.04 or to compile the program from source ...

Edit: with a bit more searching I found a snap, but this seems to be broken (the snap-file is all of 8kb ...); there's a long(-ish) [discussion]("https://github.com/OpenBoard-org/OpenBoard/issues/138#issuecomment-406240747") on the github issue-tracker about the need for a package for 18.04; there's several scripts and a flatpak linked.

Holger

---

### Post by pkoukoulis-r on 2019-01-16
thanks for the link.
I've tried the [download]("http://max.educa.madrid.org/max10/pool/main/o/openboard/") for 18.04 using both methods, but both do not work:

```

$ ls -ltr openboard_1.4.1-0max6_amd64.deb
-rw-rw-r-- 1 xxxxyyyy xxxxyyyy 1885784 Jan 16 14:52 openboard_1.4.1-0max6_amd64.deb
$ sudo apt install ./openboard_1.4.1-0max6_amd64.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies.
 openboard : Depends: openboard-common (>= 1:1.4.1-0max6) but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

```

$ sudo dpkg -i openboard_1.4.1-0max6_amd64.deb
(Reading database ... 334060 files and directories currently installed.)
Preparing to unpack openboard_1.4.1-0max6_amd64.deb ...
Unpacking openboard (1:1.4.1-0max6) over (1.5.1) ...
dpkg: dependency problems prevent configuration of openboard:
 openboard depends on openboard-common (>= 1:1.4.1-0max6); however:
  Package openboard-common is not installed.


dpkg: error processing package openboard (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.60ubuntu1) ...
Errors were encountered while processing:
 openboard

```

---

### Post by pkoukoulis-r on 2019-01-16
I tried the [flatpak]("https://flathub.org/apps/details/ch.openboard.OpenBoard") build for this software as well, but that does not work either.

Firstly, flatpak does not install:

```

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.1 LTS
Release:	18.04
Codename:	bionic
$ sudo add-apt-repository ppa:alexlarsson/flatpak
..
..
$ sudo apt update
..
..
$ sudo apt install flatpak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies.
 flatpak : Depends: libostree-1-1 (>= 2018.6) but it is not going to be installed
           Recommends: xdg-desktop-portal
           Recommends: xdg-desktop-portal-gtk or
                       xdg-desktop-portal-backend
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

---

### Post by Holger_Gehrke on 2019-01-16
Can't say much about the .deb files from Madrid Linux, since I haven't tried them (yet). But I have managed to install and run the flatpak. I didn't use the "official" PPA, I used the older flatpak in the Ubuntu repositories. You can use 'sudo add-apt-repository --remove ppa:alexlarsson/flatpak' to get rid of that ppa; after a short look at the ppa I think they are in the middle of updating it and something there is in an inconsistent state.

What I did:
```

sudo apt install flatpak
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install https://flathub.org/repo/appstream/ch.openboard.OpenBoard.flatpakref
flatpak run ch.openboard.OpenBoard 

```
The last line starts OpenBoard. I haven't done much with it beyond checking that it runs.

Holger

---

### Post by pkoukoulis-r on 2019-01-16
Many thanks. Finally got it installed.:)

I had to do this $ [FONT=courier new]sudo apt --fix-broken install[/FONT]  first, since flatpak would not install otherwise, before running what you specified.

Cheers

---

### Post by Holger_Gehrke on 2019-01-16
And just in case you get any problems with the flatpak version: the Madrid Linux version works ... but there's **two** .deb files and they both need to be installed. Download them both and install openboard-common_1.4.1-0max6_all.deb before openboard_1.4.1-0max6_amd64.deb .

Holger

---

### Post by varishtsg on 2019-02-06
> **Holger_Gehrke said:**
> And just in case you get any problems with the flatpak version: the Madrid Linux version works ... but there's **two** .deb files and they both need to be installed. Download them both and install openboard-common_1.4.1-0max6_all.deb before openboard_1.4.1-0max6_amd64.deb .

Holger

The deb version you linked installed fine. The only issue I face is that I'm not able to quit the application. I always have to force quit the app. Any solution to that.

---

### Post by Holger_Gehrke on 2019-02-06
Openboard uses a rather ... unusual ... layout. There's a menu opened by the rightmost item in the toolbar which has "Quit" as it's last item. The (windows typical) key combination alt-f4 also works.

Holger

---

