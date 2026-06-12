---
title: "Add/Remove Applications does not work at all.."
date: 2007-12-24
forum: General Help
---

### Post by noodleey on 2007-12-24
hi,

I am quite new on Ubuntu (and Linux, as well)... I just installed the operating system and updated it and seems like no problem with the internet connection or anything but i am having a trouble with add/remove application section.. It *_doesn't matter what i am trying_* to install, it gives an error like this;

*"**[I]Cannot install 'application name'***

This application conflicts with other installed software. To install 'application' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to solve this conflict."[/I]

---

### Post by taurus on 2007-12-24
Maybe you don't have enough repos in your /etc/apt/sources.list.  Close Add/Remove and open synaptic:  System -> Administration -> Synaptic Package Manager -> Settings -> Repositories.  Make sure there is a check for everything in there except Source code and CDROM.  Close it and press Reload.  Now, see if you can install whatever you wanted to install before.

---

### Post by p_quarles on 2007-12-24
Do like it says: open the Synaptic package manager (it's under the Administration menu). It will give you feedback about which package is conflicting with everything you try to install.

---

### Post by noodleey on 2007-12-24
> **taurus said:**
> Maybe you don't have enough repos in your /etc/apt/sources.list.  Close Add/Remove and open synaptic:  System -> Administration -> Synaptic Package Manager -> Settings -> Repositories.  Make sure there is a check for everything in there except Source code and CDROM.  Close it and press Reload.  Now, see if you can install whatever you wanted to install before.

yeah i have done excatly what you have said works now! thank you ((:

---

