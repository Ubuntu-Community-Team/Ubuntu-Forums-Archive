---
title: "Few Questions Before I Install ;)"
date: 2006-07-10
forum: General Help
---

### Post by blackdahliamurder on 2006-07-10
I have a bit of background in Linux in general, so I'm not total noob. But had a few questions before I installed (K)(U)buntu.

1. Is there a way I can take off packages I don't need during the install? Such as the game.

2. Will I be able to play around in the kernel? ;)

3. And are is ndiswrapper or wireless applications that come with the instalation?

Thanks.

---

### Post by hellmet on 2006-07-10
1) Nope
2)Dunno(no knowledge abt. that)
3)Yes(afaik ,u need to install them using Synaptic)

---

### Post by Delkster on 2006-07-10
The installer doesn't really ask almost any question (except probably in expert mode which I haven't tried) so you'll need to uninstall afterwards what you don't want.

What do you mean by "playing around in the kernel"? Of course it's possible to compile your own if that's what you want. Personally I run the prepackaged kernels (which work pretty well for me in Ubuntu).

---

### Post by aysiu on 2006-07-10
Use the Alternate CD. Do a server install, and you can choose whatever packages you want.

You can play around with the kernel after the installation, but I don't know how to do that.

I don't believe *ndiswrapper* comes with the default installation, but it is available in the repositories if you have a wired connection to fetch the packages: > Package ndisgtk

    * breezy (net): graphical frontend for ndiswrapper (installation of Windows WiFi drivers) [universe]
      0.5-1ubuntu1: all
    * dapper (net): graphical frontend for ndiswrapper (installation of Windows WiFi drivers) [universe]
      0.6-0ubuntu1: all
    * edgy (net): graphical frontend for ndiswrapper (installation of Windows WiFi drivers) [universe]
      0.6-0ubuntu1: all

Package ndiswrapper-source

    * hoary (misc): Source for the ndiswrapper linux kernel module [universe]
      0.12+1.0rc2-1: i386
    * breezy (misc): Source for the ndiswrapper linux kernel module [universe]
      1.1-4ubuntu2: all
    * dapper (misc): Source for the ndiswrapper linux kernel module [universe]
      1.8-0ubuntu2: all
    * edgy (misc): Source for the ndiswrapper linux kernel module [universe]
      1.8-0ubuntu2: all

Package ndiswrapper-utils

    * warty (misc): User space tools for ndiswrapper
      0.10-1: i386
    * hoary (misc): Userspace utilities for ndiswrapper
      0.12+1.0rc2-1: i386
    * breezy (misc): Userspace utilities for ndiswrapper
      1.1-4ubuntu2: amd64 i386
    * dapper (misc): Userspace utilities for ndiswrapper
      1.8-0ubuntu2: amd64 i386
    * edgy (misc): Userspace utilities for ndiswrapper
      1.8-0ubuntu2: amd64 i386

---

