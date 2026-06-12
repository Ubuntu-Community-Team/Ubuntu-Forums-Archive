---
title: "Cant update or upgrade please help"
date: 2018-02-25
forum: General Help
---

### Post by asifnaz on 2018-02-25
```
asif@asif-HP-ProBook-4330s:~$ sudo apt-get update
[sudo] password for asif: 
Ign:1 http://security.ubuntu.com/ubuntu zesty-security InRelease            
Err:2 http://security.ubuntu.com/ubuntu zesty-security Release
  404  Not Found [IP: 91.189.91.26 80]
Ign:3 http://ci.archive.ubuntu.com/ubuntu zesty InRelease
Ign:4 http://ci.archive.ubuntu.com/ubuntu zesty-updates InRelease
Ign:5 http://ci.archive.ubuntu.com/ubuntu zesty-backports InRelease
Err:6 http://ci.archive.ubuntu.com/ubuntu zesty Release
  404  Not Found [IP: 91.189.88.161 80]
Err:7 http://ci.archive.ubuntu.com/ubuntu zesty-updates Release
  404  Not Found [IP: 91.189.88.161 80]
Err:8 http://ci.archive.ubuntu.com/ubuntu zesty-backports Release
  404  Not Found [IP: 91.189.88.161 80]
Reading package lists... Done
E: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ci.archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ci.archive.ubuntu.com/ubuntu zesty-updates Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ci.archive.ubuntu.com/ubuntu zesty-backports Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
asif@asif-HP-ProBook-4330s:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  game-data-packager game-data-packager-runtime ioquake3 ioquake3-server libopusfile0 linux-headers-4.10.0-19 linux-headers-4.10.0-19-generic
  linux-headers-4.10.0-22 linux-headers-4.10.0-22-generic linux-headers-4.10.0-24 linux-headers-4.10.0-24-generic
  linux-image-4.10.0-19-generic linux-image-4.10.0-22-generic linux-image-4.10.0-24-generic linux-image-extra-4.10.0-19-generic
  linux-image-extra-4.10.0-22-generic linux-image-extra-4.10.0-24-generic yamagi-quake2 yamagi-quake2-core
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  gdb gdbserver gir1.2-javascriptcoregtk-4.0 gir1.2-webkit2-4.0 grub-common grub-pc grub-pc-bin grub2-common imagemagick imagemagick-6-common
  imagemagick-6.q16 libjavascriptcoregtk-4.0-18 libmagickcore-6.q16-3 libmagickcore-6.q16-3-extra libmagickwand-6.q16-3 libqt5concurrent5
  libqt5core5a libqt5dbus5 libqt5gui5 libqt5network5 libqt5opengl5 libqt5printsupport5 libqt5sql5 libqt5sql5-sqlite libqt5test5
  libqt5widgets5 libqt5xml5 libwebkit2gtk-4.0-37 libwhoopsie0 linux-libc-dev python3-distupgrade python3-update-manager qt5-gtk-platformtheme
  sudo ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk update-manager update-manager-core whoopsie xmir xserver-common
  xserver-xorg-core
42 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 39.4 MB of archives.
After this operation, 26.6 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 grub-pc i386 2.02~beta3-4ubuntu2.2
  404  Not Found [IP: 91.189.88.152 80]
Err:2 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 grub-pc-bin i386 2.02~beta3-4ubuntu2.2
  404  Not Found [IP: 91.189.88.152 80]
Err:3 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 grub2-common i386 2.02~beta3-4ubuntu2.2
  404  Not Found [IP: 91.189.88.152 80]
Err:4 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 grub-common i386 2.02~beta3-4ubuntu2.2
  404  Not Found [IP: 91.189.88.152 80]
Err:5 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 imagemagick-6-common all 8:6.9.7.4+dfsg-3ubuntu1.2
  404  Not Found [IP: 91.189.88.152 80]
Ign:6 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libmagickcore-6.q16-3 i386 8:6.9.7.4+dfsg-3ubuntu1.2
Ign:7 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libmagickwand-6.q16-3 i386 8:6.9.7.4+dfsg-3ubuntu1.2
Err:8 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 whoopsie i386 0.2.55.2
  404  Not Found [IP: 91.189.88.152 80]
Err:9 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libwhoopsie0 i386 0.2.55.2
  404  Not Found [IP: 91.189.88.152 80]
Err:10 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 sudo i386 1.8.19p1-1ubuntu1.2
  404  Not Found [IP: 91.189.88.152 80]
Err:11 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 ubuntu-release-upgrader-gtk all 1:17.04.9
  404  Not Found [IP: 91.189.88.152 80]
Err:12 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 ubuntu-release-upgrader-core all 1:17.04.9
  404  Not Found [IP: 91.189.88.152 80]
Err:13 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 python3-distupgrade all 1:17.04.9
  404  Not Found [IP: 91.189.88.152 80]
Err:14 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 update-manager all 1:17.04.4
  404  Not Found [IP: 91.189.88.152 80]
Err:15 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 update-manager-core all 1:17.04.4
  404  Not Found [IP: 91.189.88.152 80]
Err:16 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 python3-update-manager all 1:17.04.4
  404  Not Found [IP: 91.189.88.152 80]
Ign:17 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 gir1.2-webkit2-4.0 i386 2.16.6-0ubuntu0.17.04.1
Ign:18 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 gir1.2-javascriptcoregtk-4.0 i386 2.16.6-0ubuntu0.17.04.1
Ign:19 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libwebkit2gtk-4.0-37 i386 2.16.6-0ubuntu0.17.04.1
Ign:20 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libjavascriptcoregtk-4.0-18 i386 2.16.6-0ubuntu0.17.04.1
Err:5 http://security.ubuntu.com/ubuntu zesty-security/main i386 imagemagick-6-common all 8:6.9.7.4+dfsg-3ubuntu1.2
  404  Not Found [IP: 91.189.88.152 80]
Ign:21 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 gdb i386 7.12.50.20170314-0ubuntu1.1
Ign:22 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 gdbserver i386 7.12.50.20170314-0ubuntu1.1
Ign:23 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 imagemagick-6.q16 i386 8:6.9.7.4+dfsg-3ubuntu1.2
Ign:24 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 imagemagick i386 8:6.9.7.4+dfsg-3ubuntu1.2
Ign:25 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libmagickcore-6.q16-3-extra i386 8:6.9.7.4+dfsg-3ubuntu1.2
Err:26 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libqt5core5a i386 5.7.1+dfsg-2ubuntu4~1.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:27 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libqt5concurrent5 i386 5.7.1+dfsg-2ubuntu4~1.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:6 http://security.ubuntu.com/ubuntu zesty-security/main i386 libmagickcore-6.q16-3 i386 8:6.9.7.4+dfsg-3ubuntu1.2
  404  Not Found [IP: 91.189.88.152 80]
Err:7 http://security.ubuntu.com/ubuntu zesty-security/main i386 libmagickwand-6.q16-3 i386 8:6.9.7.4+dfsg-3ubuntu1.2
  404  Not Found [IP: 91.189.88.152 80]
Err:17 http://security.ubuntu.com/ubuntu zesty-security/main i386 gir1.2-webkit2-4.0 i386 2.16.6-0ubuntu0.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:18 http://security.ubuntu.com/ubuntu zesty-security/main i386 gir1.2-javascriptcoregtk-4.0 i386 2.16.6-0ubuntu0.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:19 http://security.ubuntu.com/ubuntu zesty-security/main i386 libwebkit2gtk-4.0-37 i386 2.16.6-0ubuntu0.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:20 http://security.ubuntu.com/ubuntu zesty-security/main i386 libjavascriptcoregtk-4.0-18 i386 2.16.6-0ubuntu0.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:28 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libqt5dbus5 i386 5.7.1+dfsg-2ubuntu4~1.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:29 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 qt5-gtk-platformtheme i386 5.7.1+dfsg-2ubuntu4~1.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:30 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libqt5network5 i386 5.7.1+dfsg-2ubuntu4~1.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:21 http://security.ubuntu.com/ubuntu zesty-security/main i386 gdb i386 7.12.50.20170314-0ubuntu1.1
  404  Not Found [IP: 91.189.88.152 80]
Err:22 http://security.ubuntu.com/ubuntu zesty-security/main i386 gdbserver i386 7.12.50.20170314-0ubuntu1.1
  404  Not Found [IP: 91.189.88.152 80]
Err:23 http://security.ubuntu.com/ubuntu zesty-security/main i386 imagemagick-6.q16 i386 8:6.9.7.4+dfsg-3ubuntu1.2
  404  Not Found [IP: 91.189.88.152 80]
Err:24 http://security.ubuntu.com/ubuntu zesty-security/main i386 imagemagick i386 8:6.9.7.4+dfsg-3ubuntu1.2
  404  Not Found [IP: 91.189.88.152 80]
Err:25 http://security.ubuntu.com/ubuntu zesty-security/main i386 libmagickcore-6.q16-3-extra i386 8:6.9.7.4+dfsg-3ubuntu1.2
  404  Not Found [IP: 91.189.88.152 80]
Err:31 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libqt5gui5 i386 5.7.1+dfsg-2ubuntu4~1.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:32 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libqt5widgets5 i386 5.7.1+dfsg-2ubuntu4~1.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:33 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libqt5opengl5 i386 5.7.1+dfsg-2ubuntu4~1.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:34 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libqt5printsupport5 i386 5.7.1+dfsg-2ubuntu4~1.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:35 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libqt5sql5 i386 5.7.1+dfsg-2ubuntu4~1.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:36 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libqt5sql5-sqlite i386 5.7.1+dfsg-2ubuntu4~1.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:37 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libqt5test5 i386 5.7.1+dfsg-2ubuntu4~1.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:38 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 libqt5xml5 i386 5.7.1+dfsg-2ubuntu4~1.17.04.1
  404  Not Found [IP: 91.189.88.152 80]
Err:39 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 linux-libc-dev i386 4.10.0-30.34
  404  Not Found [IP: 91.189.88.152 80]
Ign:40 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 xserver-common all 2:1.19.3-1ubuntu1.1
Ign:41 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 xmir i386 2:1.19.3-1ubuntu1.1
Err:39 http://security.ubuntu.com/ubuntu zesty-security/main i386 linux-libc-dev i386 4.10.0-30.34
  404  Not Found [IP: 91.189.88.152 80]
Ign:42 http://ci.archive.ubuntu.com/ubuntu zesty-updates/main i386 xserver-xorg-core i386 2:1.19.3-1ubuntu1.1
Err:40 http://security.ubuntu.com/ubuntu zesty-security/main i386 xserver-common all 2:1.19.3-1ubuntu1.1
  404  Not Found [IP: 91.189.88.152 80]
Err:41 http://security.ubuntu.com/ubuntu zesty-security/main i386 xmir i386 2:1.19.3-1ubuntu1.1
  404  Not Found [IP: 91.189.88.152 80]
Err:42 http://security.ubuntu.com/ubuntu zesty-security/main i386 xserver-xorg-core i386 2:1.19.3-1ubuntu1.1
  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_2.02~beta3-4ubuntu2.2_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc-bin_2.02~beta3-4ubuntu2.2_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub2-common_2.02~beta3-4ubuntu2.2_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_2.02~beta3-4ubuntu2.2_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/imagemagick-6-common_6.9.7.4+dfsg-3ubuntu1.2_all.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore-6.q16-3_6.9.7.4+dfsg-3ubuntu1.2_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickwand-6.q16-3_6.9.7.4+dfsg-3ubuntu1.2_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/w/whoopsie/whoopsie_0.2.55.2_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/w/whoopsie/libwhoopsie0_0.2.55.2_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.8.19p1-1ubuntu1.2_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-release-upgrader/ubuntu-release-upgrader-gtk_17.04.9_all.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-release-upgrader/ubuntu-release-upgrader-core_17.04.9_all.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-release-upgrader/python3-distupgrade_17.04.9_all.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_17.04.4_all.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_17.04.4_all.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/python3-update-manager_17.04.4_all.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/w/webkit2gtk/gir1.2-webkit2-4.0_2.16.6-0ubuntu0.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/w/webkit2gtk/gir1.2-javascriptcoregtk-4.0_2.16.6-0ubuntu0.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/w/webkit2gtk/libwebkit2gtk-4.0-37_2.16.6-0ubuntu0.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/w/webkit2gtk/libjavascriptcoregtk-4.0-18_2.16.6-0ubuntu0.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gdb/gdb_7.12.50.20170314-0ubuntu1.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gdb/gdbserver_7.12.50.20170314-0ubuntu1.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/imagemagick-6.q16_6.9.7.4+dfsg-3ubuntu1.2_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/imagemagick_6.9.7.4+dfsg-3ubuntu1.2_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore-6.q16-3-extra_6.9.7.4+dfsg-3ubuntu1.2_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/q/qtbase-opensource-src/libqt5core5a_5.7.1+dfsg-2ubuntu4~1.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/q/qtbase-opensource-src/libqt5concurrent5_5.7.1+dfsg-2ubuntu4~1.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/q/qtbase-opensource-src/libqt5dbus5_5.7.1+dfsg-2ubuntu4~1.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/q/qtbase-opensource-src/qt5-gtk-platformtheme_5.7.1+dfsg-2ubuntu4~1.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/q/qtbase-opensource-src/libqt5network5_5.7.1+dfsg-2ubuntu4~1.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/q/qtbase-opensource-src/libqt5gui5_5.7.1+dfsg-2ubuntu4~1.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/q/qtbase-opensource-src/libqt5widgets5_5.7.1+dfsg-2ubuntu4~1.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/q/qtbase-opensource-src/libqt5opengl5_5.7.1+dfsg-2ubuntu4~1.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/q/qtbase-opensource-src/libqt5printsupport5_5.7.1+dfsg-2ubuntu4~1.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/q/qtbase-opensource-src/libqt5sql5_5.7.1+dfsg-2ubuntu4~1.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/q/qtbase-opensource-src/libqt5sql5-sqlite_5.7.1+dfsg-2ubuntu4~1.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/q/qtbase-opensource-src/libqt5test5_5.7.1+dfsg-2ubuntu4~1.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://ci.archive.ubuntu.com/ubuntu/pool/main/q/qtbase-opensource-src/libqt5xml5_5.7.1+dfsg-2ubuntu4~1.17.04.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_4.10.0-30.34_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.19.3-1ubuntu1.1_all.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xmir_1.19.3-1ubuntu1.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.19.3-1ubuntu1.1_i386.deb  404  Not Found [IP: 91.189.88.152 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by slickymaster on 2018-02-25
> **asifnaz said:**
> ```
asif@asif-HP-ProBook-4330s:~$ sudo apt-get update
[sudo] password for asif: 
Ign:1 http://security.ubuntu.com/ubuntu zesty-security InRelease            
Err:2 http://security.ubuntu.com/ubuntu zesty-security Release
  404  Not Found [IP: 91.189.91.26 80]
