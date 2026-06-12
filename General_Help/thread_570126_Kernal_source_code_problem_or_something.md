---
title: "Kernal source code problem or something"
date: 2007-10-07
forum: General Help
---

### Post by Christ_Guard on 2007-10-07
Here is my problem:

```
christian@christian-laptop:~/Desktop/iwlwifi-1.0.0-1$ make
Makefile:20: 
Makefile:21: WARNING: $SHELL not set to bash.
Makefile:22: If you experience build errors, try
Makefile:23: 'make SHELL=/bin/bash'.
Makefile:24: 
Kernel Makefile not found at '/lib/modules/2.6.20-16-generic/source'
make: *** [compatible/kversion] Error 1
christian@christian-laptop:~/Desktop/iwlwifi-1.0.0-1$ make SHELL=/bin/bash
Kernel Makefile not found at '/lib/modules/2.6.20-16-generic/source'
make: *** [compatible/kversion] Error 1
christian@christian-laptop:~/Desktop/iwlwifi-1.0.0-1$ 

```


I think this is a problem with kernal or something, IDK. Any ideas on what to do? Thanks!

-Christian

---

### Post by jake16424 on 2007-10-07
> **Christ_Guard said:**
> Here is my problem:

```
christian@christian-laptop:~/Desktop/iwlwifi-1.0.0-1$ make
Makefile:20: 
Makefile:21: WARNING: $SHELL not set to bash.
Makefile:22: If you experience build errors, try
Makefile:23: 'make SHELL=/bin/bash'.
Makefile:24: 
Kernel Makefile not found at '/lib/modules/2.6.20-16-generic/source'
make: *** [compatible/kversion] Error 1
christian@christian-laptop:~/Desktop/iwlwifi-1.0.0-1$ make SHELL=/bin/bash
Kernel Makefile not found at '/lib/modules/2.6.20-16-generic/source'
make: *** [compatible/kversion] Error 1
christian@christian-laptop:~/Desktop/iwlwifi-1.0.0-1$ 

```


I think this is a problem with kernal or something, IDK. Any ideas on what to do? Thanks!

-Christian


far from an expert, but looks as though it was looking for a file, that wasn't present, but im prolly wrong, cause im new to linux, had ubuntu 7.4 or 7.3,, wichever, but,, im just now getting back into it.

---

### Post by Elshadii on 2007-10-14
Are you trying to build wifi drivers?  If so you it doesn't look like you've installed the build tools.  Try doing:

sudo apt-get install build-essential linux-source

from a command line or search the package "build-essential" and "linux-source" in synaptic.  That should fix you up.

---

### Post by azamo on 2007-11-03
I get 
```
/home/azamo/ieee80211-1.2.18/Makefile:17: 
/home/azamo/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/azamo/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/azamo/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/azamo/ieee80211-1.2.18/Makefile:21: 

```
while trying to install ieee802.11 1.2.18.

And when i typed 
```
$ sudo apt-get install build-essential linux-source

```
I got
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Additionally I get an error while trying to install ipw2200-1.2.0:
```
make[2]: *** [/home/azamo/ipw2200-1.2.0/ipw2200.o] Error 1
make[1]: *** [_module_/home/azamo/ipw2200-1.2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2
```
In the INSTALL file for ipw2200 it is desribed as follows:
```
The following error appears when compiling the driver.
make[1]: Entering directory `/usr/src/kernels/2.6.11-1.1369_FC4-i686'
make[1]: *** No rule to make target `modules'. Stop.
make[1]: Leaving directory `/usr/src/kernels/2.6.11-1.1369_FC4-i686'
make: *** [modules] Error 2

CAUSE: make sure that the kernel source is installed on your machine
```

I am looking for help for a long time but I only find advises to install linux-headers and build-essential, which both seem to be ok in my system.

Does anyone have any idea what may be wrong?

---

### Post by Elshadii on 2007-11-04
So you have the build-essential and kernel-source packages installed.  I see that in your text it looks like you are trying to compile something for a fedora core kernel:

/usr/src/kernels/2.6.11-1.1369_FC4-i686

I looked and the 80211-source package is in the universe repo. for gutsy.  That package will also install the doc that will provide directions on how to compile these modules.  HTH

---

### Post by d_in_Conduct on 2007-11-04
I wasn't able to compile much of anything in Gutsy.  I think the sources are laid out differently, or not everything is supplied.

I've gone back to Feisty.

---

