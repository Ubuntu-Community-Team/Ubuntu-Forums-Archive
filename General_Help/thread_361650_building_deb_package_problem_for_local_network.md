---
title: "building deb package problem for local network"
date: 2007-02-14
forum: General Help
---

### Post by ximok on 2007-02-14
I am developing a custom package for my internal network that has major changes with every release of ubuntu (breezy,dapper,edgy,feisty).  If I need make the package update only for those releases would it be appropriate to assign the dependency of the  package to the version number of  ubuntu-minimal?

Example (Logical, not syntactical)

custom-package-1.0 depends on ubuntu-minimal == 0.80 for breezy
custom-package-2.0 depends on ubuntu-minimal == 0.119 for dapper
custom-package-3.0 depends on ubuntu-minimal == 1.30 for edgy
custom-package-4.0 depends on ubuntu-minimal == 1.34 for feisty

Would this be the correct way to build this package for these releases, or should I be referencing something else?

I can't have my custom package version 2.0 being installed on breezy for example.  Breezy should be cut off at custom package-1.0

Any help would be appreciated.

---

### Post by lamego on 2007-02-14
You pretty much answered yourself, your packages should depend on whatever ubuntu-minimal version they depend on.

---

### Post by loell on 2007-02-14
if it can't pose a problem for that component ie(api changes and such)
then yes :)

---

### Post by ximok on 2007-02-14
So, with the logic I just used, I should be able to post all of the different versions of my code for each release, and only the proper version will install with its release, without apt trying to upgrade ubuntu-minimal?

---

### Post by lamego on 2007-02-14
> So, with the logic I just used, I should be able to post all of the different versions of my code for each release, and only the proper version will install with its release, without apt trying to upgrade ubuntu-minimal?
A package dependency does not invoke upgrades, it will just stop the package from beeing installed/configured until the dependency gets resolved.
So yes, those packages can't not be properly configured because their dependency will not be met on the wrong system.

---

### Post by ximok on 2007-02-15
Thank you for your help.  I just realized I have a two part problem.

I need to reconfigure my custom repository so that it advertises the different versions.

In a nutshell, I need to rebuild with a breezy, dapper, edgy, and feisty repository just like the ubuntu archives are... go figure (I really should have predicted this).

But, that's the easy part now.

Thanks for all the help.

---