Ign:3 http://ci.archive.ubuntu.com/ubuntu zesty InRelease
Ign:4 http://ci.archive.ubuntu.com/ubuntu zesty-updates InRelease
Ign:5 http://ci.archive.ubuntu.com/ubuntu zesty-backports InRelease
Err:6 http://ci.archive.ubuntu.com/ubuntu zesty Release
  404  Not Found [IP: 91.189.88.161 80]
Err:7 http://ci.archive.ubuntu.com/ubuntu zesty-updates Release
  404  Not Found [IP: 91.189.88.161 80]
Err:8 http://ci.archive.ubuntu.com/ubuntu zesty-backports Release
  404  Not Found [IP: 91.189.88.161 80]
Reading package lists... Done
[COLOR=#FF0000][B]E: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ci.archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ci.archive.ubuntu.com/ubuntu zesty-updates Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ci.archive.ubuntu.com/ubuntu zesty-backports Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.[/B][/COLOR]
asif@asif-HP-ProBook-4330s:~$ sudo apt-get upgrade...snip...

```

apt is telling you what is the problem, Zesty is EOL since January and its repos were moved from archive.ubuntu.com to old-releases.ubuntu.com. The reason for this is that it is now out of support and no longer receiving updates and security patches.

I advise you to upgrade to a supported version, 17.10 or 16.04

---

