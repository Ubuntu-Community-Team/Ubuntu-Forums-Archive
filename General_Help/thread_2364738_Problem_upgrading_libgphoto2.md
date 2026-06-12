---
title: "Problem upgrading libgphoto2"
date: 2017-06-27
forum: General Help
---

### Post by eichan on 2017-06-27
Hi all,

The regular updates Ubuntu does flawlessly 99% of the time are giving me a bit of a headache right now. The problem is that it seems to be impossible to upgrade libgphoto2, and my package manager tells me I have a broken package. I'd be veeery glad if someone could give me a hand!

First, a bit of background: I'm using a laptop running Xubuntu 16.04. I've been using gphoto2 without any problems for a long time (mostly using it with Kstars and through its INDI driver). But now, kaboom. Happy to provide any extra information, but not sure what is relevant.

Now, here is the output of the failing commands:

sudo apt upgrade:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libgphoto2-port12 : Breaks: libgphoto2-port12:i386 (!= 2.5.14+201706051856~ubuntu16.04.1) but 2.5.14+201706200750~ubuntu16.04.1 is installed
 libgphoto2-port12:i386 : Breaks: libgphoto2-port12 (!= 2.5.14+201706200750~ubuntu16.04.1) but 2.5.14+201706051856~ubuntu16.04.1 is installed
E: Unmet dependencies. Try using -f.

```

sudo apt upgrade -f:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libgphoto2-port12 : Breaks: libgphoto2-port12:i386 (!= 2.5.14+201706051856~ubuntu16.04.1) but 2.5.14+201706200750~ubuntu16.04.1 is to be installed
 libgphoto2-port12:i386 : Breaks: libgphoto2-port12 (!= 2.5.14+201706200750~ubuntu16.04.1) but 2.5.14+201706051856~ubuntu16.04.1 is to be installed
E: Broken packages

```

sudo dpkg --configure -a
```

dpkg: error processing package libgphoto2-port12:i386 (--configure):
 package libgphoto2-port12:i386 2.5.14+201706200750~ubuntu16.04.1 cannot be configured because libgphoto2-port12:amd64 is at a different version (2.5.14+201706051856~ubuntu16.04.1)
Setting up less (481-2.1ubuntu0.2) ...
Setting up fliusb-dkms (1.3+r3137~201706221923~ubuntu16.04.1) ...
Loading new fliusb-1.3+r3137~201706221923~ubuntu16.04.1 DKMS files...
Building only for 4.4.0-81-generic
Building initial module for 4.4.0-81-generic
Done.


fliusb:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-81-generic/updates/dkms/


depmod........


DKMS: install completed.
Setting up libqsi7 (7.2.0+r3137~201706221925~ubuntu16.04.1) ...
dpkg: dependency problems prevent configuration of libgphoto2-6:i386:
 libgphoto2-6:i386 depends on libgphoto2-port12 (>= 2.5.10); however:
  Package libgphoto2-port12:i386 is not configured yet.


dpkg: error processing package libgphoto2-6:i386 (--configure):
 dependency problems - leaving unconfigured
Setting up libfishcamp (1.0+r3137~201706221922~ubuntu16.04.1) ...
Setting up libindi-data (1.4.1+r3137~201706221921~ubuntu16.04.1) ...
Setting up libapogee3 (3.0.3234+r3137~201706221926~ubuntu16.04.1) ...
Setting up libqhy (0.1.8+r3137~201706221920~ubuntu16.04.1) ...
Setting up openvpn (2.3.10-1ubuntu2.1) ...
 * Restarting virtual private network daemon(s)...                                         *   No VPN is running.
Setting up libsbigudrv2 (2.1.1+r3137~201706221913~ubuntu16.04.1) ...
Setting up libfli1 (1.8.ubuntu5+r3137~201706221913~ubuntu16.04.1) ...
Setting up indi-bin (1.4.1+r3137~201706221921~ubuntu16.04.1) ...
Setting up libindi1:amd64 (1.4.1+r3137~201706221921~ubuntu16.04.1) ...
The user `tan' is already a member of `dialout'.
Setting up indi-qhy (1.6+r3137~201706221914~ubuntu16.04.1) ...
Setting up indi-gpsd (0.3+r3137~201706221912~ubuntu16.04.1) ...
Setting up indi-mi (1.1+r3137~201706221909~ubuntu16.04.1) ...
Setting up indi-asi (0.5+r3137~201706221916~ubuntu16.04.1) ...
Setting up indi-qsi (0.5.0+r3137~201706221911~ubuntu16.04.1) ...
Setting up indi-gphoto (1.4+r3137~201706221919~ubuntu16.04.1) ...
Setting up indi-fli (1.0.0ubuntu3+r3137~201706221920~ubuntu16.04.1) ...
Setting up indi-sbig (1.7+r3137~201706221915~ubuntu16.04.1) ...
Setting up indi-apogee (1.5+r3137~201706221910~ubuntu16.04.1) ...
Setting up indi-ffmv (0.1+r3137~201706221908~ubuntu16.04.1) ...
Setting up indi-sx (1.4+r3137~201706221907~ubuntu16.04.1) ...
Setting up indi-fishcamp (1.0+r3137~201706221904~ubuntu16.04.1) ...
Setting up indi-dsi (0.1+r3137~201706221911~ubuntu16.04.1) ...
Setting up libindi-dev (1.4.1+r3137~201706221921~ubuntu16.04.1) ...
Setting up indi-duino (0.2+r3137~201706221918~ubuntu16.04.1) ...
Setting up indi-maxdomeii (1.1+r3137~201706221926~ubuntu16.04.1) ...
Setting up indi-aagcloudwatcher (1.3+r3137~201706221905~ubuntu16.04.1) ...
Setting up indi-full (1.4~201706221916~ubuntu16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Errors were encountered while processing:
 libgphoto2-port12:i386
 libgphoto2-6:i386

```

---

### Post by steeldriver on 2017-06-27
Those don't look like standard Ubuntu package versions - do you have other repositories enabled?

Also not sure why you would have both i386 and (presumably) x86_64 packages installed - unless you need them for multiarch development? The problem seems to be that your system seems to have got into a state in which the versions of the 32-bit and 64-bit software are conflicting. It looks remarkably similar to this askubuntu question (which seems to have been closed as off-topic because the OP was using KDE Neon):

[Unmet dependencies - libgphoto2-port12]("https://askubuntu.com/questions/926787/unmet-dependencies-libgphoto2-port12")

The fix there seems to have been

```

sudo apt-get dist-upgrade -f

```

---

### Post by eichan on 2017-06-28
These come indeed from an external repository. The fix you found did work for me. So thank you very much, problem solved!

---

