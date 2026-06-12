---
title: "Unzip uninstall scare"
date: 2012-11-23
forum: General Help
---

### Post by thulefoth on 2012-11-23
On 11.10 WUBI XFCE, I installed "Unzip" with Synaptic.  It did not resolve the need/lack of an unzip tool, so I marked it for removal.

Although Unzip required not dependencies and installed by itself, upon Marking it for Removal, Synaptic now reports :

"To be removed -

java-wrappers
lintian
opticalraytracer
ubuntu-desktop"

Wow.  That seems drastic.  Is this a symptom of trouble?  What should  I do?   - Thx!

---

### Post by snowpine on 2012-11-23
Unzip is a "dependency" of the package ubuntu-desktop, so if you install unzip it will also uninstall ubuntu-desktop. Now, ubuntu-desktop is only a "metapackage" (a dummy package that installs a bunch of other packages) so your computer won't explode if you uninstall it. HOWEVER, there is no benefit to uninstalling unzip, therefore I recommend you don't do it.

[http://packages.ubuntu.com/oneiric/ubuntu-desktop](http://packages.ubuntu.com/oneiric/ubuntu-desktop)

---

### Post by thulefoth on 2012-11-23
I saw that Unzip itself is marked as a metapackage ... I usually  am vigilant for the dialog showing additional dependencies when installing a package, but it apparently works a little different with metapackages.

I'm planning to make a full install of Ubuntu Server soon (then put Xfce on it), moving away from WUBI after years (tho I like that it has been retained for those who find it convenient...).  Since this is not a malfunction-symptom, I will 'control myself' and just let sleeping dogs lay.   Thank you!

---

### Post by sdowney717 on 2012-11-23
It is like an a la carte all you can eat buffet. You pick up things that you simply forget about unless they start squeaking.

---

