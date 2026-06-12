---
title: "Broken dependencies - how to fix / roll back"
date: 2016-03-23
forum: General Help
---

### Post by Deon_Blaauw on 2016-03-23
Hi Guys,

I recently updated Ubuntu, and ran into some dependency issues. When going to the software center, I get the following message when trying to do a repair:

```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 538124 files and directories currently installed.)
Preparing to unpack .../libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb ...
Unpacking libstdc++6-armhf-cross (4.8.4-2ubuntu1~14.04.1cross0.11.1) over (4.8.2-16ubuntu4cross0.11) ...
dpkg: error processing archive /var/cache/apt/archives/libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb (--unpack):
 trying to overwrite '/usr/share/gcc-4.8/python/libstdcxx/__init__.py', which is also in package libstdc++6:i386 4.8.4-2ubuntu1~14.04.1
Errors were encountered while processing:
 /var/cache/apt/archives/libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb
Error in function: 
dpkg: dependency problems prevent configuration of libstdc++-4.8-dev-armhf-cross:
 libstdc++-4.8-dev-armhf-cross depends on libstdc++6-armhf-cross (>= 4.8.4-2ubuntu1~14.04.1cross0.11.1); however:
  Version of libstdc++6-armhf-cross on system is 4.8.2-16ubuntu4cross0.11.


dpkg: error processing package libstdc++-4.8-dev-armhf-cross (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++-4.8-arm-linux-gnueabihf:
 g++-4.8-arm-linux-gnueabihf depends on libstdc++-4.8-dev-armhf-cross (= 4.8.4-2ubuntu1~14.04.1cross0.11.1); however:
  Package libstdc++-4.8-dev-armhf-cross is not configured yet.


dpkg: error processing package g++-4.8-arm-linux-gnueabihf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsfstdc++-4.8-dev-armhf-cross:
 libsfstdc++-4.8-dev-armhf-cross depends on libstdc++-4.8-dev-armhf-cross (= 4.8.4-2ubuntu1~14.04.1cross0.11.1); however:
  Package libstdc++-4.8-dev-armhf-cross is not configured yet.


dpkg: error processing package libsfstdc++-4.8-dev-armhf-cross (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++-4.8-multilib-arm-linux-gnueabihf:
 g++-4.8-multilib-arm-linux-gnueabihf depends on g++-4.8-arm-linux-gnueabihf (= 4.8.4-2ubuntu1~14.04.1cross0.11.1); however:
  Package g++-4.8-arm-linux-gnueabihf is not configured yet.
 g++-4.8-multilib-arm-linux-gnueabihf depends on libsfstdc++-4.8-dev-armhf-cross (= 4.8.4-2ubuntu1~14.04.1cross0.11.1) | libsfstdc++-4.8-dev-armhf-cross; however:
  Package libsfstdc++-4.8-dev-armhf-cross is not configured yet.
  Package libsfstdc++-4.8-dev-armhf-cross is not configured yet.


dpkg: error processing package g++-4.8-multilib-arm-linux-gnueabihf (--configure):
 dependency problems - leaving unconfigured
```

I've already done the following (did not work):
```
sudo apt-get autoclean
sudo apt-get clean
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

I also tried installing the missing package and got this:

```
sudo apt-get install libstdc++6-armhf-cross

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libstdc++6-armhf-cross
0 upgraded, 1 newly installed, 0 to remove and 30 not upgraded.
4 not fully installed or removed.
Need to get 0 B/210 kB of archives.
After this operation, 749 kB of additional disk space will be used.
(Reading database ... 538120 files and directories currently installed.)
Preparing to unpack .../libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb ...
Unpacking libstdc++6-armhf-cross (4.8.4-2ubuntu1~14.04.1cross0.11.1) ...
dpkg: error processing archive /var/cache/apt/archives/libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb (--unpack):
 trying to overwrite '/usr/share/gcc-4.8/python/libstdcxx/__init__.py', which is also in package libstdc++6:i386 4.8.4-2ubuntu1~14.04.1
Errors were encountered while processing:
 /var/cache/apt/archives/libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any idea on how to solve this will be much appreciated!

---

### Post by Deon_Blaauw on 2016-03-23
Update: I managed to resolve it for now.

I used the package manager to simply remove the entire package, after that I ran sudo apt-get autoremove to clean everything out. I think there might be an issue with this specific package and its dependencies.

---

### Post by banescusebi on 2016-03-24
Hi Deon_Blaauw,

I'm having the same problem. Can you please describe your solution more precisely? Which package did you remove before running sudo apt-get autoremove?

Thanks!

---

### Post by banescusebi on 2016-03-24
The following commands fixed my problems:

```

sudo dpkg --purge --force-depends "libstdc++-4.8-dev-armhf-cross"
sudo dpkg --purge --force-depends "libsfstdc++-4.8-dev-armhf-cross"
sudo apt-get install libstdc++6-armhf-cross 
sudo apt-get -f install 

```

---

### Post by Deon_Blaauw on 2016-03-30
In this case, terminal is your friend. I used sudo dpkg --remove --force-remove-reinstreq <package_name> to remove each package until I could install the package manager using sudo apt-get install synaptic. Once synaptic is running, you can see which packages are broken and "bulk-remove" them

---

### Post by cai3 on 2016-04-04
Hello banescusebi!

I run the code you wrote, but I still had errors, why?

After I run:  
```
sudo apt-get -f install  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 libmbim-glib0 libqmi-glib0
  libreoffice-gtk3 libtotem0 linux-headers-4.2.0-27
  linux-headers-4.2.0-27-generic linux-image-4.2.0-27-generic
  linux-image-extra-4.2.0-27-generic linux-signed-image-4.2.0-27-generic
  openbsd-inetd totem-common usb-modeswitch usb-modeswitch-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsfstdc++-4.8-dev-armhf-cross libstdc++-4.8-dev-armhf-cross
  libstdc++6-armhf-cross
The following NEW packages will be installed:
  libsfstdc++-4.8-dev-armhf-cross libstdc++-4.8-dev-armhf-cross
The following packages will be upgraded:
  libstdc++6-armhf-cross
1 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1 634 kB of archives.
After this operation, 16,9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 286544 files and directories currently installed.)
Preparing to unpack .../libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb ...
Unpacking libstdc++6-armhf-cross (4.8.4-2ubuntu1~14.04.1cross0.11.1) over (4.8.2-16ubuntu4cross0.11) ...
dpkg: error processing archive /var/cache/apt/archives/libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb (--unpack):
 trying to overwrite '/usr/share/gcc-4.8/python/libstdcxx/__init__.py', which is also in package libstdc++6:i386 4.8.4-2ubuntu1~14.04.1
Selecting previously unselected package libstdc++-4.8-dev-armhf-cross.
Preparing to unpack .../libstdc++-4.8-dev-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb ...
Unpacking libstdc++-4.8-dev-armhf-cross (4.8.4-2ubuntu1~14.04.1cross0.11.1) ...
Selecting previously unselected package libsfstdc++-4.8-dev-armhf-cross.
Preparing to unpack .../libsfstdc++-4.8-dev-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb ...
Unpacking libsfstdc++-4.8-dev-armhf-cross (4.8.4-2ubuntu1~14.04.1cross0.11.1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Hello Deon_Blaauw, Which packages should I remove? Thank you!


> **Deon_Blaauw said:**
> In this case, terminal is your friend. I used sudo dpkg --remove --force-remove-reinstreq <package_name> to remove each package until I could install the package manager using sudo apt-get install synaptic. Once synaptic is running, you can see which packages are broken and "bulk-remove" them

---

