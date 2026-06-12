---
title: "What makes my kernel unique(?)"
date: 2007-03-26
forum: General Help
---

### Post by B-Con on 2007-03-26
I was wondering, what exactly sets one kernel apart from someone else's kernel (assuming they have the same architecture)? As best I can tell, there are two things that can make a kernel I use different from the default kernel: my config file and the specific mods I've added to it. Is that right? (The current config file I know is located in /boot/config-`uname -r`).

Following from that, what about the kernel that comes with Ubuntu? What sets it apart from the vanilla kernel? Are there any specific mods added to the vanilla kernel, or is it just all configuration settings?

---

### Post by Ramses de Norre on 2007-03-26
Why should your kernel be different from others? All ubuntu i386 kernels of the same version are identical...

The ubuntu kernel has been patched, so the source is a little different from the vanilla kernel. This is done by most distro's and makes certain things work or work better.

---

### Post by B-Con on 2007-03-26
Ok, that's what I was wondering. I'm just looking for all the ways that the exact kernel I use might possible differ from the exact kernel someone else uses. So far I assume it's just the config file and specific mods/patches.

If I were to recompile the kernel, I presume that I should find and apply the Ubuntu-specific patches?

---

