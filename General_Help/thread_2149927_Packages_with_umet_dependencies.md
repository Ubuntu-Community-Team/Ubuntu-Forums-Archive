---
title: "Packages with umet dependencies"
date: 2013-05-30
forum: General Help
---

### Post by ShadowVegan on 2013-05-30
When I try to install anything, I get an error that some of my packages have unmet dependencies.

```
administrator@Desktop:~$ sudo apt-get install gcalctool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcalctool is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libwebkitgtk-3.0-0 : Depends: libgeoclue0 (>= 0.11.1+git20091217) but it is not going to be installed
 unity-webapps-service : Depends: geoclue-ubuntu-geoip but it is not going to be installed or
                                  geoclue-provider
                         Depends: libgeoclue0 (>= 0.11.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

I don't want to install the geoclue software and I don't see why the other software should require it. I tried removing libwebkitgtk3.0-0 but then some other software (that I do want) had unmet dependencies, so I reinstalled it. I want to keep libwebkitgtk-3.0-0 (I don't care about unity-webapps-service, I can delete it if it will help) but I do not want geoclue.

I already tried sudo apt-get update && sudo apt-get upgrade.

When I try sudo apt-get -f install it tries to make me install geoclue.

```
administrator@Desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  geoclue geoclue-ubuntu-geoip libgeoclue0
The following NEW packages will be installed:
  geoclue geoclue-ubuntu-geoip libgeoclue0
0 upgraded, 3 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 34.8 kB/69.1 kB of archives.
After this operation, 326 kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

Is there any way to get around the dependency issue without installing geoclue? I can install still install software with dpkg if that makes a difference in anything.

Thank you.

---

### Post by 2F4U on 2013-05-30
It seems as if you would need geoclue as a dependency:

[https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1120358](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1120358)

---

### Post by ShadowVegan on 2013-05-30
> **2F4U said:**
> It seems as if you would need geoclue as a dependency:

[https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1120358](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1120358)

Yes, but it's more than just the datetime indicator that supposedly depends on it. I don't see why the packages that supposedly depend on it would, and even if they do, is there some way to circumvent this and tell the terminal to do what I want anyway?

As a temporary fix I used sudo apt-get -f install and installed the geoclue software then used sudo rm -rf to remove all of the files assocated with the software so that my system thinks it exists but it can't run because the files don't exist. Would still be nice to know a better method if anyone has any ideas.

---

