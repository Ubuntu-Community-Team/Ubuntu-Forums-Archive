---
title: "Ati and DRI"
date: 2005-03-30
forum: General Help
---

### Post by bushka on 2005-03-30
Hello A:)

I'm trying to get 3d support from my Ati Rage Pro Mobility Mach64, however whatever I do I get the error message below.

> DIRECT RENDERING OPEN SOURCE PROJECT  -  DRIVER INSTALLATION SCRIPT

[ [http://dri.sourceforge.net](http://dri.sourceforge.net) ]

==========================================================================

The script will now compile the DRM kernel modules for your machine.

Press ENTER to continue or CTRL-C to exit.


Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong. 

The dri.log states that...

> Makefile:163: *** Cannot find a kernel config file.  Stop. 

It would seem simple enough, get the source and run make menuconfig and save just to generate the .config file it can not find, however I can not get the source for my kernel exactely, 2.6.10-5 but I can get the source through apt-get for linux-source-2.6.10, I'm guessing this is what I need so I have downloaded and installed it, then I run make menuconfig, save and exit. I also create a symbolic link from /usr/src/linux to /usr/src/linux-source-2.6.10. But still when I run the DRI installer I get the error messages posted above?

What am I doing wrong?

---

### Post by soul_rebel on 2005-03-31
try with kernel headers instead of source.

---

