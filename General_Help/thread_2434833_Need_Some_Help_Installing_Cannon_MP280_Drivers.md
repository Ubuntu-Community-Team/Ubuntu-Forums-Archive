---
title: "Need Some Help Installing Cannon MP280 Drivers"
date: 2020-01-11
forum: General Help
---

### Post by orion20k on 2020-01-11
Hi all after doing a nice clean install on my new desktop system, i went to install my printer drivers for the cannon mp280, i downloaded the drivers from the cannon site. the tar file containd the following,cnijfilter-common_3.40-1_amd64.deb and cnijfilter-mp280series_3.40-1_amd64.deb and the respective manuals it seems the cannon driver depends on libpng12-0_1.2.54-1ubuntu1_amd64 & libtiff4_3.9.7-2ubuntu1_amd64  and [COLOR=#000000][FONT=monospace]libpango1.0-0

[/FONT][/COLOR]```

System Infromation:

Operating System: Kubuntu 19.10
KDE Plasma Version: 5.16.5
KDE Frameworks Version: 5.62.0
Qt Version: 5.12.4
Kernel Version: 5.3.0-26-generic
OS Type: 64-bit
Processors: 2 × AMD E1-1200 APU with Radeon(tm) HD Graphics
Memory: 1.7 GiB of RAM

```


[FONT=monospace][COLOR=#000000]libpango1.0-0 installes no problem thanks apt[/COLOR]
[/FONT]


libtiff4_3.9.7-2ubuntu1_amd64.deb installs no problem thanks again apt

In a rare twist i had to downlad and install the multiarch-support_2.29-0ubuntu2_amd64.deb package


when i try to install libpng12 i get the following


```
 sudo dpkg -i libpng12-0_1.2.54-1ubuntu1_amd64.deb
(Reading database ... 232849 files and directories currently installed.)
Preparing to unpack libpng12-0_1.2.54-1ubuntu1_amd64.deb ...
Unpacking libpng12-0:amd64 (1.2.54-1ubuntu1) ...
dpkg: error processing archive libpng12-0_1.2.54-1ubuntu1_amd64.deb (--install):
 unable to install new version of '/lib/x86_64-linux-gnu/libpng12.so.0': No such file or directory
Processing triggers for libc-bin (2.30-0ubuntu2) ...
Errors were encountered while processing:
 libpng12-0_1.2.54-1ubuntu1_amd64.deb

```


when i try to install cnijfilter-common_3.40-1_amd64.deb it throws me an error because of the problem with libpng12


```

sudo dpkg -i cnijfilter-mp280series_3.40-1_amd64.deb[sudo] password for yoda: 
Selecting previously unselected package cnijfilter-mp280series.
(Reading database ... 232645 files and directories currently installed.)
Preparing to unpack cnijfilter-mp280series_3.40-1_amd64.deb ...
Unpacking cnijfilter-mp280series (3.40-1) ...
dpkg: dependency problems prevent configuration of cnijfilter-mp280series:
 cnijfilter-mp280series depends on libpng12-0 (>= 1.2.8rel); however:
  Package libpng12-0:amd64 is not installed.


dpkg: error processing package cnijfilter-mp280series (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-mp280series

```

the problem seems to be libpng12 im not sure whats going on to stop it installing

---

