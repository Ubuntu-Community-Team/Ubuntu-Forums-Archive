---
title: "Broken package prevents the installation of anything else"
date: 2007-06-22
forum: General Help
---

### Post by kentshultz on 2007-06-22
I was just messing around and installing some VMware packages in Synaptic and the package vmware-player didn't finish installing correctly.  Synaptic reported that it was getting a bad exit status (1) on it's post-installation script.

So I tried moving the package and found I couldn't do that either, error on the PRE-removal script.

I've tried everything under the sun.  Removal, Complete removal, reinstallation, etc.  It won't go away.

Now the Update Manager is trying to install some updates and it can't because of the broken package.  It returns the following message:

"It is impossible to install or remove any software. Please use the package manager 'Synaptic' or run 'sudo apt-get install -f' in a terminal to fix this issue at first."

Kind of an ominous message.  Of course, apt-get install -f simply tries to reinstall vmware-player to no avail.

I would really appreciate any advice on resolving this issue.  I'm sure it's not the first time it has happened, and I'm guessing it's not a problem specific to the particular VMware package.  I don't even care to get the package installed, I just want to fix Synaptic!

Thanks in advance.

---

### Post by jusmurph on 2007-06-22
Should just be able to remove it via synaptic?

You can even sort by broken packages, mark for complete removal and apply.

---

### Post by kentshultz on 2007-06-22
I've tried removing it.  Bad exit code on Pre-removal script:

"E: vmware-player: subprocess pre-removal script returned error exit status 1"

---

### Post by grim4593 on 2007-06-22
It does something similar for me for firestarter... Except it didn't break synaptic, I just can't use it or remove it.

---

### Post by DarkStarAeon on 2007-06-29
I've had the same issue on my laptop, can't remove vmware in synaptic or add/remove, reinstall does nothing either. It's a royal pain, everytime I want to add/remove any program I have to deal with the vmware thing in the details terminal, it's aggravating.

---

