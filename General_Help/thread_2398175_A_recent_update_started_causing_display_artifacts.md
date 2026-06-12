---
title: "A recent update started causing display artifacts"
date: 2018-08-08
forum: General Help
---

### Post by yigal-l on 2018-08-08
One of the updates at the first half of July caused my Ubuntu 16.04  installation to display artifacts when connected to a Dell display  through a docking station. The artifacts are showing both on the Dell  display and on the laptop's display, and do not appear when the Dell  display is not connected. How would you suggest finding which update  caused it and revert it (at least until the package is fixed)?

Updating Intel's display driver from 01.org didn't help.

  Also worth mentioning that it does not happen with another Philips  display, connected to the same Dock with HDMI. Connecting the Dell  display with HDMI didn't solve the issue.

  The setup:
  
[LIST]
[*]Lenovo Yoga 720-13IKB 
[*]Graphics card: Intel Corporation UHD Graphics 620 (rev 07) 
[*]Connected to an Asus SIMPRO Dock through USB-C 
[*]Dell P2317HI display connected to the docking station with DisplayPort/HDMI 
[/LIST]
  A video showing the artifacts (throughout the first 20 seconds): [https://streamable.com/vpr6b](https://streamable.com/vpr6b)

  The recent update history from /var/log/apt/history.log:
```

    Start-Date: 2018-07-07  19:06:54
    Commandline: aptdaemon role='role-commit-packages' sender=':1.385'
    Install: libllvm6.0:amd64 (1:6.0-1ubuntu2~16.04.1, automatic)
    Upgrade: libsoup-gnome2.4-1:amd64 (2.52.2-1ubuntu0.2, 2.52.2-1ubuntu0.3), libdrm-nouveau2:amd64 (2.4.83-1~16.04.1, 2.4.91-2~16.04.1), linux-libc-dev:amd64 (4.4.0-128.154, 4.4.0-130.156), gir1.2-soup-2.4:amd64 (2.52.2-1ubuntu0.2, 2.52.2-1ubuntu0.3), libapt-inst2.0:amd64 (1.2.26, 1.2.27), update-notifier-common:amd64 (3.168.8, 3.168.9), libarchive-zip-perl:amd64 (1.56-2, 1.56-2ubuntu0.1), apt:amd64 (1.2.26, 1.2.27), libglapi-mesa:amd64 (17.2.8-0ubuntu0~16.04.1, 18.0.5-0ubuntu0~16.04.1), xserver-xorg-video-amdgpu-hwe-16.04:amd64 (1.4.0-1~16.04.1, 18.0.1-1~16.04.1), google-chrome-stable:amd64 (67.0.3396.87-1, 67.0.3396.99-1), libxatracker2:amd64 (17.2.8-0ubuntu0~16.04.1, 18.0.5-0ubuntu0~16.04.1), libegl1-mesa:amd64 (17.2.8-0ubuntu0~16.04.1, 18.0.5-0ubuntu0~16.04.1), libapt-pkg5.0:amd64 (1.2.26, 1.2.27), libsoup2.4-1:amd64 (2.52.2-1ubuntu0.2, 2.52.2-1ubuntu0.3), libgbm1:amd64 (17.2.8-0ubuntu0~16.04.1, 18.0.5-0ubuntu0~16.04.1), libdrm-amdgpu1:amd64 (2.4.83-1~16.04.1, 2.4.91-2~16.04.1), firefox-locale-en:amd64 (60.0.2+build1-0ubuntu0.16.04.1, 61.0+build3-0ubuntu0.16.04.2), libwayland-egl1-mesa:amd64 (17.2.8-0ubuntu0~16.04.1, 18.0.5-0ubuntu0~16.04.1), libdrm2:amd64 (2.4.83-1~16.04.1, 2.4.91-2~16.04.1), oracle-java8-set-default:amd64 (8u171-1~webupd8~0, 8u171-1~webupd8~1), rfkill:amd64 (0.5-1ubuntu3, 0.5-1ubuntu3.1), apt-utils:amd64 (1.2.26, 1.2.27), libgl1-mesa-dri:amd64 (17.2.8-0ubuntu0~16.04.1, 18.0.5-0ubuntu0~16.04.1), oracle-java8-installer:amd64 (8u171-1~webupd8~0, 8u171-1~webupd8~1), xserver-xorg-video-intel-hwe-16.04:amd64 (2:2.99.917+git20170309-0ubuntu1~16.04.1, 2:2.99.917+git20171229-1~16.04.1), xserver-xorg-core-hwe-16.04:amd64 (2:1.19.5-0ubuntu2~16.04.1, 2:1.19.6-1ubuntu4~16.04.1), libgl1-mesa-glx:amd64 (17.2.8-0ubuntu0~16.04.1, 18.0.5-0ubuntu0~16.04.1), libdrm-intel1:amd64 (2.4.83-1~16.04.1, 2.4.91-2~16.04.1), firefox:amd64 (60.0.2+build1-0ubuntu0.16.04.1, 61.0+build3-0ubuntu0.16.04.2), apt-transport-https:amd64 (1.2.26, 1.2.27), libdrm-radeon1:amd64 (2.4.83-1~16.04.1, 2.4.91-2~16.04.1), xserver-xorg-legacy-hwe-16.04:amd64 (2:1.19.5-0ubuntu2~16.04.1, 2:1.19.6-1ubuntu4~16.04.1), mesa-vdpau-drivers:amd64 (17.2.8-0ubuntu0~16.04.1, 18.0.5-0ubuntu0~16.04.1), xserver-xorg-video-radeon-hwe-16.04:amd64 (1:7.10.0-1~16.04.1, 1:18.0.1-1~16.04.1), libexiv2-14:amd64 (0.25-2.1ubuntu16.04.1, 0.25-2.1ubuntu16.04.2), update-notifier:amd64 (3.168.8, 3.168.9), xserver-xorg-video-ati-hwe-16.04:amd64 (1:7.10.0-1~16.04.1, 1:18.0.1-1~16.04.1), mesa-va-drivers:amd64 (17.2.8-0ubuntu0~16.04.1, 18.0.5-0ubuntu0~16.04.1), libdrm-common:amd64 (2.4.83-1~16.04.1, 2.4.91-2~16.04.1)
    End-Date: 2018-07-07  19:07:52
    
    Start-Date: 2018-07-11  15:22:26
    Commandline: apt install android-tools-adb
    Requested-By: user (1000)
    Install: android-tools-adb:amd64 (5.1.1r36+git20160322-0ubuntu3)
    End-Date: 2018-07-11  15:22:27
    
    Start-Date: 2018-07-15  10:39:49
    Commandline: /usr/bin/unattended-upgrade
    Upgrade: libimage-magick-perl:amd64 (8:6.8.9.9-7ubuntu5.11, 8:6.8.9.9-7ubuntu5.12), libcups2:amd64 (2.1.3-4ubuntu0.4, 2.1.3-4ubuntu0.5), libimage-magick-q16-perl:amd64 (8:6.8.9.9-7ubuntu5.11, 8:6.8.9.9-7ubuntu5.12), imagemagick:amd64 (8:6.8.9.9-7ubuntu5.11, 8:6.8.9.9-7ubuntu5.12), libmagickwand-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.11, 8:6.8.9.9-7ubuntu5.12), cups-server-common:amd64 (2.1.3-4ubuntu0.4, 2.1.3-4ubuntu0.5), cups-common:amd64 (2.1.3-4ubuntu0.4, 2.1.3-4ubuntu0.5), libpng12-dev:amd64 (1.2.54-1ubuntu1, 1.2.54-1ubuntu1.1), imagemagick-6.q16:amd64 (8:6.8.9.9-7ubuntu5.11, 8:6.8.9.9-7ubuntu5.12), libmagickcore-6.q16-2-extra:amd64 (8:6.8.9.9-7ubuntu5.11, 8:6.8.9.9-7ubuntu5.12), cups-ppdc:amd64 (2.1.3-4ubuntu0.4, 2.1.3-4ubuntu0.5), libcupsmime1:amd64 (2.1.3-4ubuntu0.4, 2.1.3-4ubuntu0.5), firefox-locale-en:amd64 (61.0+build3-0ubuntu0.16.04.2, 61.0.1+build1-0ubuntu0.16.04.1), libmagickcore-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.11, 8:6.8.9.9-7ubuntu5.12), libjpeg-turbo8:amd64 (1.4.2-0ubuntu3, 1.4.2-0ubuntu3.1), libcupsppdc1:amd64 (2.1.3-4ubuntu0.4, 2.1.3-4ubuntu0.5), firefox:amd64 (61.0+build3-0ubuntu0.16.04.2, 61.0.1+build1-0ubuntu0.16.04.1), imagemagick-common:amd64 (8:6.8.9.9-7ubuntu5.11, 8:6.8.9.9-7ubuntu5.12), libmagick++-6.q16-5v5:amd64 (8:6.8.9.9-7ubuntu5.11, 8:6.8.9.9-7ubuntu5.12), cups-bsd:amd64 (2.1.3-4ubuntu0.4, 2.1.3-4ubuntu0.5), cups-core-drivers:amd64 (2.1.3-4ubuntu0.4, 2.1.3-4ubuntu0.5), cups-daemon:amd64 (2.1.3-4ubuntu0.4, 2.1.3-4ubuntu0.5), libcupsimage2:amd64 (2.1.3-4ubuntu0.4, 2.1.3-4ubuntu0.5), cups:amd64 (2.1.3-4ubuntu0.4, 2.1.3-4ubuntu0.5), libcupscgi1:amd64 (2.1.3-4ubuntu0.4, 2.1.3-4ubuntu0.5), cups-client:amd64 (2.1.3-4ubuntu0.4, 2.1.3-4ubuntu0.5), perlmagick:amd64 (8:6.8.9.9-7ubuntu5.11, 8:6.8.9.9-7ubuntu5.12), libpng12-0:amd64 (1.2.54-1ubuntu1, 1.2.54-1ubuntu1.1)
    End-Date: 2018-07-15  10:40:06
    
    Start-Date: 2018-07-15  10:51:00
    Commandline: aptdaemon role='role-commit-packages' sender=':1.730'
    Upgrade: dnsmasq-base:amd64 (2.75-1ubuntu0.16.04.4, 2.75-1ubuntu0.16.04.5), flashplugin-installer:amd64 (30.0.0.113ubuntu0.16.04.1, 30.0.0.134ubuntu0.16.04.1), thunderbird-gnome-support:amd64 (1:52.8.0+build1-0ubuntu0.16.04.1, 1:52.9.1+build3-0ubuntu0.16.04.1), thunderbird-locale-en-us:amd64 (1:52.8.0+build1-0ubuntu0.16.04.1, 1:52.9.1+build3-0ubuntu0.16.04.1), thunderbird:amd64 (1:52.8.0+build1-0ubuntu0.16.04.1, 1:52.9.1+build3-0ubuntu0.16.04.1), dns-root-data:amd64 (2015052300+h+1, 2018013001~16.04.1), linux-firmware:amd64 (1.157.19, 1.157.20), thunderbird-locale-en:amd64 (1:52.8.0+build1-0ubuntu0.16.04.1, 1:52.9.1+build3-0ubuntu0.16.04.1)
    End-Date: 2018-07-15  10:52:16
    
    Start-Date: 2018-07-17  11:07:13
    Commandline: aptdaemon role='role-install-file' sender=':1.83'
    Install: libxcb-xtest0:amd64 (1.11.1-1ubuntu1, automatic)
    End-Date: 2018-07-17  11:07:14
    
    Start-Date: 2018-07-18  11:32:40
    Commandline: /usr/bin/unattended-upgrade
    Upgrade: libpolkit-gobject-1-0:amd64 (0.105-14.1, 0.105-14.1ubuntu0.1), libpolkit-agent-1-0:amd64 (0.105-14.1, 0.105-14.1ubuntu0.1), libpolkit-backend-1-0:amd64 (0.105-14.1, 0.105-14.1ubuntu0.1), policykit-1:amd64 (0.105-14.1, 0.105-14.1ubuntu0.1)
    End-Date: 2018-07-18  11:32:44
    
    Start-Date: 2018-07-19  16:49:39
    Commandline: apt upgrade
    Requested-By: user (1000)
    Upgrade: snapd:amd64 (2.32.9, 2.33.1ubuntu2), squashfs-tools:amd64 (1:4.3-3ubuntu2.16.04.1, 1:4.3-3ubuntu2.16.04.2), gnome-software:amd64 (3.20.5-0ubuntu0.16.04.10, 3.20.5-0ubuntu0.16.04.11), python-apt-common:amd64 (1.1.0~beta1ubuntu0.16.04.1, 1.1.0~beta1ubuntu0.16.04.2), ubuntu-software:amd64 (3.20.5-0ubuntu0.16.04.10, 3.20.5-0ubuntu0.16.04.11), chromium-codecs-ffmpeg-extra:amd64 (66.0.3359.181-0ubuntu0.16.04.1, 67.0.3396.99-0ubuntu0.16.04.2), ubuntu-core-launcher:amd64 (2.32.9, 2.33.1ubuntu2), oracle-java8-set-default:amd64 (8u171-1~webupd8~1, 8u181-1~webupd8~1), oracle-java8-installer:amd64 (8u171-1~webupd8~1, 8u181-1~webupd8~1), gnome-software-common:amd64 (3.20.5-0ubuntu0.16.04.10, 3.20.5-0ubuntu0.16.04.11), python3-apt:amd64 (1.1.0~beta1ubuntu0.16.04.1, 1.1.0~beta1ubuntu0.16.04.2)
    End-Date: 2018-07-19  16:50:45
```

(Posted on Ask Ubuntu a week ago but realized this kind of troubleshooting probably belongs here)

---

