---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2022-11-27
forum: General Help
---

### Post by mfleming on 2022-11-27
I am getting this after installing the package libopencv-dev on Ubuntu 22.04. 

I have tried various things, but nothing works:

sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libopencv-highgui-dev:amd64:
 libopencv-highgui-dev:amd64 depends on libdc1394-dev; however:
  Package libdc1394-dev:amd64 is not installed.
  Etc

udo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  crda libflashrom1 libftdi1-2
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libdc1394-dev
The following NEW packages will be installed:
  libdc1394-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0 B/116 kB of archives.
After this operation, 540 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 453509 files and directories currently installed.)
Preparing to unpack .../libdc1394-dev_2.2.6-4_amd64.deb ...
Unpacking libdc1394-dev:amd64 (2.2.6-4) ...
dpkg: error processing archive /var/cache/apt/archives/libdc1394-dev_2.2.6-4_amd64.deb (--unpack):
 trying to overwrite '/usr/include/dc1394/camera.h', which is also in package libdc1394-22-dev:amd64 2.2.5-2.1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libdc1394-dev_2.2.6-4_amd64.deb
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)

sudo apt-get remove --purge libopencv-dev
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libopencv-highgui-dev : Depends: libdc1394-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

Assistance would be greatly appreciated.

Matthew Fleming

---

### Post by Impavidus on 2022-11-28
There's a conflict between libdc1394-dev and libdc1394-22-dev. The latter package was used in older releases of Ubuntu, but no longer in 22.04 (which has libdc1394-25-dev). Try to remove it:```
sudo dpkg --remove libdc1394-22-dev
sudo apt install -f
```

---

### Post by mfleming on 2022-11-28
It worked! Thank you very very much!

---

