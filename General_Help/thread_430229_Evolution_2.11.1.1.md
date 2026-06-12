---
title: "Evolution 2.11.1.1"
date: 2007-05-01
forum: General Help
---

### Post by rbmorse on 2007-05-01
Has been released. I downloaded the tarball but the package would not build on Feisty with the 386 generic kernel...configures OK, but make reports numerous syntax errors and quits.

I have Gutsy (7.10-pre) running in a VMware Workstation VM and noticed that Evolution 2.11.1.1 is in the Gutsy repositories, and installs and works fine there, But, it  will not install on Feisty, citing about 30 unfulfilled dependencies.  The files are available from the Ubunty files web page, but I am concerned about regression problems resulting from installing a subset of Gutsy onto a live, production Fesity installation. 

What should I do to request that Evolution 2.11.1.1. be formally backported to Feisty?  The current version in Feisty (2.,10.X) is sufficient buggy and unstable to warrant extraordinary handling, but I don't know who to ask or the correct venue to do so.

---

### Post by dcstar on 2007-05-01
> **rbmorse said:**
> Has been released. I downloaded the tarball but the package would not build on Feisty with the 386 generic kernel...configures OK, but make reports numerous syntax errors and quits.

I have Gutsy (7.10-pre) running in a VMware Workstation VM and noticed that Evolution 2.11.1.1 is in the Gutsy repositories, and installs and works fine there, But, it  will not install on Feisty, citing about 30 unfulfilled dependencies.  The files are available from the Ubunty files web page, but I am concerned about regression problems resulting from installing a subset of Gutsy onto a live, production Fesity installation. 

What should I do to request that Evolution 2.11.1.1. be formally backported to Feisty?  The current version in Feisty (2.,10.X) is sufficient buggy and unstable to warrant extraordinary handling, but I don't know who to ask or the correct venue to do so.

I have never seen any Evolution Backports for any Ubuntu release, usually because the newer versions have so many dependencies that do not exist in the previous Ubuntu version that it is extremely difficult to build it without breaking many other things.

---

