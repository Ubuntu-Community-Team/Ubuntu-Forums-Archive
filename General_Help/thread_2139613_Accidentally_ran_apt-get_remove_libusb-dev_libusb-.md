---
title: "Accidentally ran apt-get remove libusb-dev libusb-0.1-4 xserver-xorg-input-joystick"
date: 2013-04-27
forum: General Help
---

### Post by Vindows Wista on 2013-04-27
Hey guys I need some help with this issue. I ran the above command and it seems to have removed some essential packages. I can't seem to run any apt-get command. I get this error: sudo: apt-get: command not found; Here is a list of things this removed and installed. Is there a way to get everything back? I've only noticed the apt-get command not working but I'd like to install everything back so I don't run into anymore problems. I'm running Ubuntu 12.04

Start-Date: 2013-04-27  23:22:52
Commandline: apt-get remove libusb-dev libusb-0.1-4 xserver-xorg-input-joystick
Install: pinentry-gtk2:amd64 (0.8.1-1ubuntu1, automatic), libksba8:amd64 (1.2.0-2, automatic), gnupg-agent:amd64 (2.0.17-2ubuntu2.12.04.2, automatic), libassuan0:amd64 (2.0.2-1ubuntu1, automatic), gnupg2:amd64 (2.0.17-2ubuntu2.12.04.2, automatic)
Remove: sane-utils:amd64 (1.0.22-7ubuntu1), bluez-alsa:amd64 (4.98-2ubuntu7), ubuntu-desktop:amd64 (1.267.1), usb-modeswitch:amd64 (1.2.3+repack0-1ubuntu2), python-aptdaemon.pkcompat:amd64 (0.43+bzr805-0ubuntu9), gnome-shell:amd64 (3.4.1-0ubuntu2), unattended-upgrades:amd64 (0.76ubuntu1), update-notifier:amd64 (0.119ubuntu8.6), libgphoto2-port0:amd64 (2.4.13-1ubuntu1.2), libsane-hpaio:amd64 (3.12.2-1ubuntu3.1), bluez-gstreamer:amd64 (4.98-2ubuntu7), nautilus-share:amd64 (0.7.3-1ubuntu2), gvfs-backends:amd64 (1.12.1-0ubuntu1.1), obex-data-server:amd64 (0.4.6-0ubuntu1), libsane:amd64 (1.0.22-7ubuntu1), language-selector-gnome:amd64 (0.79.3), ubuntuone-installer:amd64 (3.0.2-0ubuntu1.1), ubuntu-extras-keyring:amd64 (2010.09.27), python-software-properties:amd64 (0.82.7.3), printer-driver-postscript-hp:amd64 (3.12.2-1ubuntu3.1), hplip:amd64 (3.12.2-1ubuntu3.1), seahorse:amd64 (3.2.2-0ubuntu2.1), software-center:amd64 (5.2.9), bluez:amd64 (4.98-2ubuntu7), shotwell:amd64 (0.12.3-0ubuntu0.1), duplicity:amd64 (0.6.18-0ubuntu3.1), update-manager:amd64 (0.156.14.11), update-manager-core:amd64 (0.156.14.11), deja-dup:amd64 (22.0-0ubuntu4), simple-scan:amd64 (3.4.3-0ubuntu1), python-aptdaemon:amd64 (0.43+bzr805-0ubuntu9), apt:amd64 (0.8.16~exp12ubuntu10.10), libusb-dev:amd64 (0.1.12-20), sessioninstaller:amd64 (0.20+bzr128-0ubuntu1.2), medibuntu-keyring:amd64 (2008.04.20), libhpmud0:amd64 (3.12.2-1ubuntu3.1), gnome-bluetooth:amd64 (3.2.2-0ubuntu5), gnome-user-share:amd64 (3.0.2-0ubuntu1), system-config-printer-udev:amd64 (1.3.8+20120201-0ubuntu8.1), software-properties-gtk:amd64 (0.82.7.3), libopenobex1:amd64 (1.5-2build1), aptdaemon:amd64 (0.43+bzr805-0ubuntu9), libusb-0.1-4:amd64 (0.1.12-20), apturl:amd64 (0.5.1ubuntu3), xul-ext-ubufox:amd64 (2.6-0ubuntu0.12.04.1), printer-driver-hpcups:amd64 (3.12.2-1ubuntu3.1), colord:amd64 (0.1.16-2ubuntu0.1), python-aptdaemon.gtk3widgets:amd64 (0.43+bzr805-0ubuntu9), landscape-client-ui-install:amd64 (12.05-0ubuntu1.12.04), xserver-xorg-input-joystick:amd64 (1.6.0-1build2), printer-driver-hpijs:amd64 (3.12.2-1ubuntu3.1), gnupg:amd64 (1.4.11-3ubuntu2.2), libgphoto2-2:amd64 (2.4.13-1ubuntu1.2)
End-Date: 2013-04-27  23:24:25

---

### Post by dino99 on 2013-04-27
At least try the "recovery mode" from the grub menu while booting, activate the network and select to repair the system. If that also fail, then you are ready for a clean fresh install  :P

---

### Post by steeldriver on 2013-04-27
... if repair fails, you *may* be able to reinstall apt (and related python packages) using dpkg from the debs in /var/cache/apt/archives/ (if they haven't been cleaned yet)

```
ls /var/cache/apt/archives/| grep apt
```

---

### Post by Vindows Wista on 2013-04-29
Thanks for the suggestions. I tried the recovery mode but it just hangs when I enable networking, it installs a bunch of plugins and then just hangs there.

I tried ls /var/cache/apt/archives/| grep apt, and it gives me this list: aptdaemon_0.43+bzr805-0ubuntu9_all.deb
```
aptdaemon-data_0.43+bzr805-0ubuntu9_all.deb
aptitude_0.6.6-1ubuntu1.2_amd64.deb
python-aptdaemon_0.43+bzr805-0ubuntu9_all.deb
python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu9_all.deb
python-aptdaemon.pkcompat_0.43+bzr805-0ubuntu9_all.deb
```

I then tried to install the 3 python debs but got this...
```
sudo dpkg -i python-aptdaemon_0.43+bzr805-0ubuntu9_all.deb
Selecting previously unselected package python-aptdaemon.
(Reading database ... 420813 files and directories currently installed.)
Unpacking python-aptdaemon (from python-aptdaemon_0.43+bzr805-0ubuntu9_all.deb) ...
dpkg: dependency problems prevent configuration of python-aptdaemon:
 python-aptdaemon depends on python-software-properties; however:
  Package python-software-properties is not installed.
dpkg: error processing python-aptdaemon (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-aptdaemon
```

---

