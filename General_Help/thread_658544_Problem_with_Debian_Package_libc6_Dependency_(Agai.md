---
title: "Problem with Debian Package: libc6 Dependency (Again)"
date: 2008-01-04
forum: General Help
---

### Post by GenuineXP on 2008-01-04
I'm trying to install the brickos package, an alternative OS for the Lego Mindstorms RCX hardware. Unfortunately, the version in the repositories has a known issue and the kernel renders the RCX unusable. I read in several Debian bug listings that the problem was solved in some new versions. The latest in the Gutsy repos is 2, while the newest I found in some Debian pools is 5, uploaded in December.

I've found a version 4 package for Ubuntu, but there's no amd64 package (I'm running Gutsy amd64). I thought that Debian packages were supposed to install without modification under Ubuntu, but I get the infamous libc6 dependency error despite the fact that that package is indeed installed. This is a frustrating problem I've run into before. In the past, I just gave up. Is there something I can do? Some kind of conversion or something?

Thanks!

---

### Post by dcstar on 2008-01-05
> **GenuineXP said:**
> 
.........
I've found a version 4 package for Ubuntu, but there's no amd64 package (I'm running Gutsy amd64). **I thought that Debian packages were supposed to install without modification under Ubuntu**, but I get the infamous libc6 dependency error despite the fact that that package is indeed installed.
.......!

No, Ubuntu is based on Debian, but Ubuntu <> Debian.

As well, all later versions of things have dependencies, this package obviously has been compiled with a dependency that is not available on your current Ubuntu version, that is why it will not install and this has nothing to do with Ubuntu, the same issue will be there on older Debian versions.

---

