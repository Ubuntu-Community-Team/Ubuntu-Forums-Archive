---
title: "How to (Properly) Install Netbeans: Plugins Completely Broken!"
date: 2008-07-02
forum: General Help
---

### Post by GenuineXP on 2008-07-02
I'm unsure what the best way to install/configure Netbeans 6.1 is. I downloaded and installed the C/C++ package from their website and ran the installer via sudo. It installed Netbeans to /usr/local. I performed an update of some plugins, and after restarting the IDE I got a bunch of errors saying 11 of my plugins couldn't be loaded... including the plugin manager!

Now I can't access my plugins at all. Just to get things running, I ran Netbeans once as root. This fixed a few things, and allowed me to get back into the IDE as a normal user... but a bunch of plugins still seem to be disabled along with the plugin manager, so I can't even check/configure/enable/disable anything!

First of all, was it a mistake to run the installer as root? Also, how can I fix this plugin problem? Is there a way to manually enable/disable plugins?

Thanks.

---

### Post by rossjman1 on 2008-07-02
Netbeans is in the repos. All you had to do was sudo apt-get install netbeans or install through synaptic.

---

### Post by GenuineXP on 2008-07-02
> **rossjman1 said:**
> Netbeans is in the repos. All you had to do was sudo apt-get install netbeans or install through synaptic.

Version 6.0.1 is in the repos, which didn't have the features I wanted. 6.1 is available for download, so I grabbed that.

In any case, anyone know how I can fix the plugin problem?

Now it seems I rm'ed a file I needed for a clean removal via the installer. Looks like I've got a mess on my hands. Damn ext3 for lacking recovery support! FAT32 ftw!

**EDIT:**

Thanks to rm, updatedb, and locate, it seems I've eradicated Netbeans from my filesystem... I think. Phew.

---

### Post by GenuineXP on 2008-07-02
I installed Netbeans locally (in ~/.local) using the same installer. It had no problem with the updates this time. Seems like this'll have to do for now, though I guess if I ever need to add another user they won't be able to use Netbeans (without adding their own installation).

I'm thinking a permissions problem caused the strange errors with the updates. If I installed as root into /usr/local, would I have to run Netbeans as root to perform updates?

---

