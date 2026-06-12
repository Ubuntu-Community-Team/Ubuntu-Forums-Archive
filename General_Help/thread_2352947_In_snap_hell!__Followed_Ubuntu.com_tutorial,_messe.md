---
title: "In snap hell!  Followed Ubuntu.com tutorial, messed up"
date: 2017-02-17
forum: General Help
---

### Post by MechaMechanism on 2017-02-17
I followed this how to here; [https://www.ubuntu.com/download/cloud/conjure-up](https://www.ubuntu.com/download/cloud/conjure-up)

Nothing worked.  Did snap remove conjure-up and now there's all this snap stuff running on my computer.  How do I remove all the snap stuff that conjure-up installed.  I am going to try the tutorial again.  I just need to know how to reset snap to default and uninstall the software and stop programs.  I thought that when you uninstalled conjure-up it would uninstall the lxc stuff.

---

### Post by deadflowr on 2017-02-17
You can see all the snaps installed with
```
snap list
```
then use either the remove command or maybe try disable.
use
```
snap help
```
to get a rundown of the various commands you can utilize to control snaps.

---

### Post by DuckHook on 2017-02-17
What "snap stuff" and "lxc stuff" are you referring to? Both snap and lxc are part of a default Ubuntu install these days and are natural elements of the OS. I've never used *conjure-up*, but it would appear to be just a stack of apps on top of lxc and running inside a snap. If you remove it, both snap core and lxc libraries will remain on your computer, as they should. Without them, you may break some functionality.

If your computer is behaving strangely in a non-default way, then you must provide detailed description of such behaviour. There is nothing to go on in your initial post.

BTW, it is a good idea when trying out new stuff to first run them inside a VM.

---

### Post by MechaMechanism on 2017-02-18
> **DuckHook said:**
> What "snap stuff" and "lxc stuff" are you referring to? Both snap and lxc are part of a default Ubuntu install these days and are natural elements of the OS. I've never used *conjure-up*, but it would appear to be just a stack of apps on top of lxc and running inside a snap. If you remove it, both snap core and lxc libraries will remain on your computer, as they should. Without them, you may break some functionality.

If your computer is behaving strangely in a non-default way, then you must provide detailed description of such behaviour. There is nothing to go on in your initial post.

BTW, it is a good idea when trying out new stuff to first run them inside a VM.

I did sudo snap remove lxd and it worked, no more processes.  I will try it out in an VM first.

---

