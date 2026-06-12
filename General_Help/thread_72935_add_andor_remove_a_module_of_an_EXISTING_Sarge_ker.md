---
title: "add and/or remove a module of an EXISTING Sarge kernel"
date: 2005-10-07
forum: General Help
---

### Post by Virgilinux on 2005-10-07
Can I use Ubuntu 5.04 liveCD to add and/or remove a module of an EXISTING (installed) Kernel?

If yes, how?

For background, I am installing Sarge (debian stable) on an HP laptop. The debian installer installs the "wrong" sound module during the first stage of the installation. This blocks the installed kernel from booting to complete the second stage of the installation.

Basically, it is a known bug, which has not been corrected.
See: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=298623](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=298623)

Presumably, the problem is caused by a sound module: i810_audio.ko . The workaround is to install the ALSA (snd_intel8x0) module ((which would among other things 'blacklist' the OSS modules).

I have already tried a number of things, going through "expert" installation, trying to use the debian installer as a rescue CD, getting into a console, etc. But nothing has worked. So, perhaps Ubuntu liveCD may allow me to add and/or substract the appropiate kernel modules.

Thanks in advance.

Virgil

---

### Post by Virgilinux on 2005-10-09
If you want further info on this, view:
[http://www.knoppix.net/forum/viewtopic.php?t=21410](http://www.knoppix.net/forum/viewtopic.php?t=21410)

---

