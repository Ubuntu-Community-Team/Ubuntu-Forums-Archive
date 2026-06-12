---
title: "banshee-1: unmet dependencies?"
date: 2008-06-01
forum: General Help
---

### Post by | MM | on 2008-06-01
Hi,

I enable [this]("https://launchpad.net/~banshee-team/+archive") PPA so i could try out the Banshee release candidates.

Unfortunately, when i try to install banshee-1, i get the following:
```
matthew@matthew-desktop:~$ sudo apt-get install banshee-1
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
  banshee-1: Depends: libboo2.0-cil (>= 0.8.1.2865) but it is not going to be installed
             Depends: libnotify0.4-cil (>= 0.4.0~r2998) but it is not installable
E: Broken packages
```

Has anyone managed to get banshee-1 to install?  Any pointers?

Cheers

---

### Post by | MM | on 2008-06-09
bump

---

### Post by mc4man on 2008-06-09
libboo2.0-cil (>= 0.8.1.2865) that version is not available in ubuntu repos
[http://packages.debian.org/lenny/libboo2.0-cil](http://packages.debian.org/lenny/libboo2.0-cil)
libnotify0.4-cil (>= 0.4.0~r2998) is also not available (at all)
[http://packages.debian.org/lenny/libnotify0.4-cil](http://packages.debian.org/lenny/libnotify0.4-cil)

At _first glance_ there seems to be no issues if you install them
The first one will replace an existing ubuntu (hardy) version - that's the one to look at. (what uses it and will it/they have problems with higher version)
The 2nd one stands alone won't be a problem

edit: tested and installed banshee-1 (keeping banshee)(On hardy)
On my system the only thing that uses libboo2.0 is banshee, so shouldn't be an issue, just install it (ie. _don't uninstall_ your current libboo2.0, just download the 2 .debs to your desktop, double click on and let the package manager deal with it). Then install banshee-1. This way you'll keep your current banshee install and be able to install/use banshee-1

---

