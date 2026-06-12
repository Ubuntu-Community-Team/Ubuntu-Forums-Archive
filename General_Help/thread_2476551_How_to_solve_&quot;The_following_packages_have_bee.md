---
title: "How to solve &quot;The following packages have been kept back' ?"
date: 2022-06-29
forum: General Help
---

### Post by satimis on 2022-06-29
Hi all,

Ubuntu 22.04 desktop running as VM of Oracle VirtualBox

$ sudo apt update```

Hit:1 https://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:3 http://hk.archive.ubuntu.com/ubuntu jammy InRelease                    
Hit:4 http://hk.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:5 http://hk.archive.ubuntu.com/ubuntu jammy-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.

```

$ sudo apt upgrade```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnome-remote-desktop
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Please advise how to solve the problem.  Thanks in advance.

Regards

---

### Post by #&amp;thj^% on 2022-06-29
What happens if you run this exactly:
```
sudo apt-get --with-new-pkgs upgrade
```
This allows new packages to be installed. It will let you know what packages would be installed and prompt you before actually doing the install.

---

### Post by satimis on 2022-06-29
> **1fallen said:**
> What happens if you run this exactly:
```
sudo apt-get --with-new-pkgs upgrade
```
$ sudo apt-get --with-new-pkgs upgrade
```
 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnome-remote-desktop
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Regards

---

### Post by #&amp;thj^% on 2022-06-29
> **satimis said:**
> $ sudo apt-get --with-new-pkgs upgrade
```
 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnome-remote-desktop
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Regards

Thanks, Normally, when you run the sudo apt update and sudo apt upgrade commands, it updates all the installed packages to their available newer versions.

However, if the dependencies of an installed package have been changed such that it requires installation of new packages, the installed package won’t be upgraded with the system update and you’ll see package kept back error.
Now try:
```
sudo apt install  gnome-remote-desktop
```

---

### Post by satimis on 2022-06-29
> **1fallen said:**
> Thanks, Normally, when you run the sudo apt update and sudo apt upgrade commands, it updates all the installed packages to their available newer versions.

However, if the dependencies of an installed package have been changed such that it requires installation of new packages, the installed package won’t be upgraded with the system update and you’ll see package kept back error.
Now try:
```
sudo apt install  gnome-remote-desktop
```
gnome-remote-desktop already installed.

$ apt policy gnome-remote-desktop```

gnome-remote-desktop:
  Installed: 42.0-4ubuntu1
  Candidate: 42.1.1-0ubuntu1
  Version table:
     42.1.1-0ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
 *** 42.0-4ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```

Regards

---

### Post by #&amp;thj^% on 2022-06-29
Ok I jumped the gun a bit:
```
sudo apt remove gnome-remote-desktop
```
and 
```
 sudo apt autoremove
```
and again:
```
sudo apt install gnome-remote-desktop
```
On my KVM I'll see:
```
The following packages have been kept back:
  linux-generic-hwe-22.04 linux-headers-generic-hwe-22.04
  linux-image-generic-hwe-22.04
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```
which was fixed with:
```
sudo apt install linux-generic-hwe-22.04 linux-headers-generic-hwe-22.04
  linux-image-generic-hwe-22.04
[sudo] password for me: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  linux-image-generic-hwe-22.04
The following held packages will be changed:
  linux-generic-hwe-22.04
The following packages will be upgraded:
  linux-generic-hwe-22.04 linux-headers-generic-hwe-22.04
  linux-image-generic-hwe-22.04
