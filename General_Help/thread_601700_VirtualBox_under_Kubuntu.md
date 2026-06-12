---
title: "VirtualBox under Kubuntu"
date: 2007-11-03
forum: General Help
---

### Post by MrBaseball34 on 2007-11-03
Kubuntu 7.10, Gutsy Gibbon on Dell Optiplex GX150.

Trying to install VirtualBox, using GDebi pakage installer. 
I get this error and don't know what to do:

Error: Dependency is not satisfiable: libqt3-mt


Also, I have Microsoft Optical Mouse and the screen flickers when I move the mouse around.
Is there anything I can do to remedy this?

---

### Post by ubukool on 2007-11-03
Hi there,

I looked in the repositories and libqt3-mt is a package you can download and install, so go into synaptic and do this, or you can type:

sudo apt-get install libqt3-mt

in the terminal.  When you've installed this package, try installing VirtualBox with GDebi once again.  It should work.

I don't know about the mouse problem, sorry.

---

### Post by MrBaseball34 on 2007-11-03
It seems that other libs are necc. too. Why wasn't this stuff installed when I installed Kubuntu?
Is there a place to get all packages at once .vs downloading  each of them separately? Is
there a way to install all the required ones without having to install them one by one?

I'm having a little trouble with this.

---

### Post by ubukool on 2007-11-04
normally, if you download from a repository, when you opt to download a package it will automatically mark the dependencies for installation too.  I'm wondering why you aren't installing VirtualBox from the Kubuntu repositories, unless it's not in there.

The VirtualBox website should show what dependencies are needed to be installed, so maybe you just need to check there, make a list, and install them from the repositories.  It can be a pain when you are trying to install software yourself from individual packages which is why synaptic is so wonderful, it makes like so much easier.

Good luck! :)

---

### Post by MrBaseball34 on 2007-11-04
> **ubukool said:**
> <SNIP>I'm wondering why you aren't installing VirtualBox from the Kubuntu repositories<SNIP>

I downloaded the desktop install from Kubuntu. I do not yet have an internet connection on that system
because I can not get it set up.

Linux heads often wonder why Windows users don't make the change, well, this is the BIGGEST reason.

At least Windows works out of the box and you don't have to go download 10 million different things to get it to work. Even the networking is simple unlike Linux.

This is just too damn frustrating and the documentation is too lacking in information/examples.

---

