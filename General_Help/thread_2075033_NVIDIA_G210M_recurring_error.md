---
title: "NVIDIA G210M recurring error"
date: 2012-10-22
forum: General Help
---

### Post by n1tsuj3 on 2012-10-22
Any time I install a new application I run into a 'package operation failed' error
```
installArchives() failed: Selecting previously unselected package libboost-system1.46.1.
(Reading database ... 
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
(Reading database ... 182725 files and directories currently installed.)
Unpacking libboost-system1.46.1 (from .../libboost-system1.46.1_1.46.1-7ubuntu3_amd64.deb) ...
Selecting previously unselected package libboost-filesystem1.46.1.
Unpacking libboost-filesystem1.46.1 (from .../libboost-filesystem1.46.1_1.46.1-7ubuntu3_amd64.deb) ...
Selecting previously unselected package libboost-thread1.46.1.
Unpacking libboost-thread1.46.1 (from .../libboost-thread1.46.1_1.46.1-7ubuntu3_amd64.deb) ...
Selecting previously unselected package libtorrent-rasterbar6.
Unpacking libtorrent-rasterbar6 (from .../libtorrent-rasterbar6_0.15.10-1_amd64.deb) ...
Selecting previously unselected package qbittorrent.
Unpacking qbittorrent (from .../qbittorrent_2.9.7-1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up nvidia-g210m-acpi-source (0.1.0-1~ppa0~karmic) ...
Removing old nvidia-g210m-acpi-0.1.0 DKMS files...

------------------------------
Deleting module version: 0.1.0
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-g210m-acpi-0.1.0 DKMS files...

Loading tarball for nvidia-g210m-acpi-0.1.0

DKMS: ldtarball completed.

Creating symlink /var/lib/dkms/nvidia-g210m-acpi/0.1.0/source ->
                 /usr/src/nvidia-g210m-acpi-0.1.0

DKMS: add completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-32-generic....(bad exit status: 2)
ERROR (dkms apport): binary package for nvidia-g210m-acpi: 0.1.0 not found
Error! Bad return status for module build on kernel: 3.2.0-32-generic (x86_64)
Consult /var/lib/dkms/nvidia-g210m-acpi/0.1.0/build/make.log for more information.
dpkg: error processing nvidia-g210m-acpi-source (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
Setting up libboost-system1.46.1 (1.46.1-7ubuntu3) ...
Setting up libboost-filesystem1.46.1 (1.46.1-7ubuntu3) ...
Setting up libboost-thread1.46.1 (1.46.1-7ubuntu3) ...
Setting up libtorrent-rasterbar6 (0.15.10-1) ...
Setting up qbittorrent (2.9.7-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nvidia-g210m-acpi-source
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up nvidia-g210m-acpi-source (0.1.0-1~ppa0~karmic) ...
Removing old nvidia-g210m-acpi-0.1.0 DKMS files...

------------------------------
Deleting module version: 0.1.0
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-g210m-acpi-0.1.0 DKMS files...

Loading tarball for nvidia-g210m-acpi-0.1.0

DKMS: ldtarball completed.

Creating symlink /var/lib/dkms/nvidia-g210m-acpi/0.1.0/source ->
                 /usr/src/nvidia-g210m-acpi-0.1.0

DKMS: add completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-32-generic....(bad exit status: 2)
ERROR (dkms apport): binary package for nvidia-g210m-acpi: 0.1.0 not found
Error! Bad return status for module build on kernel: 3.2.0-32-generic (x86_64)
Consult /var/lib/dkms/nvidia-g210m-acpi/0.1.0/build/make.log for more information.
dpkg: error processing nvidia-g210m-acpi-source (--configure):
 subprocess installed post-installation script returned error exit status 10

```
I've tried searching the forums and launchpad forums but this seems pretty consistent with the geforce g210m file. I'm brand new to Ubuntu so be gentle if this is a simple fix ;) Thanks!

---

