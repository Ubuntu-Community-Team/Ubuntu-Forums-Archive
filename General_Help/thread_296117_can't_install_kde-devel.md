---
title: "can't install kde-devel"
date: 2006-11-09
forum: General Help
---

### Post by Ossipon on 2006-11-09
To compile programs, I need the kde-devel package, however when I try to install it using apt-get, I get the following error message:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde-devel: Depends: kdesdk (>= 4:3.4.3) but it is not going to be installed
             Depends: libarts1-dev (>= 1.4.2) but it is not going to be installed
             Depends: kdelibs4-dev (>= 4:3.4.3) but it is not going to be installed
             Depends: kdebase-dev (>= 4:3.4.3) but it is not going to be installed
             Depends: libkonq4-dev (>= 4:3.4.3) but it is not going to be installed
E: Broken packages

```

Following the broken dependency path leads me to libarts1c2a, which is already the newest version according to apt-get

Using google I found some information on this. The problem is usually caused by not having kubuntu.org kde repositories, I've checked this and I do have those.

I'm using kubuntu 6.10 on an amd64 architecture. Any help would be greatly appriciated:)

---