3 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
Need to get 6,718 B of archives.
After this operation, 3,072 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-generic-hwe-22.04 amd64 5.15.0.40.42 [1,670 B]
Get:2 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-image-generic-hwe-22.04 amd64 5.15.0.40.42 [2,592 B]
Get:3 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-headers-generic-hwe-22.04 amd64 5.15.0.40.42 [2,456 B]
Fetched 6,718 B in 1s (11.6 kB/s)                           
(Reading database ... 268511 files and directories currently installed.)
Preparing to unpack .../linux-generic-hwe-22.04_5.15.0.40.42_amd64.deb ...
Unpacking linux-generic-hwe-22.04 (5.15.0.40.42) over (5.15.0.27.30) ...
Preparing to unpack .../linux-image-generic-hwe-22.04_5.15.0.40.42_amd64.deb ...
Unpacking linux-image-generic-hwe-22.04 (5.15.0.40.42) over (5.15.0.27.30) ...
Preparing to unpack .../linux-headers-generic-hwe-22.04_5.15.0.40.42_amd64.deb .
..
Unpacking linux-headers-generic-hwe-22.04 (5.15.0.40.42) over (5.15.0.27.30) ...
Setting up linux-image-generic-hwe-22.04 (5.15.0.40.42) ...
Setting up linux-headers-generic-hwe-22.04 (5.15.0.40.42) ...
Setting up linux-generic-hwe-22.04 (5.15.0.40.42) ...
linux-image-generic-hwe-22.04: command not found

