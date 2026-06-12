---
title: "[HELP] Failed installing steam on ubuntu 20.04"
date: 2020-07-15
forum: General Help
---

### Post by john888 on 2020-07-15
Hi, All please help

I'm trying to install steam on my ubuntu 20.04. download the installer from official link [https://store.steampowered.com/about/](https://store.steampowered.com/about/) and it seemed to failed to install because of alsa package from below

"The file /lib/modules/5.4.0-39-generic/build/include/INCLUDE_VERSION_H does not exist. Please install the package with full kernel sources for your distribution or use --with-kernel=dir option to specify another directory with kernel sources (default is /lib/modules/5.4.0-39-generic/build)."

SETUP 
Ubuntu 20.04 LTS
5.4.0-39-generic Radeon HD 7730M

---

### Post by Perfect Storm on 2020-07-16
Try install it via the repositories instead, it may pull the required libs.

```
sudo apt install steam
```

---

### Post by john888 on 2020-07-16
> **Artificial Intelligence said:**
> Try install it via the repositories instead, it may pull the required libs.

```
sudo apt install steam
```

Thanks for reply, I had tried that as well same error

---

### Post by john888 on 2020-07-16
[COLOR=unset][COLOR=unset][IMG]https://i.imgur.com/ktYWkaQ.png[/IMG]

Tried to update today, I think this error goes beyond steam issue. any other subforum suggestion I could ask for help? or maybe I could post this as ubuntu bugs? if so where can I post this?
[/COLOR]
[/COLOR]

---

### Post by Perfect Storm on 2020-07-16
Please run;
```
sudo apt update && sudo apt upgrade
```

and post the output.

---

### Post by john888 on 2020-07-16
> **Artificial Intelligence said:**
> Please run;
```
sudo apt update && sudo apt upgrade
```

and post the output.

Here is the current result

Hit:1 [https://repo.steampowered.com/steam](https://repo.steampowered.com/steam) stable InRelease                     
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                      
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease                         
Hit:4 [https://repo.nordvpn.com/deb/nordvpn/debian](https://repo.nordvpn.com/deb/nordvpn/debian) stable InRelease
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease [111 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports InRelease [98,3 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security InRelease [107 kB]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main i386 Packages [138 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages [253 kB]
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main Translation-en [99,7 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 c-n-f Metadata [7.312 B]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages [128 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe i386 Packages [67,9 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe Translation-en [63,9 kB]
Fetched 1.074 kB in 5s (204 kB/s)         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
30 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 steam:i386 : Conflicts: steam-launcher but 1:1.0.0.64 is to be installed
              Conflicts: steam-launcher:i386
 steam-devices : Conflicts: steam-launcher but 1:1.0.0.64 is to be installed
                 Conflicts: steam-launcher:i386
E: Broken packages

---

### Post by Perfect Storm on 2020-07-16
Let's try from scratch.

```
sudo apt remove --purge steam-launcher steam-installer steam-devices steam steam:i386 && sudo apt autoremove
sudo apt update && sudo apt upgrade
```

By the way, have you added PPAs to your system?

---

### Post by john888 on 2020-07-16
> **Artificial Intelligence said:**
> Let's try from scratch.

```
sudo apt remove --purge steam-launcher steam-installer steam-devices steam steam:i386 && sudo apt autoremove
sudo apt update && sudo apt upgrade
```

By the way, have you added PPAs to your system?

The PPA added were:
[https://repo.nordvpn.com/deb/nordvpn/debian](https://repo.nordvpn.com/deb/nordvpn/debian) stable main
[https://repo.steampowered.com/steam/](https://repo.steampowered.com/steam/) stable steam
[https://repo.steampowered.com/steam/](https://repo.steampowered.com/steam/) stable steam (Source Code)


Hit the following when running  ```
sudo apt remove --purge steam-launcher steam-installer steam-devices steam steam:i386 && sudo apt autoremove
```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'steam-installer' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  calf-plugins gir1.2-gst-plugins-bad-1.0 gstreamer1.0-adapter-pulseeffects
  gstreamer1.0-autogain-pulseeffects gstreamer1.0-convolver-pulseeffects
  gstreamer1.0-crystalizer-pulseeffects ipset libatomic1:i386 libbsd0:i386
  libdbi-perl libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386
  libdrm-radeon1:i386 libdrm2:i386 libebur128-1 libecap3 libedit2:i386
  libelf1:i386 libev4 libevent-core-2.1-7 libexpat1:i386 libffi7:i386
  libgetdns10 libgl1:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:i386
  libglapi-mesa:i386 libglvnd0:i386 libglx-mesa0:i386 libglx0:i386 libipset13
  libllvm10:i386 libllvm9 libllvm9:i386 libpciaccess0:i386 libsensors5:i386
  libstdc++6:i386 libunbound8 libvulkan1:i386 libwayland-client0:i386
  libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386
  libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386
  libxcb-sync1:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386
  libxfixes3:i386 libxinerama1:i386 libxshmfence1:i386 libxss1:i386
  libxxf86vm1:i386 libzita-convolver3 mda-lv2 mesa-vulkan-drivers:i386
  python3-brlapi python3-louis python3-pyatspi python3-speechd
  rubberband-ladspa squid-common squid-langpack xbrlapi xsltproc zam-plugins
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  steam:i386* steam-devices* steam-launcher*
0 upgraded, 0 newly installed, 3 to remove and 29 not upgraded.
1 not fully installed or removed.
After this operation, 4.585 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 196313 files and directories currently installed.)
Removing steam:i386 (1:1.0.0.61-2ubuntu3) ...
Removing steam-devices (1:1.0.0.61-2ubuntu3) ...
Setting up alsa-driver-linuxant (1.0.23.1) ...
Building modules for the 5.4.0-40-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.54
39.log
dpkg: error processing package alsa-driver-linuxant (--configure):
 installed alsa-driver-linuxant package post-installation script subprocess retu
rned error exit status 1
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
Errors were encountered while processing:
 alsa-driver-linuxant
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Perfect Storm on 2020-07-16
Never mix Debian and Ubuntu together and keep away from PPAs as long it's possible. It will ruined your system if not careful.

You better start a new thread in "General" forum regarding your problem, as I'm not using Ubuntu anymore.

---

### Post by john888 on 2020-07-16
> **Artificial Intelligence said:**
> Never mix Debian and Ubuntu  together and keep away from PPAs as long it's possible. It will ruined  your system if not careful.

You better start a new thread in "General" forum regarding your problem, as I'm not using Ubuntu anymore.

Thanks for the suggestion. I have no choice because it is used to install nordvpn

---

### Post by wildmanne39 on 2020-07-21
*Thread moved to **General Help for a more appropriate fit**.*

---

### Post by olduse78802 on 2020-07-22
I use the direct steam installer from this page

[https://linuxconfig.org/how-to-install-steam-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-install-steam-on-ubuntu-20-04-focal-fossa-linux)

---

### Post by john888 on 2020-08-09
Hi all, thanks for the help I remove alsa package following this link [https://stackoverflow.com/questions/48431372/removing-broken-packages-in-ubuntu](https://stackoverflow.com/questions/48431372/removing-broken-packages-in-ubuntu)
and then re-install steam dependencies following this link [https://linuxconfig.org/how-to-install-steam-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-install-steam-on-ubuntu-20-04-focal-fossa-linux)

now it is up and running successfully, closing this thread

---

