---
title: "Synaptic Error, Please help. thanks"
date: 2007-09-18
forum: General Help
---

### Post by Arghhh haha on 2007-09-18
Hi there, just installed Ubuntu 7.04, i think its really cool, although I wanted to show my friend what it looked like so i tryed to install a screen recorder, but it didnt work, so i just forgot about it and carried on browsing the new things available on this OS, just as i read about Compiz Fusion i decided to give it a go to find that i couldn't run the Synaptic package manager.

The error i get:

E: The package recordmydesktop needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I have done a few searches to see what kind of solutions there are for this sort of problem, and tryed what a few members suggested, to no avail. So here i am asking you all:-D

---

### Post by dcstar on 2007-09-19
> **Arghhh haha said:**
> Hi there, just installed Ubuntu 7.04, i think its really cool, although I wanted to show my friend what it looked like so i tryed to install a screen recorder, but it didnt work, so i just forgot about it and carried on browsing the new things available on this OS, just as i read about Compiz Fusion i decided to give it a go to find that i couldn't run the Synaptic package manager.

The error i get:

E: The package recordmydesktop needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I have done a few searches to see what kind of solutions there are for this sort of problem, and tryed what a few members suggested, to no avail. So here i am asking you all:-D

The cached files are in /var/cache/apt/archives, you may want to move/delete them (after you make sure you just didn't run out of disk space in the root filesystem).

Synaptic also has a setting to delete cached files in the preferences.

---

