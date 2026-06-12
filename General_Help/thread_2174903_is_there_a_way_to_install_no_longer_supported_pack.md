---
title: "is there a way to install no longer supported packages"
date: 2013-09-16
forum: General Help
---

### Post by fraterchaos on 2013-09-16
I was wondering if there is some way to install a package that is no longer supported?

I'm asking because I would really like to have the full set of Compiz-plugins-extra that is no longer supported (in particualr the reflection and distortion plugins) 

I've searched, and have even downloaded the tarballs for it (version 0.8) but when I try to follow the command line instructions to configure and make the package, make gives me an error... the instructions say to type make, but it always says there is no target and no makefiles (I'm not really too well versed oin this compiling from sources stuff)

If someone knows how to enable depreciated sources for the package manager, or can explain in detail how to do the configure/make on this package, I would be very happy... that is consiering its even possible to install these older plugins?

---

### Post by Dennis N on 2013-09-17
Start here:

[http://old-releases.ubuntu.com/ubuntu/pool/universe/c/](http://old-releases.ubuntu.com/ubuntu/pool/universe/c/)

If you want version 0.8, they seem to be under "compiz-fusion-plugins-extra" and "compiz-fusion-plugins-unsupported".

You can attempt installation with gdebi package installer.

---

### Post by CatKiller on 2013-09-18
In general, you can just grab packages from packages.ubuntu.com and sort out any dependencies by hand. In the particular case of compiz-plugins-extra, the reason they aren't included is because they don't work. Compiz has gone through a massive overhaul, meaning that the old package won't work with new Compiz. New everything else won't work with old Compiz. You're just asking for trouble with the attempt.

The old plugins are being re-implemented as developer time allows, and I know that Reflection has made it back in because I use it myself. I believe Deformation is in there too, but I don't know for sure. Some branches are newer than other branches; I was running compiz-experimental on 12.10 for access to these plugins, but they're back in the main branch by 13.04. Still no burn, though :(

---

