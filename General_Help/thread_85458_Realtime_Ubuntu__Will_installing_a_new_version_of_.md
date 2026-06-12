---
title: "Realtime Ubuntu:  Will installing a new version of PAM break anything?"
date: 2005-11-02
forum: General Help
---

### Post by alfzer0 on 2005-11-02
Does anyone know if compiling and installing the newest version of libpam and libpam-modules (v.81) will break anything in a default breezy install?  I read that it is very distribution dependant, and I'd like some advice if anyone has some to offer before I possibly destroy my install.

Since the default breezy kernel has the rlimits patches merged (all 2.6.12-rc4 and later kernels), I'd like to try to get some userspace programs running in realtime (such as the jack audio server) without root access.  However, the version of PAM (Pluggable Authentication Modules) shipped with breezy (v.76) doesn't have the options to manage the realtime privilege settings that are now available from the rlimits kernel patches.  Versions of [PAM]("http://www.kernel.org/pub/linux/libs/pam/")>0.80 are supposed to have the ability to do this.  This alone should allow decent "realtime" operations from userspace programs in ubuntu.  For a much better realtime implementation, a recompiled kernel with the kernel premption turned on (CONFIG_PREEMPT=y) is needed.

If I can get this accomplished I plan to write a howto for all the people that have been trying to get jack running without much success.  I do currently have a way to run jackd with realtime privileges with [set_rtlimits]("http://tapas.affenbande.org/?page_id=22").  set_rtlimits was designed for distributions that do not use PAM and still have access to the functionality of the rlimits kernel patches.  However I've found that all userspace programs that connect to jack must have their realtime privileges set with it (not just the jack daemon), and its incredibly annoying to do this for all these apps.

Thanks in advance for any info,
-Jeff

P.S.  I've also got oss2jack running, which allows multiple applications that support sound output through oss to use jack as their output, which in turn, jack uses alsa for its output.

---

### Post by norman_h on 2006-04-29
[http://demudi.agnula.org/wiki/Low-latencyKernelBuildingHowto](http://demudi.agnula.org/wiki/Low-latencyKernelBuildingHowto)
> Quick and dirty steps

To enable normal user to start application in realtime mode using the rlimits you need to download this debian package (from ubuntustudio):

    * [http://www.ubuntustudio.com/uploads/breezy/libpam-modules_0.76-22ubuntu3studio1_i386.deb](http://www.ubuntustudio.com/uploads/breezy/libpam-modules_0.76-22ubuntu3studio1_i386.deb)

and install it with with dpkg, as usual:

 # dpkg -i libpam-modules_0.76-22ubuntu3studio1_i386.deb

Reboot. No further configuration is needed: for all kernels we have installed or will install, we already have the ability to start JACK (or other applications) in realtime mode (provided that the user is in the audio group).
Explanation and backgrounds

This approach requires a version of PAM with rlimits support. The new 0.80 version has the support but unfortunately there isn't a debian package for that version jet. Previous versions of PAM must be patched to become rlimits-aware. Current DeMuDi and Debian Etch (the two are synced) have the 0.79 version of PAM. So you have two ways: or to patch your current version of PAM to add the rlimits support or to install a pre-patched debian package. Both methods are fine (clearly the latter is simpler) and are illustrated at the ubuntustudio site:

    * [http://ubuntustudio.com/wiki/index.php/Breezy:Rlimits-Aware_PAM](http://ubuntustudio.com/wiki/index.php/Breezy:Rlimits-Aware_PAM) 

The pre-patched package (that for Breezy) provided by ubuntustudio it's the 0.76 version, a bit older that the version currently in DeMuDi and Debian Etch. Nonetheless, the package it is reported to work flawlessly on Debian Etch and DeMuDi. Just be careful to don't upgrade the package libpam-modules when you upgrade the system, otherwise the newer unpatched version (0.79) will be installed. A quick way to be sure that the package will not be upgraded is to use aptitude and put libpam-modules in a hold state (just select the package and press '=').

---

