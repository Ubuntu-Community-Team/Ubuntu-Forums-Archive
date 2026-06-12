---
title: "Can't fully reinstall 59 packages after &quot;/var/lib/dpkg/info/*&quot; wipe"
date: 2016-07-02
forum: General Help
---

### Post by usedname66 on 2016-07-02
Hello,

Tiny issue, mistaken deleted all of "/var/lib/dpkg/info/", had to therefore reinstall about 3k packages, as others suggested doing, and it fixed most "dpkg: warning: files list file for package..." errors.

However I have 40** packages** (BELOW) that after trying to do "sudo apt-get install --reinstall (BELOW)",  I get the the error ***"Reinstallation of (BELOW) is not possible, it cannot be downloaded."***. I searched for a few of them but most don't have any PPAs associated with them, **so I cannot reinstall them**?

Help much appreciated. (ignore .txt file only 40 now thats below)

```
dpkg: warning: files list file for package 'linux-headers-4.2.0-35' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libncurses5:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwayland-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtinfo5:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxtables10' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-themes-standard-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libvpx2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ttf-kochi-gothic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libisccfg-export90' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ieee-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ttf-indic-fonts-core' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapt-inst1.7:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ttf-kochi-mincho' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libx264-146:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gstreamer0.10-fluendo-mp3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtinfo-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtinfo-dev:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lib32tinfo5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libprocps3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libirs-export91' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lib32ncurses5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdns-export100' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gstreamer0.10-plugins-bad-multiverse' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsoundtouch0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libncurses5-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjsoncpp0v5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lib32ncurses5-dev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libisc-export95' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpq5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gstreamer0.10-plugins-bad:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnutls-deb0-28:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapt-pkg4.16:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxrender1:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-media' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgstreamer-plugins-bad0.10-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gstreamer0.10-plugins-ugly:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-4.2.0-35-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lib32tinfo-dev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwayland-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxrender1-dbg:amd64' missing; assuming package has no files currently installed
```

---

### Post by oldos2er on 2016-07-03
Which version of Ubuntu? I'm guessing the packages that won't install have been superseded by newer versions.

---

### Post by usedname66 on 2016-07-03
> **oldos2er said:**
> Which version of Ubuntu? I'm guessing the packages that won't install have been superseded by newer versions.

Yup coming  from 15.04 and upgraded to 64-bit 16.04, I can too see some of those packages are no longer needed,  pretty tedious trying to figure which one thoses.

---

### Post by oldos2er on 2016-07-04
I see you mark the thread 'Solved' which we appreciate, so in that spirit would you share the solution? It will assist other who might be having the same problem.

---

### Post by usedname66 on 2016-07-05
I had to go through each one of the packages, learn what they are their dependencies ect. Took a while, no simple solution but [https://mirrors.kernel.org](https://mirrors.kernel.org) helped to some of the packages that I couldn't of directly downloaded.

---

