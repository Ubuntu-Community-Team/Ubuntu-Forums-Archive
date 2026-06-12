---
title: "Software Updater has stopped working automatically"
date: 2017-09-19
forum: General Help
---

### Post by gerryw on 2017-09-19
I am using Ubuntu 16.04.

The software updater has stopped working automatically and when I go to do it manually I get "not all updates can be installed" and advises me to "Run a partial upgrade".

But when I attempt to run the partial upgrade I get "Error authenticating some packages" and the following list:

libglapi-mesa:i386
libgles2-mesa
libosmesa6
libosmesa6:i386
libwayland-egl1-mesa
libxatracker2
mesa-vdpau-drivers
mesa-vulkan-drivers

Any help gratefully received

---

### Post by vasa1 on 2017-09-19
If you can, please open a terminal and run```
sudo apt-get update
```and post the entire output here as text between code tags.

Then, run```
sudo apt-get upgrade
```ans if the output is confusing you, press "n" at the [Y/n] prompt and post that output here as well.

The output from```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
```maybe informative as well.

---

### Post by gerryw on 2017-09-19
```
sudo apt-get update
Hit:1 [http://ubuntu.ethz.ch/ubuntu](http://ubuntu.ethz.ch/ubuntu) xenial InRelease
Hit:2 [http://ubuntu.ethz.ch/ubuntu](http://ubuntu.ethz.ch/ubuntu) xenial-updates InRelease                    
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:4 [http://ubuntu.ethz.ch/ubuntu](http://ubuntu.ethz.ch/ubuntu) xenial-backports InRelease                  
Ign:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty InRelease                     
Hit:6 [http://ubuntu.ethz.ch/ubuntu](http://ubuntu.ethz.ch/ubuntu) xenial-security InRelease                   
Get:7 [http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu) xenial InRelease [23.8 kB]
Hit:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty Release                       
Hit:10 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty InRelease       
Hit:11 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial InRelease
Hit:12 [https://packages.microsoft.com/repos/vscode](https://packages.microsoft.com/repos/vscode) stable InRelease          
Hit:13 [https://apt-mo.trafficmanager.net/repos/dotnet-release](https://apt-mo.trafficmanager.net/repos/dotnet-release) xenial InRelease
Ign:7 [http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu) xenial InRelease
Fetched 23.8 kB in 1s (14.5 kB/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu) xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9
W: The repository 'http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  glade2script libgles1-mesa libpango1.0-0 linux-headers-4.4.0-64
  linux-headers-4.4.0-64-generic linux-headers-4.4.0-66
  linux-headers-4.4.0-66-generic linux-headers-4.4.0-67
  linux-headers-4.4.0-67-generic linux-headers-4.4.0-70
  linux-headers-4.4.0-70-generic linux-headers-4.4.0-71
  linux-headers-4.4.0-71-generic linux-headers-4.4.0-72
  linux-headers-4.4.0-72-generic linux-image-4.4.0-64-generic
  linux-image-4.4.0-66-generic linux-image-4.4.0-67-generic
  linux-image-4.4.0-70-generic linux-image-4.4.0-71-generic
  linux-image-4.4.0-72-generic linux-image-extra-4.4.0-64-generic
  linux-image-extra-4.4.0-66-generic linux-image-extra-4.4.0-67-generic
  linux-image-extra-4.4.0-70-generic linux-image-extra-4.4.0-71-generic
  linux-image-extra-4.4.0-72-generic linux-signed-image-4.4.0-72-generic
  snap-confine
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  gnome-exe-thumbnailer libegl1-mesa libgbm1 libgl1-mesa-dri
  libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa
  libglapi-mesa:i386 libgles1-mesa libgles2-mesa libinput10 libmirclient9
  libosmesa6 libosmesa6:i386 libwayland-egl1-mesa libxatracker2 linux-generic
  linux-headers-generic linux-image-generic linux-signed-generic
  linux-signed-image-generic mesa-vdpau-drivers mesa-vulkan-drivers snapcraft
  snapcraft-examples
The following packages will be upgraded:
  apparmor bind9-host bluez bluez-cups bluez-obexd bzr code cups cups-bsd
  cups-client cups-common cups-core-drivers cups-daemon cups-ppdc
  cups-server-common dnsutils gir1.2-gdkpixbuf-2.0 gir1.2-packagekitglib-1.0
  google-chrome-stable libapparmor-perl libapparmor1 libbind9-140
  libbluetooth3 libcryptsetup4 libcups2 libcups2:i386 libcupscgi1
  libcupsimage2 libcupsmime1 libcupsppdc1 libdns-export162 libdns162 libgd3
  libgd3:i386 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libisc-export160
  libisc160 libisccc140 libisccfg140 libkf5archive5 liblouis-data liblouis9
  liblwres141 libpackagekit-glib2-16 libpython3.5 libpython3.5-dev
  libpython3.5-minimal libpython3.5-stdlib libqapt3 libqapt3-runtime
  libsmbclient libsnapd-glib1 libwbclient0 libxml2 libxml2:i386 libxml2-utils
  linux-firmware linux-generic-lts-wily linux-headers-generic-lts-wily
  linux-libc-dev lxd lxd-client python-bzrlib python-defusedxml python-jwt
  python-libxml2 python-samba python3-jwt python3-louis python3-update-manager
  python3.5 python3.5-dev python3.5-minimal python3.5-venv qapt-batch samba
  samba-common samba-common-bin samba-dsdb-modules samba-libs
  samba-vfs-modules smbclient snap-confine snapd snapd-login-service tcpdump
  thunderbird thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-us update-manager update-manager-core xserver-common
  xserver-xorg-core
95 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
Need to get 270 MB of archives.
After this operation, 44.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

``````
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb [http://ubuntu.ethz.ch/ubuntu/](http://ubuntu.ethz.ch/ubuntu/) xenial main restricted
/etc/apt/sources.list:deb [http://ubuntu.ethz.ch/ubuntu/](http://ubuntu.ethz.ch/ubuntu/) xenial-updates main restricted
/etc/apt/sources.list:deb [http://ubuntu.ethz.ch/ubuntu/](http://ubuntu.ethz.ch/ubuntu/) xenial universe
/etc/apt/sources.list:deb [http://ubuntu.ethz.ch/ubuntu/](http://ubuntu.ethz.ch/ubuntu/) xenial-updates universe
/etc/apt/sources.list:deb [http://ubuntu.ethz.ch/ubuntu/](http://ubuntu.ethz.ch/ubuntu/) xenial multiverse
/etc/apt/sources.list:deb [http://ubuntu.ethz.ch/ubuntu/](http://ubuntu.ethz.ch/ubuntu/) xenial-updates multiverse
/etc/apt/sources.list:deb [http://ubuntu.ethz.ch/ubuntu/](http://ubuntu.ethz.ch/ubuntu/) xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://ubuntu.ethz.ch/ubuntu/](http://ubuntu.ethz.ch/ubuntu/) xenial-security main restricted
/etc/apt/sources.list:deb [http://ubuntu.ethz.ch/ubuntu/](http://ubuntu.ethz.ch/ubuntu/) xenial-security universe
/etc/apt/sources.list:deb [http://ubuntu.ethz.ch/ubuntu/](http://ubuntu.ethz.ch/ubuntu/) xenial-security multiverse
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
/etc/apt/sources.list.d/dotnetdev.list:deb [arch=amd64] [https://apt-mo.trafficmanager.net/repos/dotnet-release/](https://apt-mo.trafficmanager.net/repos/dotnet-release/) xenial main
/etc/apt/sources.list.d/dotnetdev.list.save:deb [arch=amd64] [https://apt-mo.trafficmanager.net/repos/dotnet-release/](https://apt-mo.trafficmanager.net/repos/dotnet-release/) xenial main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/paolorotolo-android-studio-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) trusty main
/etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-updates-xenial.list:deb [http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu) xenial main
/etc/apt/sources.list.d/ubuntu-x-swat-ubuntu-updates-xenial.list.save:deb [http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu) xenial main
/etc/apt/sources.list.d/vscode.list:deb [arch=amd64] [https://packages.microsoft.com/repos/vscode](https://packages.microsoft.com/repos/vscode) stable main
/etc/apt/sources.list.d/vscode.list.save:deb [arch=amd64] [https://packages.microsoft.com/repos/vscode](https://packages.microsoft.com/repos/vscode) stable main
/etc/apt/sources.list.d/webupd8team-java-trusty.list.distUpgrade:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
/etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list:deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial main
/etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list.save:deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial main

```
I was not aware that I was root how do I turn it off?

