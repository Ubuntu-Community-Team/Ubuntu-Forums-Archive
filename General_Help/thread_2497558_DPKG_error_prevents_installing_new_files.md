---
title: "DPKG error prevents installing new files"
date: 2024-05-09
forum: General Help
---

### Post by timf34 on 2024-05-09
Hi there,

I am currently unable to run any sort of `sudo apt install [package]` commands on my Nvidia Jetson Orin Nano (running Ubuntu 20.04)

When I try to install a package, I get the following error (full logs below):
```
dpkg: unrecoverable fatal error, aborting:
 loading files list file for package 'evince-common': cannot open /var/lib/dpkg/info/evince-common.list (Bad message)
```

I have verified that that file exists, however when I open it it is empty.

I have tried to rename and remove the file, however that doesn't work:
```
fov@marvel-fov-7:/var/lib/dpkg/info$ sudo rm evince-common.list
rm: cannot remove 'evince-common.list': Bad message
fov@marvel-fov-7:/var/lib/dpkg/info$ sudo mv /var/lib/dpkg/info/evince-common.list /var/lib/dpkg/info/evince-common.list.bak
mv: cannot stat '/var/lib/dpkg/info/evince-common.list': Bad message
```

I have also tried to reinstall dpkg, however that doesn't work either, resulting in the same error:
```
sudo apt-get install --reinstall dpkg
...
After this operation, 0 B of additional disk space will be used.
debconf: Delaying package configuration, since apt-utils is not installed.
dpkg: unrecoverable fatal error, aborting:
 loading files list file for package 'evince-common': cannot open /var/lib/dpkg/info/evince-common.list (Bad message)
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Running `sudo reboot` doesn't change anything either.

Sample full logs:
```
fov@marvel-fov-7:~$ sudo apt install curl
[sudo] password for fov: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb bogl-bterm busybox-static cryptsetup-bin dctrl-tools dpkg-repack gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 grub-common
  libdebian-installer4 libtimezonemap-data libtimezonemap1 os-prober python3-icu python3-pam rdate tasksel tasksel-data
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libcurl4
The following NEW packages will be installed
  curl
The following packages will be upgraded:
  libcurl4
1 to upgrade, 1 to newly install, 0 to remove and 361 not to upgrade.
Need to get 0 B/372 kB of archives.
After this operation, 396 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: Delaying package configuration, since apt-utils is not installed.
dpkg: unrecoverable fatal error, aborting:
 loading files list file for package 'evince-common': cannot open /var/lib/dpkg/info/evince-common.list (Bad message)
E: Sub-process /usr/bin/dpkg returned an error code (2)
fov@marvel-fov-7:~$ sudo rm /var/lib/dpkg/info/evince-common.list
rm: cannot remove '/var/lib/dpkg/info/evince-common.list': Bad message
fov@marvel-fov-7:~$ sudo apt-get install --reinstall dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb bogl-bterm busybox-static cryptsetup-bin dctrl-tools dpkg-repack gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 grub-common
  libdebian-installer4 libtimezonemap-data libtimezonemap1 os-prober python3-icu python3-pam rdate tasksel tasksel-data
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 1 reinstalled, 0 to remove and 362 not to upgrade.
Need to get 1,112 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) focal-updates/main arm64 dpkg arm64 1.19.7ubuntu3.2 [1,112 kB]
Fetched 1,112 kB in 6s (177 kB/s)                                                                                                                              
debconf: Delaying package configuration, since apt-utils is not installed.
dpkg: unrecoverable fatal error, aborting:
 loading files list file for package 'evince-common': cannot open /var/lib/dpkg/info/evince-common.list (Bad message)
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