```
And again I'll run:
```
sudo apt upgrade
sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  curl libcurl3-gnutls libcurl3-nss libcurl4 libmozjs-91-0 libnss-systemd
  libpam-systemd libsystemd0 libudev1 systemd systemd-oomd systemd-sysv
  systemd-timesyncd udev
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 standard security updates
Need to get 6,944 kB/12.1 MB of archives.
After this operation, 62.5 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 systemd-timesyncd amd64 249.11-0ubuntu3.3 [31.2 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libsystemd0 amd64 249.11-0ubuntu3.3 [318 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libnss-systemd amd64 249.11-0ubuntu3.3 [133 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 systemd-sysv amd64 249.11-0ubuntu3.3 [10.5 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 systemd-oomd amd64 249.11-0ubuntu3.3 [34.8 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libpam-systemd amd64 249.11-0ubuntu3.3 [203 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 systemd amd64 249.11-0ubuntu3.3 [4,579 kB]
Get:8 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 udev amd64 249.11-0ubuntu3.3 [1,557 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libudev1 amd64 249.11-0ubuntu3.3 [77.4 kB]
Fetched 6,944 kB in 1s (5,230 kB/s)
(Reading database ... 268511 files and directories currently installed.)
Preparing to unpack .../systemd-timesyncd_249.11-0ubuntu3.3_amd64.deb ...
Unpacking systemd-timesyncd (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Preparing to unpack .../libsystemd0_249.11-0ubuntu3.3_amd64.deb ...
Unpacking libsystemd0:amd64 (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Setting up libsystemd0:amd64 (249.11-0ubuntu3.3) ...
(Reading database ... 268511 files and directories currently installed.)
Preparing to unpack .../0-libnss-systemd_249.11-0ubuntu3.3_amd64.deb ...
Unpacking libnss-systemd:amd64 (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Preparing to unpack .../1-systemd-sysv_249.11-0ubuntu3.3_amd64.deb ...
Unpacking systemd-sysv (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Preparing to unpack .../2-systemd-oomd_249.11-0ubuntu3.3_amd64.deb ...
Unpacking systemd-oomd (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Preparing to unpack .../3-libpam-systemd_249.11-0ubuntu3.3_amd64.deb ...
Unpacking libpam-systemd:amd64 (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Preparing to unpack .../4-systemd_249.11-0ubuntu3.3_amd64.deb ...
Unpacking systemd (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Preparing to unpack .../5-udev_249.11-0ubuntu3.3_amd64.deb ...
Unpacking udev (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Preparing to unpack .../6-libudev1_249.11-0ubuntu3.3_amd64.deb ...
Unpacking libudev1:amd64 (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Setting up libudev1:amd64 (249.11-0ubuntu3.3) ...
(Reading database ... 268511 files and directories currently installed.)
Preparing to unpack .../curl_7.81.0-1ubuntu1.3_amd64.deb ...
Unpacking curl (7.81.0-1ubuntu1.3) over (7.81.0-1ubuntu1.2) ...
Preparing to unpack .../libcurl4_7.81.0-1ubuntu1.3_amd64.deb ...
Unpacking libcurl4:amd64 (7.81.0-1ubuntu1.3) over (7.81.0-1ubuntu1.2) ...
Preparing to unpack .../libcurl3-gnutls_7.81.0-1ubuntu1.3_amd64.deb ...
Unpacking libcurl3-gnutls:amd64 (7.81.0-1ubuntu1.3) over (7.81.0-1ubuntu1.2) ...
Preparing to unpack .../libcurl3-nss_7.81.0-1ubuntu1.3_amd64.deb ...
Unpacking libcurl3-nss:amd64 (7.81.0-1ubuntu1.3) over (7.81.0-1ubuntu1.2) ...
Preparing to unpack .../libmozjs-91-0_91.10.0-0ubuntu1_amd64.deb ...
Unpacking libmozjs-91-0:amd64 (91.10.0-0ubuntu1) over (91.7.0-2) ...
Setting up libmozjs-91-0:amd64 (91.10.0-0ubuntu1) ...
Setting up libcurl3-gnutls:amd64 (7.81.0-1ubuntu1.3) ...
Setting up systemd (249.11-0ubuntu3.3) ...
Setting up systemd-timesyncd (249.11-0ubuntu3.3) ...
Setting up udev (249.11-0ubuntu3.3) ...
Setting up libcurl3-nss:amd64 (7.81.0-1ubuntu1.3) ...
Setting up systemd-oomd (249.11-0ubuntu3.3) ...
Setting up libcurl4:amd64 (7.81.0-1ubuntu1.3) ...
Setting up curl (7.81.0-1ubuntu1.3) ...
Setting up systemd-sysv (249.11-0ubuntu3.3) ...
Setting up libnss-systemd:amd64 (249.11-0ubuntu3.3) ...
Setting up libpam-systemd:amd64 (249.11-0ubuntu3.3) ...
Processing triggers for libc-bin (2.35-0ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for dbus (1.12.20-2ubuntu4) ...
Processing triggers for initramfs-tools (0.140ubuntu13) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-40-generic
me@me-Standard-PC-Q35-ICH9-2009:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by satimis on 2022-06-29
> **1fallen said:**
> Ok I jumped the gun a bit:
```
sudo apt remove gnome-remote-desktop
```
and 
```
 sudo apt autoremove
```
and again:
```
sudo apt install gnome-remote-desktop
```
On my KVM I'll see:
```
The following packages have been kept back:
  linux-generic-hwe-22.04 linux-headers-generic-hwe-22.04
  linux-image-generic-hwe-22.04
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```
which was fixed with:
```
sudo apt install linux-generic-hwe-22.04 linux-headers-generic-hwe-22.04
  linux-image-generic-hwe-22.04
[sudo] password for me: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  linux-image-generic-hwe-22.04
The following held packages will be changed:
  linux-generic-hwe-22.04
The following packages will be upgraded:
  linux-generic-hwe-22.04 linux-headers-generic-hwe-22.04
  linux-image-generic-hwe-22.04
3 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
Need to get 6,718 B of archives.
After this operation, 3,072 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-generic-hwe-22.04 amd64 5.15.0.40.42 [1,670 B]
Get:2 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-image-generic-hwe-22.04 amd64 5.15.0.40.42 [2,592 B]
Get:3 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-headers-generic-hwe-22.04 amd64 5.15.0.40.42 [2,456 B]
Fetched 6,718 B in 1s (11.6 kB/s)                           
(Reading database ... 268511 files and directories currently installed.)
Preparing to unpack .../linux-generic-hwe-22.04_5.15.0.40.42_amd64.deb ...
Unpacking linux-generic-hwe-22.04 (5.15.0.40.42) over (5.15.0.27.30) ...
Preparing to unpack .../linux-image-generic-hwe-22.04_5.15.0.40.42_amd64.deb ...
Unpacking linux-image-generic-hwe-22.04 (5.15.0.40.42) over (5.15.0.27.30) ...
Preparing to unpack .../linux-headers-generic-hwe-22.04_5.15.0.40.42_amd64.deb .
..
Unpacking linux-headers-generic-hwe-22.04 (5.15.0.40.42) over (5.15.0.27.30) ...
Setting up linux-image-generic-hwe-22.04 (5.15.0.40.42) ...
Setting up linux-headers-generic-hwe-22.04 (5.15.0.40.42) ...
Setting up linux-generic-hwe-22.04 (5.15.0.40.42) ...
linux-image-generic-hwe-22.04: command not found

```
And again I'll run:
```
sudo apt upgrade
sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  curl libcurl3-gnutls libcurl3-nss libcurl4 libmozjs-91-0 libnss-systemd
  libpam-systemd libsystemd0 libudev1 systemd systemd-oomd systemd-sysv
  systemd-timesyncd udev
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 standard security updates
Need to get 6,944 kB/12.1 MB of archives.
After this operation, 62.5 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 systemd-timesyncd amd64 249.11-0ubuntu3.3 [31.2 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libsystemd0 amd64 249.11-0ubuntu3.3 [318 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libnss-systemd amd64 249.11-0ubuntu3.3 [133 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 systemd-sysv amd64 249.11-0ubuntu3.3 [10.5 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 systemd-oomd amd64 249.11-0ubuntu3.3 [34.8 kB]
Get:6 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libpam-systemd amd64 249.11-0ubuntu3.3 [203 kB]
Get:7 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 systemd amd64 249.11-0ubuntu3.3 [4,579 kB]
Get:8 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 udev amd64 249.11-0ubuntu3.3 [1,557 kB]
Get:9 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libudev1 amd64 249.11-0ubuntu3.3 [77.4 kB]
Fetched 6,944 kB in 1s (5,230 kB/s)
(Reading database ... 268511 files and directories currently installed.)
Preparing to unpack .../systemd-timesyncd_249.11-0ubuntu3.3_amd64.deb ...
Unpacking systemd-timesyncd (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Preparing to unpack .../libsystemd0_249.11-0ubuntu3.3_amd64.deb ...
Unpacking libsystemd0:amd64 (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Setting up libsystemd0:amd64 (249.11-0ubuntu3.3) ...
(Reading database ... 268511 files and directories currently installed.)
Preparing to unpack .../0-libnss-systemd_249.11-0ubuntu3.3_amd64.deb ...
Unpacking libnss-systemd:amd64 (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Preparing to unpack .../1-systemd-sysv_249.11-0ubuntu3.3_amd64.deb ...
Unpacking systemd-sysv (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Preparing to unpack .../2-systemd-oomd_249.11-0ubuntu3.3_amd64.deb ...
Unpacking systemd-oomd (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Preparing to unpack .../3-libpam-systemd_249.11-0ubuntu3.3_amd64.deb ...
Unpacking libpam-systemd:amd64 (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Preparing to unpack .../4-systemd_249.11-0ubuntu3.3_amd64.deb ...
Unpacking systemd (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Preparing to unpack .../5-udev_249.11-0ubuntu3.3_amd64.deb ...
Unpacking udev (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Preparing to unpack .../6-libudev1_249.11-0ubuntu3.3_amd64.deb ...
Unpacking libudev1:amd64 (249.11-0ubuntu3.3) over (249.11-0ubuntu3.1) ...
Setting up libudev1:amd64 (249.11-0ubuntu3.3) ...
(Reading database ... 268511 files and directories currently installed.)
Preparing to unpack .../curl_7.81.0-1ubuntu1.3_amd64.deb ...
Unpacking curl (7.81.0-1ubuntu1.3) over (7.81.0-1ubuntu1.2) ...
Preparing to unpack .../libcurl4_7.81.0-1ubuntu1.3_amd64.deb ...
Unpacking libcurl4:amd64 (7.81.0-1ubuntu1.3) over (7.81.0-1ubuntu1.2) ...
Preparing to unpack .../libcurl3-gnutls_7.81.0-1ubuntu1.3_amd64.deb ...
Unpacking libcurl3-gnutls:amd64 (7.81.0-1ubuntu1.3) over (7.81.0-1ubuntu1.2) ...
Preparing to unpack .../libcurl3-nss_7.81.0-1ubuntu1.3_amd64.deb ...
Unpacking libcurl3-nss:amd64 (7.81.0-1ubuntu1.3) over (7.81.0-1ubuntu1.2) ...
Preparing to unpack .../libmozjs-91-0_91.10.0-0ubuntu1_amd64.deb ...
Unpacking libmozjs-91-0:amd64 (91.10.0-0ubuntu1) over (91.7.0-2) ...
Setting up libmozjs-91-0:amd64 (91.10.0-0ubuntu1) ...
Setting up libcurl3-gnutls:amd64 (7.81.0-1ubuntu1.3) ...
Setting up systemd (249.11-0ubuntu3.3) ...
Setting up systemd-timesyncd (249.11-0ubuntu3.3) ...
Setting up udev (249.11-0ubuntu3.3) ...
Setting up libcurl3-nss:amd64 (7.81.0-1ubuntu1.3) ...
Setting up systemd-oomd (249.11-0ubuntu3.3) ...
Setting up libcurl4:amd64 (7.81.0-1ubuntu1.3) ...
Setting up curl (7.81.0-1ubuntu1.3) ...
Setting up systemd-sysv (249.11-0ubuntu3.3) ...
Setting up libnss-systemd:amd64 (249.11-0ubuntu3.3) ...
Setting up libpam-systemd:amd64 (249.11-0ubuntu3.3) ...
Processing triggers for libc-bin (2.35-0ubuntu3) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for dbus (1.12.20-2ubuntu4) ...
Processing triggers for initramfs-tools (0.140ubuntu13) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-40-generic
me@me-Standard-PC-Q35-ICH9-2009:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Thanks for your advice.

$ apt policy linux-generic-hwe-22.04```

linux-generic-hwe-22.04:
  Installed: 5.15.0.40.42
  Candidate: 5.15.0.40.42
  Version table:
 *** 5.15.0.40.42 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     5.15.0.39.40 500
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
     5.15.0.25.27 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

$ apt policy linux-headers-generic-hwe-22.04```

linux-headers-generic-hwe-22.04:
  Installed: 5.15.0.40.42
  Candidate: 5.15.0.40.42
  Version table:
 *** 5.15.0.40.42 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     5.15.0.39.40 500
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
     5.15.0.25.27 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

$ apt policy linux-image-generic-hwe-22.04```

linux-image-generic-hwe-22.04:
  Installed: 5.15.0.40.42
  Candidate: 5.15.0.40.42
  Version table:
 *** 5.15.0.40.42 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     5.15.0.39.40 500
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
     5.15.0.25.27 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

Those 3 packages are already installed.

Regards

---

### Post by #&amp;thj^% on 2022-06-29
I either over explain or under explain, I was just showing the difference's to fix held packages. ;)
Have you tried to uninstall and reinstall "gnome-remote-desktop" yet?
If there is still a problem check to make sure all dependencies are fulfilled:
```
$ apt-cache depends gnome-remote-desktop
gnome-remote-desktop
 |Depends: dconf-gsettings-backend
  Depends: <gsettings-backend>
    dconf-gsettings-backend
  Depends: init-system-helpers
  Depends: libc6
  Depends: libcairo2
  Depends: libepoxy0
  Depends: libfreerdp-client2-2
  Depends: libfreerdp-server2-2
  Depends: libfreerdp2-2
  Depends: libfuse3-3
  Depends: libglib2.0-0
  Depends: libnotify4
  Depends: libpipewire-0.3-0
  Depends: libsecret-1-0
  Depends: libvncserver1
  Depends: libwinpr2-2
  Depends: libxkbcommon0
  Depends: fuse3
  Depends: libmutter-10-0
  Depends: pipewire
 |Depends: pipewire-media-session
  Depends: wireplumber
  Breaks: gnome-control-center

```
I found this interesting>>"**Breaks: gnome-control-center**"
And yet they exist together:
```
me@me-Standard-PC-Q35-ICH9-2009:~$ apt policy gnome-control-center
[B]gnome-control-center:
  Installed: 1:41.7-0ubuntu0.22.04.1[/B]
  Candidate: 1:41.7-0ubuntu0.22.04.1
  Version table:
 *** 1:41.7-0ubuntu0.22.04.1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:41.4-1ubuntu13.2 500
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
     1:41.4-1ubuntu12 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
me@me-Standard-PC-Q35-ICH9-2009:~$ apt policy gnome-remote-desktop
[B]gnome-remote-desktop:
  Installed: 42.1.1-0ubuntu1[/B]
  Candidate: 42.1.1-0ubuntu1
  Version table:
 *** 42.1.1-0ubuntu1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     42.0-4ubuntu1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

---

### Post by Impavidus on 2022-06-29
> **1fallen said:**
> 
However, if the dependencies of an installed package have been changed such that it requires installation of new packages, the installed package won&#8217;t be upgraded with the system update and you&#8217;ll see package kept back error.
That's the case for apt-get upgrade, but apt upgrade will happily install new packages to satisfy dependencies.

You can try```
sudo apt update
sudo apt upgrade gnome-remote-desktop
```Maybe it tells you why it cannot be upgraded.

I wouldn't worry too much about this. Maybe some dependency is late. If the problem is still there in three days, start worrying.

---

### Post by #&amp;thj^% on 2022-06-29
> **Impavidus said:**
> That's the case for apt-get upgrade, but apt upgrade will happily install new packages to satisfy dependencies.

You can try```
sudo apt update
sudo apt upgrade gnome-remote-desktop
```Maybe it tells you why it cannot be upgraded.

I wouldn't worry too much about this. Maybe some dependency is late. If the problem is still there in three days, start worrying.

Usually yes but in this case it did not, on both the OP's and mine:
```
The following packages have been kept back:
  linux-generic-hwe-22.04 linux-headers-generic-hwe-22.04
  linux-image-generic-hwe-22.04
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```
That was the apt upgrade and not apt-get upgrade

---

### Post by satimis on 2022-06-29
Hi all,

I solved my problem running following step;

$ sudo apt dist-upgrade```

....
....
update-initramfs: deferring update (trigger activated)
Selecting previously unselected package fuse3.
(Reading database ... 251336 files and directories currently installed.)
Preparing to unpack .../fuse3_3.10.5-1build1_amd64.deb ...
Unpacking fuse3 (3.10.5-1build1) ...
Preparing to unpack .../gnome-remote-desktop_42.1.1-0ubuntu1_amd64.deb ...
Unpacking gnome-remote-desktop (42.1.1-0ubuntu1) over (42.0-4ubuntu1) ...
Setting up fuse3 (3.10.5-1build1) ...
Installing new version of config file /etc/fuse.conf ...
update-initramfs: deferring update (trigger activated)
Setting up gnome-remote-desktop (42.1.1-0ubuntu1) ...
Disable user unit that shouldn't have been auto enabled
Processing triggers for libglib2.0-0:amd64 (2.72.1-1) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for initramfs-tools (0.140ubuntu13) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-40-generic
I: The initramfs will attempt to resume from /dev/dm-1
I: (/dev/mapper/vgubuntu-swap_1)
I: Set the RESUME variable to override this.

```

$ sudo apt update```

Hit:1 https://dl.google.com/linux/chrome/deb stable InRelease
Get:2 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]                  
Hit:3 http://hk.archive.ubuntu.com/ubuntu jammy InRelease
Hit:4 http://hk.archive.ubuntu.com/ubuntu jammy-updates InRelease
Get:5 http://hk.archive.ubuntu.com/ubuntu jammy-backports InRelease [99.8 kB]
Fetched 210 kB in 2s (127 kB/s)                                      
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.

```

Anyway.  I'm very appreciated for your time and effort trying to help me.

Thanks again.

Regards

---

### Post by #&amp;thj^% on 2022-06-29
I would take caution using "dist-upgrade" it has a tendency to remove needed packages...."apt full-upgrade" is recommended.

---

### Post by satimis on 2022-06-29
> **1fallen said:**
> I would take caution using "dist-upgrade" it has a tendency to remove needed packages...."apt full-upgrade" is recommended.
Thanks for your advice.  I would take it down.

Regards

---

