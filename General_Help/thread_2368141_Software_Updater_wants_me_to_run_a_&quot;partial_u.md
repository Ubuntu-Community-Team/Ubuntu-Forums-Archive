---
title: "Software Updater wants me to run a &quot;partial upgrade&quot;"
date: 2017-08-07
forum: General Help
---

### Post by lobosuelto on 2017-08-07
Hey guys. Ubuntu 16.04 here. My software updater popped a message that says "Not all updates can be installed, run a partial upgrade to install as many updates as possible". I've broken my OS in the past so I's rather not do it again. Hence I'm asking this question here. 

Here's what I get when I run "*sudo apt-get update && sudo apt-get dist-upgrade*":

```
the following packages were automatically installed and are no longer required:
  kde-l10n-engb libllvm3.8 libllvm3.8:i386 libmircommon5 python-support
  snap-confine ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  libgles1-mesa
The following NEW packages will be installed:
  libinput-bin libllvm4.0 libllvm4.0:i386 libsensors4:i386
  linux-headers-4.4.0-89 linux-headers-4.4.0-89-generic
  linux-image-4.4.0-89-generic linux-image-extra-4.4.0-89-generic
The following packages will be upgraded:
  gnome-software gnome-software-common libegl1-mesa libgbm1 libgl1-mesa-dev
  libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386
  libglapi-mesa libglapi-mesa:i386 libgles2-mesa libinput10 libosmesa6
  libosmesa6:i386 libwayland-egl1-mesa libxatracker2 linux-generic
  linux-headers-generic linux-image-generic mesa-common-dev mesa-vdpau-drivers
  ubuntu-software
23 upgraded, 8 newly installed, 1 to remove and 0 not upgraded.
Need to get 113 MB of archives.
After this operation, 417 MB of additional disk space will be used.
```

---

Will this break anything? Should I go ahead or just not accept it?
Thanks

---

### Post by #&amp;thj^% on 2017-08-07
What version (16.04) are you on right now?
```
lsb_release -a
```
Post back

---

### Post by lobosuelto on 2017-08-07
```

lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial
```

---

### Post by #&amp;thj^% on 2017-08-07
> **lobosuelto said:**
> Hey guys. Ubuntu 16.04 here. My software updater popped a message that says "Not all updates can be installed, run a partial upgrade to install as many updates as possible". I've broken my OS in the past so I's rather not do it again. Hence I'm asking this question here. 

Here's what I get when I run "*sudo apt-get update && sudo apt-get dist-upgrade*":

```
the following packages were automatically installed and are no longer required:
  kde-l10n-engb libllvm3.8 libllvm3.8:i386 libmircommon5 python-support
  snap-confine ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  libgles1-mesa
The following NEW packages will be installed:
  libinput-bin libllvm4.0 libllvm4.0:i386 libsensors4:i386
  linux-headers-4.4.0-89 linux-headers-4.4.0-89-generic
  linux-image-4.4.0-89-generic linux-image-extra-4.4.0-89-generic
The following packages will be upgraded:
  gnome-software gnome-software-common libegl1-mesa libgbm1 libgl1-mesa-dev
  libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386
  libglapi-mesa libglapi-mesa:i386 libgles2-mesa libinput10 libosmesa6
  libosmesa6:i386 libwayland-egl1-mesa libxatracker2 linux-generic
  linux-headers-generic linux-image-generic mesa-common-dev mesa-vdpau-drivers
  ubuntu-software
23 upgraded, 8 newly installed, 1 to remove and 0 not upgraded.
Need to get 113 MB of archives.
After this operation, 417 MB of additional disk space will be used.
```

---

Will this break anything? Should I go ahead or just not accept it?
Thanks
Welp This will be replaced:
```
The following packages will be REMOVED:
  libgles1-mesa
```
With:

```
The following packages will be upgraded:
libegl1-mesa libgbm1 libgl1-mesa-dev
  libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386
  libglapi-mesa libglapi-mesa:i386 libgles2-mesa libinput10 libosmesa6
  libosmesa6:i386 libwayland-egl1-mesa 
```
But I'm not sure why it warns of a ** "partial upgrade"** which is never advised. (So good call by you) 
But I think you should be ok with accepting this.
**Or you could just hold where your at to see if anyone reports problems today, (The wiser choice I think)**

