---
title: "Recent updates removed all drivers."
date: 2008-05-28
forum: General Help
---

### Post by Syroco on 2008-05-28
I just downloaded the updates today for Ubuntu.  After the restart my sound & video drivers were removed.  I am currently running in lowgfx mode.

I tried to reinstall my video drivers, I used Add/Remove and even downloaded the package from Nvidia.  The Add/Remove said I still had the drivers installed.  I tried to then run the Nvidia control panal application and it told me I have no Nvidia drivers installed. Weird.

I then attempted to install my package I got from the Nvidia website, terminal would install it but it still wouldn't do anything.

:/

---

### Post by Zorael on 2008-05-28
External drivers compiled by yourself or via a third-party script (such as the official nvidia driver) will need to be recompiled upon a kernel upgrade. They're tailored for a given kernel, see. The only way you can get the nvidia driver to keep working after such an upgrade would be to use the nvidia-glx* packages, which will be upgraded along with the kernel.

You'll want to find and completely remove the nvidia packages and then reinstall them to get it to work properly again. This might be possible with the official installer, via envyNG (package of the same name in lowercase), or by entering this in a terminal.
```
$ sudo aptitude purge ~nnvidia-glx
```
I'm not completely sure that will do the trick if you installed via the installer.

---

### Post by Syroco on 2008-05-28
Was the updates I did a kernel update?
I was using Hardy Heron 8.04, and the little bloop said updates are available so I downloaded them in the Update Manager.  Pretty standard stuff.

---

