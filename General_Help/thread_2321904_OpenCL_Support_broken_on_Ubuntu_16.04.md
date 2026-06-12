---
title: "OpenCL Support broken on Ubuntu 16.04?"
date: 2016-04-25
forum: General Help
---

### Post by victorhooi on 2016-04-25
Hi,

I recently install Ubuntu 16.04 on a desktop with an AMD R9 290X graphics card.

My objective is to run oclHashcat.

The recommendation from oclHashcat is to use the proprietary Catalyst/fglrx driver. However, I see in the Ubuntu 16.04 release notes that the fglrx driver is deprecated, and we're recommended to use the open-source radeon driver.

However, when I try to run the oclHashcat binary under Ubuntu, I get:

```

victorhooi@Cruncher:~/Downloads/oclHashcat-2.01$ ./oclHashcat64.bin 
./oclHashcat64.bin: error while loading shared libraries: libOpenCL.so.1: cannot open shared object file: No such file or directory

```

Does the radeon driver not yet have OpenCL support? If so, any idea on when it's coming?

I did try to install the fglrx driver following the instructions at [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) - however, I'm not sure if it's some changes in 16.04, but the script doesn't run:

```

victorhooi@Cruncher:~/Downloads/fglrx-15.302$ ./blah.run --buildpkg Ubuntu/xenial
Created directory fglrx-install.ZaUsp7
Verifying archive integrity... All good.
Uncompressing AMD Proprietary Driver-15.302...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD  Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/xenial
Resolving build dependencies...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package Unmet
E: Unable to locate package build
E: Unable to locate package dependencies
Unable to resolve  Unmet build dependencies.  Please manually install and try again.
^CSignal caught, cleaning up
victorhooi@Cruncher:~/Downloads/fglrx-15.302$ ./blah.run --buildpkg Ubuntu/trusty
Created directory fglrx-install.FlAG7H
Verifying archive integrity... All good.
Uncompressing AMD Proprietary Driver-15.302...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD  Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/trusty
Resolving build dependencies...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package Unmet
E: Unable to locate package build
E: Unable to locate package dependencies
Unable to resolve  Unmet build dependencies.  Please manually install and try again.
^CSignal caught, cleaning up

```

(I had to rename the script to get it to run, not sure if it's a path length thing or something).

Has anybody managed to either get OpenCL working on Ubuntu 16.04, or the fglrx/Catalyst drivers working?

Regards,
Victor

---

### Post by grahammechanical on 2016-04-25
"Depreciated" in this setting means there are not any AMD proprietary video drivers available in the 16.04. Ubuntu 16.04 uses a newer version of the X Server and AMD proprietary video drivers are not compatible with it. And AMD has decided not to support its proprietary video drivers on this version of the X Server. So, the Ubuntu developers have removed the ability to install AMD proprietary video drivers from 16.04.

Things might get better by the summer due to the work being done by AMD on it amdgpu driver.

Regards.

---

### Post by martin30002 on 2016-11-14
> 
[COLOR=#000000][FONT=&quot]E: Unable to locate package Unmet
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]E: Unable to locate package build
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]E: Unable to locate package dependencies [/FONT][/COLOR]Unable to resolve  Unmet build dependencies. [COLOR=#222222][FONT=Verdana]

Hu? Did you see this? [/FONT][/COLOR]Unable to resolve  "Unmet build dependencies"! There is something wrong with the installer.

---

