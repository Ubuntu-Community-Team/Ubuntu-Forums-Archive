---
title: "Dependency problems libimobiledevice4"
date: 2014-07-15
forum: General Help
---

### Post by MorrisseyJ on 2014-07-15
Hi, 

I seem to have gotten myself in to some trouble with dependencies. 

In an attempt to get my iphone working on ubuntu i installed: sudo dpkg -i libimobiledevice4_1.1.6-git20140105_amd64.deb

Since doing so i have had an error listed on the top panel of my machine with the following dialogue:
> An error occured, please run Package Manager from the right click menu or apt-get to see what is wrong. The error message was'Error:BrokenCount>0'. This usually means that your installed packages have unmet dependencies.

There is no right click option to open the package manager. 

sudo apt-get -f install, gives: 

> Correcting dependencies... failed.
The following packages have unmet dependencies:
 libimobiledevice4 : Depends: libtasn1-3 (>= 2.14-0) but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

sudo apt-get install libtasn1-3, gives:

> Package libtasn1-3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libtasn1-3' has no installation candidate



sudo apt-get remove libimobiledevice4, gives: 

> You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gvfs-backends : Depends: libimobiledevice4 (>= 1.1.5) but it is not going to be installed
 libgpod-common : Depends: libimobiledevice4 (>= 0.9.7) but it is not going to be installed
 libgpod4 : Depends: libimobiledevice4 (>= 0.9.7) but it is not going to be installed
 upower : Depends: libimobiledevice4 (>= 0.9.7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

So it seems that i can't get libimobiledevice4 working because it depends on a package that no longer exists, and I can't remove it because other components now rely on it. 

Does anyone have any ideas about what i can do to fix this. I can't currently install anything from the software centre as these errors need to be corrected first. 

Thanks in advance.

---

### Post by bapoumba on 2014-07-15
Please try :
```
sudo dpkg --purge libimobiledevice4 
```

You may want to try the following if the first attempt does not work :
```
sudo dpkg --purge --force-depends libimobiledevice4 
```

---

### Post by MorrisseyJ on 2014-07-15
Thanks, 

That appeared to work. 

> sudo dpkg --purge libimobiledevice4

Didn't work - giving: > dpkg: dependency problems prevent removal of libimobiledevice4:
but
> sudo dpkg --purge --force-depends libimobiledevice4 worked, despite dependency problems. 

I then ran sudo apt-get install -f, and reinstalled libimobiledevice4 from the repos. 

Everything appears to be working fine now. 

Thanks very much,

j

---

### Post by bapoumba on 2014-07-15
Glad to see you got it to work :)

---

