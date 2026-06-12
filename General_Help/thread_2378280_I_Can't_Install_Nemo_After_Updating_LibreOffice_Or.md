---
title: "I Can't Install Nemo After Updating LibreOffice Or VLC"
date: 2017-11-21
forum: General Help
---

### Post by kamrynborden on 2017-11-21
```
kamryn@UD2:~$ sudo apt install nemo
[sudo] password for kamryn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 nemo : Depends: libxapp1 but it is not installable
        Recommends: nemo-fileroller but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I can't install nemo file manager after updating either Libreoffice or VLC player.
 
 I used the PPAs:
 sudo add-apt-repository ppa:jonathonf/vlc -y
 sudo add-apt-repository ppa:libreoffice/ppa -y
 
 I reinstalled Ubuntu on my computer to fix it, because it messed up  some things, or I did. Everything went OK except I still can't install  the nemo file manager. I'm not sure which one broke it. I was able to successfully update LibreOffice and  VLC on all the other computers using these steps:
 
 VLC:
 sudo apt-get remove vlc vlc-nox && sudo apt-get autoremove
 sudo add-apt-repository ppa:jonathonf/vlc
 sudo apt update && sudo apt upgrade -y
 sudo install vlc
 
 LibreOffice:
 sudo apt-get remove libreoffice-core
 sudo apt-get remove --purge libreoffice-core
 sudo add-apt-repository ppa:libreoffice/ppa
 sudo apt update
 sudo apt install libreoffice.
 
 Maybe there is something different in the hardware on my computer?
 
 Specs
 OS: Ubuntu 16.04 x64
 Motherboard: ASUS Z97-K Rev 2.01
 Processor: Intel® Core&#8482; i3-4130 CPU @ 3.40GHz × 4
 RAM: HyperX Fury 8GB 1866MHz DDR3 (x1)
 Drive: Samsung EVO 850 250GB M.2
 
 All of the computers are set up the same software-wise, all the same software and settings.

---

### Post by vasa1 on 2017-11-21
This could provide a hint:```
E: Unable to correct problems, you have held broken packages.
```One possible cause is that one installs a ppa which pulls in packages newer or older than the system's defaults
and 
then somehow deletes that ppa without attending to the packages it pulled in or replaced

What does```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```
show?

Or, if you have *inxi* installed,```
inxi -r
```would be helpful.

---

### Post by kamrynborden on 2017-11-21
```

kamryn@UD2:~$ grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial main restricted
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-updates universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-updates multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu xenial-proposed universe main restricted multiverse
/etc/apt/sources.list.d/atareao-ubuntu-atareao-xenial.list:deb http://ppa.launchpad.net/atareao/atareao/ubuntu xenial main
/etc/apt/sources.list.d/dawidd0811-ubuntu-neofetch-xenial.list:deb http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu xenial main
/etc/apt/sources.list.d/etcher.list:deb https://dl.bintray.com/resin-io/debian stable etcher
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/jonathonf-ubuntu-vlc-xenial.list:deb http://ppa.launchpad.net/jonathonf/vlc/ubuntu xenial main
/etc/apt/sources.list.d/libreoffice-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu xenial main
/etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-xenial.list:deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
/etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/openshot.developers/ppa/ubuntu xenial main
/etc/apt/sources.list.d/transmissionbt-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu xenial main
/etc/apt/sources.list.d/webupd8team-ubuntu-java-xenial.list:deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main


```

---

### Post by kamrynborden on 2017-11-21
The weird thing was I updated it on other computers without a problem. Nemo still works on them.

---

### Post by again? on 2017-11-22
Don't know if related but nemo would not start on 17.04 after recent update.
Terminal error:
```
nemo: symbol lookup error: nemo: undefined symbol: xapp_gtk_window_set_icon_name
```
Had to purge webupd8  nemo ppa.

What is your output for
```
apt policy nemo
```
My output for 16.04 where nemo works ok.
```
glen@Xen2:~$ apt policy nemo
nemo:
  Installed: 2.8.6-2
  Candidate: 2.8.6-2
  Version table:
 *** 2.8.6-2 500
        500 http://ftp.iinet.net.au/pub/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by mc4man on 2017-11-22
