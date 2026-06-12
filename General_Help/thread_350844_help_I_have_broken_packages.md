---
title: "help I have broken packages"
date: 2007-02-01
forum: General Help
---

### Post by michie86 on 2007-02-01
I tried instaling the package libc 2.3.6.ds1-10 and I got errors. it says that i need tzdata. So i ended up having 2 broken packages.. here they are

sudo apt-get install -f

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6.ds1-10 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

so I downloaded tzdata and tried to install it but this is what happens

dpkg -i tzdata_2007a-1_all.deb
(Reading database ... 69881 files and directories currently installed.)
Unpacking tzdata (from tzdata_2007a-1_all.deb) ...
dpkg: error processing tzdata_2007a-1_all.deb (--install):
 trying to overwrite `/usr/share/zoneinfo/NZ', which is also in package locales
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 tzdata_2007a-1_all.deb

please help me! I really need to get these working


by the way, I tried installing libc because of this(for gnokii installation)

Selecting previously deselected package gnokii.
(Reading database ... 69877 files and directories currently installed.)
Unpacking gnokii (from gnokii_0.6.14+cvs20070111-1_i386.deb) ...
Adding group `gnokii' (113)...
Done.
dpkg: dependency problems prevent configuration of gnokii:
 gnokii depends on libbluetooth2 (>= 3.0); however:
  Package libbluetooth2 is not installed.
 gnokii depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 gnokii depends on libgnokii3; however:
  Package libgnokii3 is not installed.
 gnokii depends on libusb-0.1-4 (>= 2:0.1.12); however:
  Version of libusb-0.1-4 on system is 2:0.1.10a-22ubuntu1.
dpkg: error processing gnokii (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnokii

I'm using ubuntu 6.06
help please.. thanks

ps. is there "system restore in ubuntu?"

---

### Post by 454redhawk on 2007-02-01
did you try opening synaptic and use the fix broken package option?

Its in the synaptic menus.

---

### Post by michie86 on 2007-02-01
yes I already tried that.. this is what I get

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

what should I do? thanks

---

### Post by marselluswallace on 2007-02-02
well i have a similar problem...
i have this update available which is locales version 2.3.18.1 but everytime i try to do the update as suggested by the system, i get the following message:

E: /var/cache/apt/archives/locales_2.3.18.1_all.deb: trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package tzdata

I never had a locales problem... can anyone help me out here? thank you!

---

### Post by Zimmer on 2007-02-02
[http://ubuntuforums.org/showthread.php?t=243274&highlight=zoneinfo](http://ubuntuforums.org/showthread.php?t=243274&highlight=zoneinfo)

[http://ubuntuforums.org/showthread.php?t=350994&highlight=zoneinfo](http://ubuntuforums.org/showthread.php?t=350994&highlight=zoneinfo)

You may be part of a wider problem..

[http://ubuntuforums.org/showthread.php?t=243944&highlight=zoneinfo](http://ubuntuforums.org/showthread.php?t=243944&highlight=zoneinfo)

---

