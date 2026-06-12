---
title: "Kernel Upgrade - missing linux-restriced-modules"
date: 2007-09-01
forum: General Help
---

### Post by zend on 2007-09-01
I just did a system update and one of the things updated was the kernel to version 2.6.21.5.  If I try to use the new kernel it won't load my nvidia module.  It still works if I boot to the old kernel.  I think it's because it didn't load the linux-restricted-modules, but there doesn't seem to be a version for kernel-2.6.21.5.  Is this common with new kernels?  Will a new linux-restricted-modules be forthcoming?

---

### Post by Culprit on 2007-09-01
I read somewhere, that nVidia drivers need to be updated also.
You may build nVidia drivers for your new kernel.

---

### Post by kostkon on 2007-09-01
How did you install your nvidia drivers?

---

### Post by zend on 2007-09-01
I installed them using apt-get.

---

### Post by kostkon on 2007-09-01
Maybe you didn't get the update for the linux-restricted-modules yet, for some reason.

Try to do
```
sudo apt-get update
```

and then
```
sudo apt-get upgrade
```
if it says that there are updates.

Or do it graphically by opening the *Update Manager*.

---

### Post by zend on 2007-09-01
There are no updates for the nvidia drivers and that's not the problem.  Its the linux-restricted-modules that is required for this kernel, but it doesn't seem to exist for this kernel.

---

### Post by Handssolow on 2007-09-01
What is the latest kernel on offer?
2.6.20-16-
2.6.21-??

Prior to the kernel update I was running 2.6.20-16-generic then  the new kernel update arrived, followed here by several x-server crashes, Was it just my Nvidia restricted driver that needs to work with the new kernel?
I was surprised when uname -r showed I was back to running 2.6.20-386 when previously I'd been running generic. After modification of my menu.lst to choose generic and sudo apt-get update and sudo apt-get dist-upgrade eventually I'm back eventually with a GUI. 

Should I be running 2.6.21- ?

---

### Post by david_2001 on 2007-09-01
As far as I was aware, Ubuntu doesn't have a 2.6.**21** kernel (2.6.20 in feisty and 2.6.22 in gutsy), so  that 2.6.**21** kernel must be a custom jobbie that's either been compiled from source or has come from some third-party repository.  On that basis, there won't be an official Ubuntu restricted modules package, which means that if you need the official nvidia drivers then they will have to be installed manually.

---

