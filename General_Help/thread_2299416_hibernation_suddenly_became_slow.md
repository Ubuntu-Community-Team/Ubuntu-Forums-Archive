---
title: "hibernation suddenly became slow"
date: 2015-10-18
forum: General Help
---

### Post by lvm on 2015-10-18
14.04-32 . After the recent batch of updates was installed the time required to hibernate the system increased from ~15 seconds to 5+ minutes, during the hibernation HD LED now blinks rapidly and regularly while before it was continuously illuminated which in my opinion indicates that the problem is with the actual speed of dumping memory to disk. Nothing at all in syslog, pm-suspend.log before and after look identical, 'running hooks' part takes 2 seconds - just like before, whatever slowed it down happens after the "performing hibernate" - the last line before "awake". So no useful information at all, and I have no ideas how to diagnose this. Disk is fine. Hardware hasn't been changed for ages (MSI 890GXM-G65 mainboard, athlon X4, 4G RAM, nvidia g210, one SATA disk).

packages that were updated the last time:
Start-Date: 2015-10-17  18:31:17
Commandline: apt-get upgrade
Upgrade: libsystemd-daemon0:i386 (204-5ubuntu20.14, 204-5ubuntu20.15), libmotif-common:i386 (2.3.4-5, 2.3.4-5ubuntu0.1), libgdk-pixbuf2.0-0:i386 (2.30.7-0ubuntu1.1, 2.30.7-0ubuntu1.2), libxm4:i386 (2.3.4-5, 2.3.4-5ubuntu0.1), libudev1:i386 (204-5ubuntu20.14, 204-5ubuntu20.15), libopenvg1-mesa:i386 (10.1.3-0ubuntu0.4, 10.1.3-0ubuntu0.5), systemd-services:i386 (204-5ubuntu20.14, 204-5ubuntu20.15), mesa-vdpau-drivers:i386 (10.1.3-0ubuntu0.4, 10.1.3-0ubuntu0.5), libglapi-mesa:i386 (10.1.3-0ubuntu0.4, 10.1.3-0ubuntu0.5), firefox-globalmenu:i386 (41.0.1+build2-0ubuntu0.14.04.1, 41.0.2+build2-0ubuntu0.14.04.1), firefox:i386 (41.0.1+build2-0ubuntu0.14.04.1, 41.0.2+build2-0ubuntu0.14.04.1), libcommons-httpclient-java:i386 (3.1-10.2, 3.1-10.2ubuntu0.14.04.1), libuil4:i386 (2.3.4-5, 2.3.4-5ubuntu0.1), libegl1-mesa:i386 (10.1.3-0ubuntu0.4, 10.1.3-0ubuntu0.5), libhunspell-1.3-0:i386 (1.3.2-6ubuntu2, 1.3.2-6ubuntu2.1), ubuntu-release-upgrader-qt:i386 (0.220.7, 0.220.8), libgbm1:i386 (10.1.3-0ubuntu0.4, 10.1.3-0ubuntu0.5), libxatracker2:i386 (10.1.3-0ubuntu0.4, 10.1.3-0ubuntu0.5), libmrm4:i386 (2.3.4-5, 2.3.4-5ubuntu0.1), libgl1-mesa-dev:i386 (10.1.3-0ubuntu0.4, 10.1.3-0ubuntu0.5), udev:i386 (204-5ubuntu20.14, 204-5ubuntu20.15), libegl1-mesa-drivers:i386 (10.1.3-0ubuntu0.4, 10.1.3-0ubuntu0.5), ubuntu-release-upgrader-core:i386 (0.220.7, 0.220.8), libgles2-mesa:i386 (10.1.3-0ubuntu0.4, 10.1.3-0ubuntu0.5), gir1.2-gdkpixbuf-2.0:i386 (2.30.7-0ubuntu1.1, 2.30.7-0ubuntu1.2), libsystemd-login0:i386 (204-5ubuntu20.14, 204-5ubuntu20.15), python3-update-manager:i386 (0.196.13, 0.196.14), libpam-systemd:i386 (204-5ubuntu20.14, 204-5ubuntu20.15), update-manager-kde:i386 (0.196.13, 0.196.14), libgl1-mesa-dri:i386 (10.1.3-0ubuntu0.4, 10.1.3-0ubuntu0.5), libgdk-pixbuf2.0-common:i386 (2.30.7-0ubuntu1.1, 2.30.7-0ubuntu1.2), firefox-locale-en:i386 (41.0.1+build2-0ubuntu0.14.04.1, 41.0.2+build2-0ubuntu0.14.04.1), update-manager-core:i386 (0.196.13, 0.196.14), flashplugin-installer:i386 (11.2.202.521ubuntu0.14.04.1, 11.2.202.540ubuntu0.14.04.2), mesa-common-dev:i386 (10.1.3-0ubuntu0.4, 10.1.3-0ubuntu0.5), libwayland-egl1-mesa:i386 (10.1.3-0ubuntu0.4, 10.1.3-0ubuntu0.5), libgl1-mesa-glx:i386 (10.1.3-0ubuntu0.4, 10.1.3-0ubuntu0.5), python3-distupgrade:i386 (0.220.7, 0.220.8), libgudev-1.0-0:i386 (204-5ubuntu20.14, 204-5ubuntu20.15)
End-Date: 2015-10-17  18:33:05

Start-Date: 2015-10-17  18:34:37
Commandline: apt-get autoremove
Remove: linux-headers-3.13.0-61-generic:i386 (3.13.0-61.100), linux-image-3.13.0-61-generic:i386 (3.13.0-61.100), linux-image-extra-3.13.0-61-generic:i386 (3.13.0-61.100), linux-headers-3.13.0-61:i386 (3.13.0-61.100)
End-Date: 2015-10-17  18:35:05

There was a slight hiccup when autoremoving the old kernel but I very much doubt it could be the reason

The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old
 you may need to re-run your boot loader[grub]

---

