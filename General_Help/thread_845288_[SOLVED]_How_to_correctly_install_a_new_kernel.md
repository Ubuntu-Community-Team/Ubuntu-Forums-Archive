---
title: "[SOLVED] How to correctly install a new kernel?"
date: 2008-06-30
forum: General Help
---

### Post by caljohnsmith on 2008-06-30
I needed to install a previous version of the kernel, so using Synaptic, I just marked the "linux-image-2.6.24.16-generic" package to install. I noticed that it didn't seem to have any dependencies and therefore did not install any additional packages. I was under the impression that I needed all the packages below to use the 2.6.24.16 kernel:
```

linux-headers-2.6.24-16-generic
linux-image-2.6.24.16-generic
linux-restricted-modules-2.6.24-16-generic
linux-ubuntu-modules-2.6.24-16-generic

```
Why doesn't Synaptic consider those other packages as dependencies of the "linux-image-2.6.24.16-generic" package? Don't I need all of them? But regardless, how should I do a new kernel install so I don't have to manually make sure I get all the necessary packages?

Thanks for any help.

---

### Post by sdennie on 2008-06-30
It doesn't automatically install the other three because the kernel image doesn't strictly depend on them and can be used without them.  You will probably want to install those packages though because they contain some fairly common drivers and the headers are useful to have if you need to build new drivers from source.

The reason you have to manually download all 4 explicitly is because normally a meta packages are responsible for getting the current version of three of them (linux-image-generic and linux-headers-generic).  If you are installing an older version, the meta package no longer points at the older kernel.

---

### Post by caljohnsmith on 2008-06-30
> **vor said:**
> It doesn't automatically install the other three because the kernel image doesn't strictly depend on them and can be used without them.  You will probably want to install those packages though because they contain some fairly common drivers and the headers are useful to have if you need to build new drivers from source.

The reason you have to manually download all 4 explicitly is because normally a meta packages are responsible for getting the current version of three of them (linux-image-generic and linux-headers-generic).  If you are installing an older version, the meta package no longer points at the older kernel.
Just to clarify, are you saying I could just install linux-image-2.6.24.16-generic for example, and then let that 2.6.24.16 kernel rely on previous versions of linux-restricted-modules and linux-ubuntu-modules that are all ready installed? (I don't have to install linux-restricted-modules-2.6.24-16-generic and linux-ubuntu-modules-2.6.24-16-generic?)

It seems like it would be risky mixing and mismatching various kernel version modules, but is that not the case? Because then I would have to ask, why would they provide linux-restricted-modules and linux-ubuntu-modules specific to each kernel version?

---

### Post by sdennie on 2008-06-30
No.  When major kernel releases happen, it means that the modules for the currently installed version and the new version are no longer compatible (otherwise, they wouldn't increment the version number).  So, as you suspected, mixing the two versions is not only not advised, it's more or less impossible.  If you want all the packages specific to, for example, the -16 kernel, you will have to manually install them.  For example:

```

sudo apt-get install linux-headers-2.6.24-16-generic linux-image-2.6.24.16-generic linux-restricted-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic

```

Out of curiosity, why do you want to downgrade your kernel?

---

### Post by russlar on 2008-06-30
Question semi-related to this topic: is there any good or bad reason to run 2.6.24-series kernels with gutsy?

---

### Post by sdennie on 2008-06-30
> **russlar said:**
> Question semi-related to this topic: is there any good or bad reason to run 2.6.24-series kernels with gutsy?

I ran a custom compiled 2.6.24 kernel in Gutsy without problems.  I would imagine that you could manually download the Hardy kernels and use them in Gutsy without any problem as well (do NOT set your repos to Hardy and get them via apt-get.  Manually download the .debs and install them with dpkg -i).  The only drawback would be that you won't get automatic updates to the kernels.

---

### Post by caljohnsmith on 2008-06-30
> **vor said:**
> It doesn't automatically install the other three because the kernel image doesn't strictly depend on them and can be used without them.

> **vor said:**
> No.  When major kernel releases happen, it means that the modules for the currently installed version and the new version are no longer compatible (otherwise, they wouldn't increment the version number).  So, as you suspected, mixing the two versions is not only not advised, it's more or less impossible.  If you want all the packages specific to, for example, the -16 kernel, you will have to manually install them.

You've got me confused then, because at first you said "the kernel image doesn't strictly depend on them and *can be used without them*", and then you said "When major kernel releases happen, it means that the modules for the currently installed version and the new version are no longer compatible (otherwise, they wouldn't increment the version number).  So, as you suspected, mixing the two versions is not only not advised, it's more or less impossible." What you say in the second quote is the way I understood it when I asked my original question, but I must be misinterpreting your first quote. So would you please clarify what you meant by "the kernel image doesn't strictly depend on them and can be used without them"? I just want to make sure I'm not missing something here.

---

### Post by sdennie on 2008-06-30
Sure.  The package linux-image-2.6.24-16 can be installed and used without linux-restricted-modules-2.6.24-16, linux-ubuntu-modules-2.6.24-16 and linux-headers-2.6.24-16 (which is why it doesn't depend on them).  What that means is that, if you don't install those other three packages, you won't have some of the modules (and none of the headers) that a normal Ubuntu kernel install has.  The kernel won't fall back and use a different kernels restricted/ubuntu modules and headers, it simply won't have that functionality available.  Hope that clears it up.

---

