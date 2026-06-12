---
title: "A error occured with the package manager -  'Error:BrokenCount &gt; 0'"
date: 2007-04-22
forum: General Help
---

### Post by Marc_UK on 2007-04-22
I was installing a Ubuntu package which installed Java, Flash etc through through the "add/remove program".

It later came up with this error on the update thing, and no I cant even use the ad/remove the package manager.

---

### Post by dcstar on 2007-04-22
> **Marc_UK said:**
> I was installing a Ubuntu package which installed Java, Flash etc through through the "add/remove program".

It later came up with this error on the update thing, and no I cant even use the ad/remove the package manager.

Go into Synaptic and use the "Edit-Fix Broken Packages" function.

---

### Post by Marc_UK on 2007-04-22
> **dcstar said:**
> Go into Synaptic and use the "Edit-Fix Broken Packages" function.

Hey that worked perfect, thanks mate.

---

### Post by st0rmbrkr on 2008-02-06
I have this same problem except for it was when I was upgrading to 7.10. I tried opening the Synaptic Packet Manager but it gives me this error and closes;

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by Take0n on 2008-05-27
Hello

I have the same problem but I am able to run the synaptic packet manager. I select fix broken packages it says that it fixed them but I am not able to update or install anything cause I continue to get this error. It has something to do with virtualbox but I dont really know what :\

I get an update notification about "virtualbox-ose-modules-2.6.24-16-generic" but I am not able to update it :\

> You have 1 broken package on your system!

Use the "Broken" filter to locate it

I already tried that but the same.. I click close and the update continues until...
> 
E: /var/cache/apt/archives/virtualbox-ose-modules-2.6.24-16-generic_24_i386.deb: trying to overwrite `/lib/modules/2.6.24-16-generic/misc/vboxdrv.ko', which is also in package virtualbox

I am really stuck I don't know what to do!!

please help me

---

