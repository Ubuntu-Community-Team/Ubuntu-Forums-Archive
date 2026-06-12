---
title: "in synaptic..."
date: 2007-02-25
forum: General Help
---

### Post by Mateo on 2007-02-25
what is the difference between "mark for removal" and "mark for complete removal"?

---

### Post by Maestro23 on 2007-02-25
> **Mateo said:**
> what is the difference between "mark for removal" and "mark for complete removal"?

Mark for complete removal:  Removes any configuration files associated with the package.

Good link to bookmark: [https://help.ubuntu.com/community/SynapticHowto#head-2e236f992402f4adc61a9bb59f0751ce54fea1dc](https://help.ubuntu.com/community/SynapticHowto#head-2e236f992402f4adc61a9bb59f0751ce54fea1dc)

---

### Post by Mateo on 2007-02-25
what does that mean.  I always mark for complete, and I always have to still delete all the crap in ~/.whatever

---

### Post by aysiu on 2007-02-25
> **Mateo said:**
> what does that mean.  I always mark for complete, and I always have to still delete all the crap in ~/.whatever
According to [this Mepis guide](http://www.mepisguides.com/Mepis-6/synaptic/synaptic-complete-remove/synaptic-complete-remove.html): > Complete Removal will delete all the configuration files associated with a Program, and any libraries attached to the program as well. If you downloaded a program earlier, this will also remove the program from the Apt-Repositories cache. So it appears to be universal (or system-wide) configuration files and libraries--not user-specific ones (the ones in ~/.whatever).

---

### Post by Maestro23 on 2007-02-25
Nevermind, aysiu beat me to it.:popcorn:

---

### Post by Mateo on 2007-02-25
why would anyone ever **not** want to delete configuration files for programs you no longer use?  Now i'm scared that there are files on my computer from before I started using complete removal, wasting my hard drive space.

---

### Post by aysiu on 2007-02-25
Are you low on hard drive space? If so, I'd clean out the several-megabyte .deb files in /var/cache/apt/archives before deleting a bunch of 1 kilobyte or 2 kilobyte text files in your home directory.

```
sudo apt-get clean
``` will clean out the .deb installer files.

---

### Post by Mateo on 2007-02-26
no, I'm not low on hard drive space, but I still don't like wasted space.

---

