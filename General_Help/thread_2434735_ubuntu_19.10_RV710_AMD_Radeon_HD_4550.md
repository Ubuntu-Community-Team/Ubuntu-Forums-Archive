---
title: "ubuntu 19.10 RV710 AMD Radeon HD 4550"
date: 2020-01-09
forum: General Help
---

### Post by ekie952 on 2020-01-09
I am trying to install drivers for a AMD Radeon HD 4550 video card. Running Ubuntu 19.10.    Installed AMD Catalyst™ 13.1 Proprietary Linux x86 Display Driver and get this error message. "Check if system has the tools required for installation.fglrx installation requires that the system have kernel headers.  /lib/modules/5.3.0-26-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended." Thanks

---

### Post by deadflowr on 2020-01-10
The fglrx/catalyst drivers, which are no longer supported for any AMD graphics card on linux, haven't been supported for your particular card in nearly 10 years.
(Give or take a year or two)
You can only use the drivers already included with the system.

---

### Post by QIII on 2020-01-10
Just an explanatory note:

The kernel now includes the modules for the open source Radeon driver and the AMDGPU driver.  The latter does not support your card.  The former does.

When you install Ubuntu, the appropriate driver module is loaded and there is nothing further you need to do.

---

### Post by mastablasta on 2020-01-10
also not sure how up to date this is but they list the available feature of opensource Radeon driver: [https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)

---

