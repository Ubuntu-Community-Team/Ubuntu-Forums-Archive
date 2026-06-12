---
title: "glibc for Flash in FF, ultimately for Amazon Prime videos"
date: 2012-11-08
forum: General Help
---

### Post by solitario on 2012-11-08
Hi all. I need to install glibc, so I can install the Flash plugin rpm for Firefox (Chromium was taking me in circles regarding the plugin being installed, but not enabled) so I can watch videos on Amazon Prime.

Any help is appreciated, thanks.

```
kyle@ubuntu:~/Desktop$ rpm -i flash-plugin-11.2.202.251-release.x86_64.rpm
The program 'rpm' is currently not installed.  You can install it by typing:
sudo apt-get install rpm
kyle@ubuntu:~/Desktop$ sudo apt-get install rpm
[sudo] password for kyle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcommons-jci-java libsvga1 libbabl-0.0-0 libgegl-0.0-0 python-support
  python-gdata libcommons-io-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  librpm2 librpmbuild2 librpmio2 librpmsign0 rpm-common rpm2cpio
Suggested packages:
  alien elfutils rpm-i18n
The following NEW packages will be installed:
  librpm2 librpmbuild2 librpmio2 librpmsign0 rpm rpm-common rpm2cpio
0 upgraded, 7 newly installed, 0 to remove and 29 not upgraded.
Need to get 525 kB of archives.
After this operation, 1,687 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ precise/main librpmio2 amd64 4.9.1.1-1build1 [82.2 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ precise/main rpm-common amd64 4.9.1.1-1build1 [20.0 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ precise/main librpm2 amd64 4.9.1.1-1build1 [186 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ precise/main librpmbuild2 amd64 4.9.1.1-1build1 [69.8 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ precise/main librpmsign0 amd64 4.9.1.1-1build1 [8,844 B]
Get:6 http://archive.ubuntu.com/ubuntu/ precise/main rpm2cpio amd64 4.9.1.1-1build1 [5,152 B]
Get:7 http://archive.ubuntu.com/ubuntu/ precise/main rpm amd64 4.9.1.1-1build1 [153 kB]
Fetched 525 kB in 1s (482 kB/s)
Selecting previously unselected package librpmio2.
(Reading database ... 328917 files and directories currently installed.)
Unpacking librpmio2 (from .../librpmio2_4.9.1.1-1build1_amd64.deb) ...
Selecting previously unselected package rpm-common.
Unpacking rpm-common (from .../rpm-common_4.9.1.1-1build1_amd64.deb) ...
Selecting previously unselected package librpm2.
Unpacking librpm2 (from .../librpm2_4.9.1.1-1build1_amd64.deb) ...
Selecting previously unselected package librpmbuild2.
Unpacking librpmbuild2 (from .../librpmbuild2_4.9.1.1-1build1_amd64.deb) ...
Selecting previously unselected package librpmsign0.
Unpacking librpmsign0 (from .../librpmsign0_4.9.1.1-1build1_amd64.deb) ...
Selecting previously unselected package rpm2cpio.
Unpacking rpm2cpio (from .../rpm2cpio_4.9.1.1-1build1_amd64.deb) ...
Selecting previously unselected package rpm.
Unpacking rpm (from .../rpm_4.9.1.1-1build1_amd64.deb) ...
Processing triggers for man-db ...
Setting up librpmio2 (4.9.1.1-1build1) ...
Setting up rpm-common (4.9.1.1-1build1) ...
Setting up librpm2 (4.9.1.1-1build1) ...
Setting up librpmbuild2 (4.9.1.1-1build1) ...
Setting up librpmsign0 (4.9.1.1-1build1) ...
Setting up rpm2cpio (4.9.1.1-1build1) ...
Setting up rpm (4.9.1.1-1build1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
kyle@ubuntu:~/Desktop$ rpm -i flash-plugin-11.2.202.251-release.x86_64.rpm
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
error: Failed dependencies:
	glibc >= 2.4 is needed by flash-plugin-11.2.202.251-release.x86_64
	/bin/sh is needed by flash-plugin-11.2.202.251-release.x86_64
kyle@ubuntu:~/Desktop$ sudo apt-get install glibc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package glibc
kyle@ubuntu:~/Desktop$ 
```

---

### Post by ajgreeny on 2012-11-08
Why are you trying to use the rpm flash package?  There are deb packages available, or failing that you can use the adobe site and download the tar.gz version, extract it and then copy or move the libflashplayer.so file it contains to /usr/lib/adobe-flashplugin or usr/lib/flashplugin-installer, which you may need to make first with sudo mkdir /usr/lib/adobe-flashplugin (or flashplugin-installer).

---

