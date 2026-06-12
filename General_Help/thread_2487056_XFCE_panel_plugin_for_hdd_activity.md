---
title: "XFCE panel plugin for hdd activity"
date: 2023-05-21
forum: General Help
---

### Post by libertyspike138 on 2023-05-21
I have a notebook without any hdd activity led. I was curious if there is a plugin available to act like one in my try area in xfce? Thanks!

---

### Post by MAFoElffen on 2023-05-22
Here:
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt list xfce4-diskperf-plugin
Listing... Done
xfce4-diskperf-plugin/jammy 2.6.3-1 amd64
mafoelffen@Mikes-ThinkPad-T520:~$ apt-cache show xfce4-diskperf-plugin
Package: xfce4-diskperf-plugin
Architecture: amd64
Version: 2.6.3-1
Multi-Arch: same
Priority: optional
Section: universe/x11
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Xfce Maintainers <debian-xfce@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 379
Depends: libc6 (>= 2.7), libglib2.0-0 (>= 2.18.0), libgtk-3-0 (>= 3.16.2), libxfce4panel-2.0-4 (>= 4.11.0), libxfce4ui-2-0 (>= 4.11.0), libxfce4util7 (>= 4.9.0)
Filename: pool/universe/x/xfce4-diskperf-plugin/xfce4-diskperf-plugin_2.6.3-1_amd64.deb
Size: 50972
MD5sum: b74dab4e705918bb3ce5e9402ed61157
SHA1: 7a83694f3131e4b7ccc93880edd557ad0bdaded8
SHA256: 7bae51292b1faf30f82f67ec005420b2a80a789d6ca5df247cf7d9b4c42caab7
SHA512: e292dc8364bc829263f4e346e156f874a072316c21f2b825115aca2c25c801e83e1c5f2a8ff1c5870e2d509e17a6a033ee4966f723a674cec7a2ffd96f8e6e11
Homepage: https://goodies.xfce.org/
Description-en: disk performance display plugin for the Xfce4 panel
 DiskPerf is a plugin for the Xfce desktop environment panel. It displays disks
 and partitions performance statistics based on the rsect/wsect data provided
 by the Linux kernel.
Description-md5: e1ec7bc1bceb61058c510c729c575e6b

```

---

### Post by libertyspike138 on 2023-05-22
Thanks!

---

