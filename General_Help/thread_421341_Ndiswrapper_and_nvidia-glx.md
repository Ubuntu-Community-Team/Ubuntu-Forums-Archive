---
title: "Ndiswrapper and nvidia-glx"
date: 2007-04-24
forum: General Help
---

### Post by Sp4cedOut on 2007-04-24
I'm a linux noob with a broadcom 4310 card and I got it to work with ndiswrapper (using Edgy).  The first thing I did was install the nvidia-glx package so my GeForce Go 6150 would work properly.

$ sudo apt-get update
$ sudo apt-get install nvidia-glx

However, when I installed from the live CD it installed the generic kernal (is that the right word to use?) but nvidia-glx installed the 386, so when I boot I can either boot as generic or as 386.

The problem is, in order to get ndiswrapper to work I had to get the newest version and build it, all my build packages are off the live CD and installed under the generic kernal, ndiswrapper will not work under 386 and I can't rebuild it.  Naturally, nvidia-glx won't work under generic.  I don't have a wired internet connection available so I can't download the packages on the 386 to build ndiswrapper either.

So my situation is: if I boot as generic I can get the internet to work but nvidia-glx won't.  If I boot as 386, nvidia-glx works, but the internet won't.

Any help appreciated.

---

### Post by spd106 on 2007-04-25
This is strange, the nvidia-glx package does work with the -generic kernel. Did you install from the official repos or a third party?

---

### Post by Sp4cedOut on 2007-04-25
nvidia-glx won't work with ndiswrapper in the -generic kernel, the problem is, I can't build ndiswrapper on the -386 kernel without the build-essential package, which I can't get without an internet connection.

I do have the internet from the generic kernel, is there any way to get the 386 build-essential package from there?

---

### Post by spd106 on 2007-04-25
There is only one build-essential package, what you want are the kernel-headers and you can install these then reboot to the other kernel and build ndiswrapper.

---

