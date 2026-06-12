---
title: "nVidia updates keep failing through ppa"
date: 2019-04-28
forum: General Help
---

### Post by adam-knezi on 2019-04-28
Hi,

Ive been using the graphics-drivers PPA to update my GPU drivers as i want the proprietary drivers for my nVidia card (GTX 980Ti), however, my updates keep failing due to connection time out on IP 91.189.95.83

Removing the PPA and trying again didn't work, nor did trying to download and install a different version of my driver help either.

Is anyone else having this issue? Any fixes?

Ive checked my routers logs (WatchGuard T35-W) and there are no blocks/deny errors in the logs, i can see the connections go through perfectly.

My system is,

```
OS - Ubuntu 18.04 in a dual boot with Windows 10
CPU - i7-5820k
MOBO - MSI X99 SLI Krait Edition
RAM - 16GB DDR4
GPU - nVidia 980Ti (Gigabyte Windforce G1 gaming edition)
```

Any help/advise would be appreciated!

**UPDATE - **Its failing on [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) as the source, apt messages below,


```
The following NEW packages will be installed:
  linux-headers-4.15.0-48 linux-headers-4.15.0-48-generic linux-image-4.15.0-48-generic linux-modules-4.15.0-48-generic linux-modules-extra-4.15.0-48-generic
The following packages will be upgraded:
  gir1.2-mutter-2 gnome-shell gnome-shell-common language-selector-common language-selector-gnome libmutter-2-0 libneon27-gnutls libnss-myhostname libnss-systemd libnuma-dev libnuma1 libnvidia-cfg1-415
  libnvidia-compute-415 libnvidia-compute-415:i386 libnvidia-decode-415 libnvidia-decode-415:i386 libnvidia-encode-415 libnvidia-encode-415:i386 libnvidia-fbc1-415 libnvidia-fbc1-415:i386
  libnvidia-gl-415 libnvidia-gl-415:i386 libnvidia-ifr1-415 libnvidia-ifr1-415:i386 libpam-systemd libplymouth4 libsystemd0 libsystemd0:i386 libudev1 libudev1:i386 linux-firmware linux-generic
  linux-headers-generic linux-image-generic linux-libc-dev linux-signed-generic login mutter mutter-common nvidia-compute-utils-415 nvidia-dkms-415 nvidia-driver-415 nvidia-kernel-source-415
  nvidia-utils-415 passwd plymouth plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text systemd systemd-sysv udev ureadahead xserver-xorg-video-nvidia-415
54 to upgrade, 5 to newly install, 0 to remove and 0 not to upgrade.
Need to get 50.0 MB/253 MB of archives.
After this operation, 359 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic/main i386 libnvidia-gl-415 i386 415.27-0ubuntu0~gpu18.04.2 [16.9 MB]
Err:1 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic/main i386 libnvidia-gl-415 i386 415.27-0ubuntu0~gpu18.04.2                                                                               
  Connection timed out [IP: 91.189.95.83 80]
Get:2 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic/main amd64 libnvidia-compute-415 amd64 415.27-0ubuntu0~gpu18.04.2 [20.9 MB]
Err:2 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic/main amd64 libnvidia-compute-415 amd64 415.27-0ubuntu0~gpu18.04.2
  Connection timed out [IP: 91.189.95.83 80]
Get:3 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic/main amd64 nvidia-kernel-source-415 amd64 415.27-0ubuntu0~gpu18.04.2 [10.7 MB]
Err:3 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic/main amd64 nvidia-kernel-source-415 amd64 415.27-0ubuntu0~gpu18.04.2
  Connection timed out [IP: 91.189.95.83 80]
Get:4 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic/main amd64 xserver-xorg-video-nvidia-415 amd64 415.27-0ubuntu0~gpu18.04.2 [1,555 kB]
Err:4 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic/main amd64 xserver-xorg-video-nvidia-415 amd64 415.27-0ubuntu0~gpu18.04.2
  Connection timed out [IP: 91.189.95.83 80]
E: Failed to fetch [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-415/libnvidia-gl-415_415.27-0ubuntu0~gpu18.04.2_i386.deb](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-415/libnvidia-gl-415_415.27-0ubuntu0~gpu18.04.2_i386.deb)  Connection timed out [IP: 91.189.95.83 80]
E: Failed to fetch [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-415/libnvidia-compute-415_415.27-0ubuntu0~gpu18.04.2_amd64.deb](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-415/libnvidia-compute-415_415.27-0ubuntu0~gpu18.04.2_amd64.deb)  Connection timed out [IP: 91.189.95.83 80]
E: Failed to fetch [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-415/nvidia-kernel-source-415_415.27-0ubuntu0~gpu18.04.2_amd64.deb](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-415/nvidia-kernel-source-415_415.27-0ubuntu0~gpu18.04.2_amd64.deb)  Connection timed out [IP: 91.189.95.83 80]
E: Failed to fetch [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-415/xserver-xorg-video-nvidia-415_415.27-0ubuntu0~gpu18.04.2_amd64.deb](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-415/xserver-xorg-video-nvidia-415_415.27-0ubuntu0~gpu18.04.2_amd64.deb)  Connection timed out [IP: 91.189.95.83 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by monkeybrain20122 on 2019-04-28
May try a different server.
jump to step2 to save your time [https://itsfoss.com/fix-failed-download-package-files-error-ubuntu/](https://itsfoss.com/fix-failed-download-package-files-error-ubuntu/)

---

### Post by again? on 2019-04-28
I can click on the "Failed to fetch" links at the end of your last post and it will download the debs.
Can you? 
May just be a temporary network issue.

---

### Post by adam-knezi on 2019-05-06
Hi all,

Thanks for the responses, unfortunately I couldn't fix this issue by changing mirrors and downloading the .deb files worked, however when i installed i got these errors,

domacikolaci@Adam-PC:~/Downloads$ sudo dpkg -i libnvidia-compute-415_415.27-0ubuntu0~gpu18.04.2_amd64.deb libnvidia-gl-415_415.27-0ubuntu0~gpu18.04.2_i386.deb nvidia-kernel-source-415_415.27-0ubuntu0~gpu18.04.2_amd64.deb 
(Reading database ... 313468 files and directories currently installed.)
Preparing to unpack libnvidia-compute-415_415.27-0ubuntu0~gpu18.04.2_amd64.deb ...
Unpacking libnvidia-compute-415:amd64 (415.27-0ubuntu0~gpu18.04.2) over (415.27-0ubuntu0~gpu18.04.2) ...
Preparing to unpack libnvidia-gl-415_415.27-0ubuntu0~gpu18.04.2_i386.deb ...
dpkg-query: no packages found matching libnvidia-gl-410
Unpacking libnvidia-gl-415:i386 (415.27-0ubuntu0~gpu18.04.2) over (415.27-0ubuntu0~gpu18.04.2) ...
Preparing to unpack nvidia-kernel-source-415_415.27-0ubuntu0~gpu18.04.2_amd64.deb ...
Unpacking nvidia-kernel-source-415 (415.27-0ubuntu0~gpu18.04.2) over (415.27-0ubuntu0~gpu18.04.2) ...
dpkg: error processing package libnvidia-compute-415:amd64 (--install):
 package libnvidia-compute-415:amd64 415.27-0ubuntu0~gpu18.04.2 cannot be configured because libnvidia-compute-415:i386 is at a different version (415.27-0ubuntu0~gpu18.04.1)
dpkg: error processing package libnvidia-gl-415:i386 (--install):
 package libnvidia-gl-415:i386 415.27-0ubuntu0~gpu18.04.2 cannot be configured because libnvidia-gl-415:amd64 is at a different version (415.27-0ubuntu0~gpu18.04.1)
Setting up nvidia-kernel-source-415 (415.27-0ubuntu0~gpu18.04.2) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Errors were encountered while processing:
 libnvidia-compute-415:amd64
 libnvidia-gl-415:i386
domacikolaci@Adam-PC:~/Downloads$

---

