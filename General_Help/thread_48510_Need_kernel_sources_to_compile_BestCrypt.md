---
title: "Need kernel sources to compile BestCrypt"
date: 2005-07-12
forum: General Help
---

### Post by tbraun on 2005-07-12
Hello!

I am trying to compile BestCrypt, but I need the kernel sources for it. Ok, so I'm a newbie and don't really know where to find those sources.

Are they part of the standard Hoary installation? If so, where are they? Or do I need to download (apt-get) them?  What exactly would I have to do for that?

Any help would be greatly appreciated.

Thank you very much...

Tom

---

### Post by Xian on 2005-07-12
Open Synaptic and download either the linux-tree-2.6.10 (includes patch sets) or linux-source-2.6.10 package. It will be placed in the /usr/src directory and provide what you are needing.

---

### Post by az on 2005-07-12
You should probably try to use the linux-headers for your kernel first.  They are preconfigured and meant to do just what you want - compile modules for your kernel.  Pick the headers version that matches your kernel (the stock kernel is 2.6.10-5-386)

Some software complains when you do not have the whole linux tree but that is generally not the case.  It is harder to screw up using just the headers.

If you have not already, install build-essential.  It is what you need to build stuff...

---

### Post by tbraun on 2005-07-12
[QUOTE=azz]You should probably try to use the linux-headers for your kernel first.  They are preconfigured and meant to do just what you want - compile modules for your kernel.  Pick the headers version that matches your kernel (the stock kernel is 2.6.10-5-386)

...

If you have not already, install build-essential.  It is what you need to build stuff...[/QUOTE]

Thank you for the reply.  What would I have to tell apt-get, or where do I have to point the software I am trying to compile, in order to take advantage of those headers?

How do I install 'build-essential'?

Sorry for all those questions, but I'm pretty new to this.

Thank you very much!

Tom

---

### Post by Xian on 2005-07-12
[QUOTE=tbraun]How do I install 'build-essential'?[/QUOTE]
Open a terminal (Applications > System Tools > Terminal) and type the command below. This will open the [Synaptic](https://wiki.ubuntu.com/SynapticHowto?) package tool. Do keyword searches for the packages you are looking for, such as build-essential, linux-source, linux-headers, etc. Then just highlight the package with a mouse click and choose the install option. 
```
$ sudo synaptic
```

---

