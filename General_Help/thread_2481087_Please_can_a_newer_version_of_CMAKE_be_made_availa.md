---
title: "Please can a newer version of CMAKE be made available?"
date: 2022-11-18
forum: General Help
---

### Post by andrew-q2 on 2022-11-18
I use Darktable under Ubuntu 20.04, building Darktable development version myself.  This has worked fine until recently when one of the components, Rawspeed, will no longer build.  This is because it now requires Cmake version 3.18, whereas Ubuntu only has 3.16.3.
I have raised this with a Rawspeed developer however they say it's not down to the Rawspeed team, and they imply it's a matter for Ubuntu Cmake folk.  The details can be seen here -
[https://github.com/darktable-org/rawspeed/issues/400](https://github.com/darktable-org/rawspeed/issues/400)

Is it possible please to put a newer version of Cmake into the standard Ubuntu 20.04 update process?

Will this post reach an appropriate Cmake person, or do I need to direct this elsewhere?

Thanks

---

### Post by TheFu on 2022-11-18
> **andrew-q2 said:**
>  
Is it possible please to put a newer version of Cmake into the standard Ubuntu 20.04 update process?

Unlikely, because introducing a new version that alters existing functionality is anti-LTS.  You can probably find a PPA with the newer version of cmake and use that instead.  But if you are going to the effort to make Darktable yourself, I'd be surprised if compiling a newer cmake were too much trouble.

There are people dependent on the older version of cmake, almost certainly. Screwing them isn't something an LTS should consider.

---

### Post by tea for one on 2022-11-18
A newer version is available in Ubuntu 22.04

Package cmake
jammy (22.04LTS) (devel): cross-platform, open-source make system
3.22.1-1ubuntu1: amd64 arm64 armhf i386 ppc64el s390x

---

### Post by deadflowr on 2022-11-18
> Will this post reach an appropriate Cmake person, or do I need to direct this elsewhere?
No.
Developers don't read these forums.

For updating packages you'd probably want to follow the standard SRU upgrade procedure or the backportting procedure.
See: [https://wiki.ubuntu.com/StableReleaseUpdates]("https://wiki.ubuntu.com/StableReleaseUpdates")
[https://wiki.ubuntu.com/UbuntuBackports]("https://wiki.ubuntu.com/UbuntuBackports")
More likely it would have to be a backport.
But those are the standard ways of making a request like this.

And another option is to create a PPA or have/convince someone who can create a PPA for the package.
(If a PPA does not already exist with the updated version)

---

### Post by dragonfly41 on 2023-05-06
This might be too late for OP. But I was searching similar question and found that I can update cmake from 3.16 through PIP ...

[https://stackoverflow.com/questions/49859457/how-to-reinstall-the-latest-cmake-version](https://stackoverflow.com/questions/49859457/how-to-reinstall-the-latest-cmake-version)

[FONT=monospace][COLOR=#000000]Installing collected packages: cmake[/COLOR]
Successfully installed cmake-3.26.3
[/FONT]
[FONT=monospace][COLOR=#000000]cmake --version[/COLOR]
cmake version 3.26.3

[/FONT]My interest is that I wish to update Albert build on Ubuntu 20.04.

But ...I find later that cmake 3.26.3 requires Qt6 to be installed.

---

