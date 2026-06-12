---
title: "Installing generic .deb's."
date: 2013-08-01
forum: General Help
---

### Post by b-no on 2013-08-01
Greetings

Can you install a generic .deb (ie, meant for Debian) in any of Ubuntu's variants? Or are there specific compilation instructions when converting sourcefiles into the various .deb packages?

Thanks!

---

### Post by vasa1 on 2013-08-01
I suspect it's not a good idea but someone will come along and explain why. Please wait until then!

---

### Post by oldfred on 2013-08-01
I think you are back to the bad old days of dependency hell. Each time you install what it says it needs to support the app, that support program needs another and it goes on forever. 

A program needs to be complied for the version you have so you have the correct supporting files. Many applications have PPA's that users create where they compile the program for each version of Ubuntu (or other systems). 

If it does not have any real dependencies it may work, but you then are on your own.

---

### Post by BBQdave on 2013-08-01
> **b-no said:**
> Can you install a generic .deb (ie, meant for Debian) in any of Ubuntu's variants?

As Ubuntu is based on Debian - the program you wish to install, is most likely in the Ubuntu repos.

Safest to install from trusted repos - Ubuntu repos for Ubuntu system :) 

A side question: does anyone know of a program in the Debian repos that is not available in the Ubuntu repos?

---

### Post by dino99 on 2013-08-01
As post #3 above said, ubuntu is not baked the same way as debian is (custom compile/settings/dependencies).
So be ready to resolve some unexpected issues. :guitar:

---

### Post by deadflowr on 2013-08-01
If a deb file says it's meant for Debian and not other derivatives, then it would be safe to say that it is not a generic deb file.

Most places I have seen which provide a deb installation file will list on what system it can be installed, and some of the better ones will guide you through the process if you need anything extra installed before hand on your particular system.

Take Openoffice as an example.
Yesterday I decided to try it out on a saucy install. But in order to install the deb, I had to first purge the libreoffice from the system, as it has conflicting files between the two.

---

### Post by b-no on 2013-08-01
OK, thanks for the replies guys. I expected as much, but since the deb i was looking at didn't state any particular distro, I was unsure.

> **BBQdave said:**
> 
(...)
A side question: does anyone know of a program in the Debian repos that is not available in the Ubuntu repos?

Given that Debian is upstream from Ubuntu, I wouldn't be surprised that there are quite a few programmes not synchronised to Ubuntu's repositories; I would imagine highly-specific scientific programmes would fall into this category.

---

### Post by Dennis N on 2013-08-01
OTOH,

If you are curious if the .deb will work or not, you could always try to install with gdebi package installer. It will inform you before installing if:

1) all dependencies are met.
2) dependencies will have to be downloaded (from your software sources).
3) dependencies cannot be met.

In 1 and 2, you can proceed to install and see how the program works on the system. The gdebi installer takes care of the dependency installation in case 2. There may be other reasons the program won't work, such as inadequate graphics support, for one. If it doesn't work right, you can always uninstall it.

In case 3, it's probably best to give up.

The humble bundle games are often offered as .deb files not created for just *buntu.  

Good Luck.

---

