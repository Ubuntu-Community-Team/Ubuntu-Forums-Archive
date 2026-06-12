---
title: "Is Aptitude capable of installing local .deb package?"
date: 2006-11-11
forum: General Help
---

### Post by Akhran on 2006-11-11
If I have a packageA.deb on my local harddisk, is aptitude capable of installing packageA.deb package and resolve any dependency issue automatically (by downloading the necessary files from the Internet) ? If so, what is the required parameter for aptitude?

Thanks.

---

### Post by autocrosser on 2006-11-11
I don't know--I normally use dpkg if I'm in a terminal or Gdebi if I feel like using GUI---

---

### Post by d3v1ant_0n3 on 2006-11-11
Slightly off topic, I got this error when i mistyped in terminal earlier- what does it mean? Or is it just a joke?

                  This aptitude does not have Super Cow Powers.

---

### Post by ciscosurfer on 2006-11-11
Issue```
sudo dpkg -i *yourpackage*.*deb*
``` to install that package.  It will not resolve dependencies.

What you can do though, is iinstall with the method I mention above, and then from within a terminal, issue (all one line)```
sudo aptitude update && sudo aptitude upgrade && sudo aptitude dist-upgrade
```That will update your sources.list, and upgrade is used to install the newest versions of all packages currently installed on the system (which will resolve dependencies)
...
dist-upgrade, in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages.

---

### Post by ciscosurfer on 2006-11-11
> **d3v1ant_0n3 said:**
> Slightly off topic, I got this error when i mistyped in terminal earlier- what does it mean? Or is it just a joke?

                  This aptitude does not have Super Cow Powers.

I guess it's a joke of sorts.  It just means you entered the command wrong or improperly b/c it doesn't know how to parse the information you typed.

---

### Post by aysiu on 2006-11-11
I'm not 100% certain about this, but I believe *gdebi* integrates with Synaptic to resolve dependencies if they're available. Don't quote me on that, though.

Have you tried just double-clicking the .deb file?

---

### Post by autocrosser on 2006-11-11
Yes--I've had Gdebi resolve deps --it will have a tab in the window listing deps & a prompt to download & install them.

---

### Post by Akhran on 2006-11-11
I think if dependencies are not met, the .deb package cannot be installed. So, aptitude update, etc can't resolve the dependency issue of a package (the .deb package mentioned above) that has not been installed?

PS. Please correct me if I'm wrong.

Since dpkg -i cannot resolve dependency issues, was wondering if aptitude has the ability to install .deb package **and** resolve the dependency issue automatically by downloading the necessary packages from the Internet.

Thanks !


> **ciscosurfer said:**
> Issue```
sudo dpkg -i *yourpackage*.*deb*
``` to install that package.  It will not resolve dependencies.

---

### Post by Akhran on 2006-11-11
I don't have GUI installed (server installation). Only the terminal is available.

Thanks :) Would gdebi work in console mode?

> **aysiu said:**
> I'm not 100% certain about this, but I believe *gdebi* integrates with Synaptic to resolve dependencies if they're available. Don't quote me on that, though.

Have you tried just double-clicking the .deb file?

---

### Post by ciscosurfer on 2006-11-11
Try aysiu's advice above.  Gdebi should open up the package and should resolve dependencies.  Just double-click the file.

You can do it in a console by issuing```
cd /*directory_where_package_is*
gdebi *yourpackage.deb*
```

---

### Post by deanlinkous on 2006-11-12
**dpkg -i**
then try a **apt-get -f install** to clean up dependency issues

---

