---
title: "How to update software packages?"
date: 2008-02-10
forum: General Help
---

### Post by HuBaghdadi on 2008-02-10
Hi.
In general, how to update installed software packages installed on Ubuntu if a newer version is available?
For example, suppose I have Firestarter 4 installed a newer version is live, should I uninstall Firestarter 4 from my system and download/install the newer version?
Or this could be done by updating Ubuntu itself?
(well, assuming the application doesn't offer "Update" option)
Thanks.

---

### Post by kesman on 2008-02-10
You have about three choices. You can wait for a newer version of the software to appear in the ubuntu repositories, so it'll update by itself. Then you could check their webpage for a newer version in ubuntu install file ".deb", or then compile the newest version yourself. That's a bit tricky but provides the very latest version of course.

---

### Post by PeterJS on 2008-02-10
Generally staying with in the package management system (apt, synaptic, update manager, etc), is preferred. The reason something wouldn't be updated is because:
1) Deb packages for that version don't exist (yet)
2) That version won't be included in the current dist because of versioning, freezing, and testing standards

For the second case, you could try checking third parties like get deb, they're pretty up to date, but not nearly as complete as the general mirrors. Or you could try grabbing the debs from Debian testing, or the Ubuntu current+1 release, the problem with this method is that you could end up updating a whole bunch of dependencies by hand to accommodate using debs from a future source.

For the first case you could wait it out a few days to give the maintainer time to build them. Or in cases where the package is never going to be built, you could uninstall the existing package, build your own and install it with checkinstall. Using checkinstall will make it easist to remove to go back to using an official version, but probably won't have all the right dependency data, both on the needing and providing end (it's reasonable to assume it it builds that you've got all the needed dependencies, but that's not guaranteed )

---