---

### Post by lobosuelto on 2017-08-07
> **1fallen said:**
> Welp This will be replaced:
```
The following packages will be REMOVED:
  libgles1-mesa
```
With:

```
The following packages will be upgraded:
libegl1-mesa libgbm1 libgl1-mesa-dev
  libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386
  libglapi-mesa libglapi-mesa:i386 libgles2-mesa libinput10 libosmesa6
  libosmesa6:i386 libwayland-egl1-mesa 
```
But I'm not sure why it warns of a ** "partial upgrade"** which is never advised. (So good call by you) 
But I think you should be ok with accepting this.
**Or you could just hold where your at to see if anyone reports problems today, (The wiser choice I think)**

This message has been popping for aprox. 1 week now. Will hold to see if there are any other users being affected with this particular issue.

---

### Post by PaulW2U on 2017-08-07
Post deleted - info given re wrong Ubuntu release. Apologies but I still think an upgrade should work fine.

---

### Post by RobGoss on 2017-08-07
Got the same message on my Mate installation I just upgraded and it seems OK not sure why it offers  a partial upgrade

---

### Post by #&amp;thj^% on 2017-08-07
All is good to go!
I just took the update for today and all went well for me at least.
```
The following packages were automatically installed and are no longer required:
  linux-headers-4.10.0-29 linux-headers-4.10.0-29-generic
  linux-image-4.10.0-29-generic linux-image-extra-4.10.0-29-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-4.10.0-30 linux-headers-4.10.0-30-generic
  linux-headers-4.11.0-13 linux-headers-4.11.0-13-generic
  linux-image-4.10.0-30-generic linux-image-4.11.0-13-generic
  linux-image-extra-4.10.0-30-generic linux-image-extra-4.11.0-13-generic
The following packages will be upgraded:
  libfreerdp-cache1.1 libfreerdp-client1.1 libfreerdp-codec1.1
  libfreerdp-common1.1.0 libfreerdp-core1.1 libfreerdp-crypto1.1
  libfreerdp-gdi1.1 libfreerdp-locale1.1 libfreerdp-plugins-standard
  libfreerdp-primitives1.1 libfreerdp-utils1.1 libllvm4.0 libwinpr-crt0.1
  libwinpr-dsparse0.1 libwinpr-environment0.1 libwinpr-file0.1
  libwinpr-handle0.1 libwinpr-heap0.1 libwinpr-input0.1
  libwinpr-interlocked0.1 libwinpr-library0.1 libwinpr-path0.1
  libwinpr-pool0.1 libwinpr-registry0.1 libwinpr-rpc0.1 libwinpr-sspi0.1
  libwinpr-synch0.1 libwinpr-sysinfo0.1 libwinpr-thread0.1 libwinpr-utils0.1
  linux-generic-hwe-16.04 linux-generic-hwe-16.04-edge
  linux-headers-generic-hwe-16.04 linux-headers-generic-hwe-16.04-edge
  linux-image-generic-hwe-16.04 linux-image-generic-hwe-16.04-edge
  linux-libc-dev linux-source-4.10.0 shotwell shotwell-common youtube-dl
41 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 259 MB of archives.

```
Happy Ending here :D
```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.3 LTS
Release:	16.04
Codename:	xenial

```
```
inxi -SDM
System:    Host: me-750-417c Kernel: 4.11.0-13-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: HP model: 828A v: 1.01 Bios: AMI v: F.14 date: 09/19/2016
Drives:    HDD Total Size: 3500.7GB (15.7% used)
           ID-1: USB /dev/sda model: 2115 size: 500.1GB
           ID-2: /dev/sdb model: WDC_WD5000AACS size: 500.1GB
           ID-3: /dev/sdc model: WDC_WD20EADS size: 2000.4GB
           ID-4: USB /dev/sdd model: 00AADS size: 500.1GB

```

---

### Post by lobosuelto on 2017-08-08
"upgraded" and everything went smoothly. Thanks!

---