---

### Post by vasa1 on 2017-09-19
> **gerryw said:**
> ...I was not aware that I was root how do I turn it off?
Oops! That's only my signature and not meant for you personally!

---

### Post by vasa1 on 2017-09-19
You can go into "Software Sources" and disable the troublesome ppa as well as the ones for trusty.

Then, after checking your current kernel version using```
uname -r
```you can safely run```
sudo apt autoremove
```to remove older kernels.

Once that's done, run ```
sudo apt-get update
```and```
sudo apt-get upgrade
```again and let us know.

---

### Post by gerryw on 2017-09-19
code:```

sudo apt-get update
Hit:1 [http://ubuntu.ethz.ch/ubuntu](http://ubuntu.ethz.ch/ubuntu) xenial InRelease
Hit:2 [http://ubuntu.ethz.ch/ubuntu](http://ubuntu.ethz.ch/ubuntu) xenial-updates InRelease                    
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Ign:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty InRelease                     
Hit:5 [http://ubuntu.ethz.ch/ubuntu](http://ubuntu.ethz.ch/ubuntu) xenial-backports InRelease                  
Hit:6 [http://ubuntu.ethz.ch/ubuntu](http://ubuntu.ethz.ch/ubuntu) xenial-security InRelease                   
Hit:7 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty InRelease        
Hit:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty Release                       
Hit:10 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial InRelease 
Hit:11 [https://packages.microsoft.com/repos/vscode](https://packages.microsoft.com/repos/vscode) stable InRelease          
Hit:12 [https://apt-mo.trafficmanager.net/repos/dotnet-release](https://apt-mo.trafficmanager.net/repos/dotnet-release) xenial InRelease
Reading package lists... Done 
```

for sudo apt-get upgrade I pressed Y by mistake so this is after updating doing it again

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnome-exe-thumbnailer libegl1-mesa libgbm1 libgl1-mesa-dri
  libgl1-mesa-dri:i386 libinput10 libmirclient9 libwayland-egl1-mesa
  libxatracker2 linux-generic linux-headers-generic linux-image-generic
  linux-signed-generic linux-signed-image-generic mesa-vdpau-drivers
  mesa-vulkan-drivers snapcraft snapcraft-examples
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
```

---

### Post by slickymaster on 2017-09-19
@gerryw:
Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output code. Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by gerryw on 2017-09-19
Sorry

---

### Post by vasa1 on 2017-09-19
Why did you mark your thread [SOLVED]?

---