From affected machine run apt policy nemo (not on machine where it is installed.
Note that in 16.04 there is no such package libxapp1 so you could also post
apt show nemo

---

### Post by kamrynborden on 2017-11-22
```

kamryn@UD2:~$ apt policy nemo
nemo:
  Installed: (none)
  Candidate: 2.8.6-2
  Version table:
     2.8.6-2 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages


```

```

kamryn@UD2:~$ apt show nemo 
Package: nemo
Version: 2.8.6-2
Priority: optional
Section: universe/misc
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Cinnamon Team <pkg-cinnamon-team@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 3,048 kB
Depends: desktop-file-utils (>= 0.7), gsettings-desktop-schemas, gvfs (>= 1.3.2), libcinnamon-desktop4 (>= 2.6.4), libglib2.0-data, libnemo-extension1 (= 2.8.6-2), nemo-data (= 2.8.6-2), shared-mime-info (>= 0.50), libatk1.0-0 (>= 1.32.0), libc6 (>= 2.14), libcairo-gobject2 (>= 1.10.0), libcairo2 (>= 1.10.0), libexempi3 (>= 2.2.0), libexif12 (>= 0.6.21-1~), libgail-3-0 (>= 3.0.0), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.41.1), libgtk-3-0 (>= 3.9.12), libnotify4 (>= 0.7.0), libpango-1.0-0 (>= 1.20.0), libpangocairo-1.0-0 (>= 1.14.0), libx11-6, libxml2 (>= 2.7.4)
Recommends: cinnamon-l10n, gvfs-backends, librsvg2-common, nemo-fileroller
Suggests: eog, evince | pdf-viewer, totem | mp3-decoder, xdg-user-dirs
Homepage: http://cinnamon.linuxmint.com/
Download-Size: 766 kB
APT-Sources: http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
Description: File manager and graphical shell for Cinnamon
 Nemo is the official file manager for the Cinnamon desktop. It allows
 to browse directories, preview files and launch applications associated
 with them. It is also responsible for handling the icons on the Cinnamon
 desktop. It works on local and remote filesystems.
 .
 Several icon themes and components for viewing different kinds of files
 are available in separate packages.

```

---

### Post by mc4man on 2017-11-22
> **kamrynborden said:**
> ```

kamryn@UD2:~$ apt policy nemo
nemo:
  Installed: (none)
  Candidate: 2.8.6-2
  Version table:
     2.8.6-2 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages


```

```

kamryn@UD2:~$ apt show nemo 
Package: nemo
Version: 2.8.6-2
Priority: optional
Section: universe/misc
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Cinnamon Team <pkg-cinnamon-team@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 3,048 kB
Depends: desktop-file-utils (>= 0.7), gsettings-desktop-schemas, gvfs (>= 1.3.2), libcinnamon-desktop4 (>= 2.6.4), libglib2.0-data, libnemo-extension1 (= 2.8.6-2), nemo-data (= 2.8.6-2), shared-mime-info (>= 0.50), libatk1.0-0 (>= 1.32.0), libc6 (>= 2.14), libcairo-gobject2 (>= 1.10.0), libcairo2 (>= 1.10.0), libexempi3 (>= 2.2.0), libexif12 (>= 0.6.21-1~), libgail-3-0 (>= 3.0.0), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.41.1), libgtk-3-0 (>= 3.9.12), libnotify4 (>= 0.7.0), libpango-1.0-0 (>= 1.20.0), libpangocairo-1.0-0 (>= 1.14.0), libx11-6, libxml2 (>= 2.7.4)
Recommends: cinnamon-l10n, gvfs-backends, librsvg2-common, nemo-fileroller
Suggests: eog, evince | pdf-viewer, totem | mp3-decoder, xdg-user-dirs
Homepage: http://cinnamon.linuxmint.com/
Download-Size: 766 kB
APT-Sources: http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
Description: File manager and graphical shell for Cinnamon
 Nemo is the official file manager for the Cinnamon desktop. It allows
 to browse directories, preview files and launch applications associated
 with them. It is also responsible for handling the icons on the Cinnamon
 desktop. It works on local and remote filesystems.
 .
 Several icon themes and components for viewing different kinds of files
 are available in separate packages.

```

I don't see libxapp1 listed as a direct dep.. Maybe try again..
Otherwise install aptitude & try installing with it. 
sudo aptitude install nemo

If it fails it will/may show a solution, answer N, if another solution is presented answer Q (quit), then copy & paste the whole mess to a post.

---

### Post by kamrynborden on 2017-11-22
It works. It went back to crashing like it used to before I installed the PPA for it, so maybe there is something wrong with the PPA?
This is the PPA I've been using:
sudo add-apt-repository ppa:webupd8team/nemo3

Update: It doesn't seem to be doing it now, maybe it was just a coincidence, it is still working.
Thank you. :)

---

### Post by mc4man on 2017-11-22
> **kamrynborden said:**
> It works. It went back to crashing like it used to before I installed the PPA for it, so maybe there is something wrong with the PPA?
This is the PPA I've been using:
sudo add-apt-repository ppa:webupd8team/nemo3

Update: It doesn't seem to be doing it now, maybe it was just a coincidence, it is still working.
Thank you. :)
while I'm currently using nemo in 18.04 (with unity) I've never tried the ppa version in 16.04. It's been patched to integrate better with unity & handle the desktop,  (instead of nautilus),  in better fashion than the Ubuntu repo nemo.
Keep in mind those ppa nemo versions are not for Ubuntu releases later than 16.04 (17.04/17.10/18.04) but could remain installed if one upgraded 16.04 to a later release.

The apt policy you last posted was only showing the Ubuntu repo version of nemo.. 2.8.6-2

---

