---
title: "Radeon Driver in 64 Bit"
date: 2007-10-29
forum: General Help
---

### Post by jcfisher on 2007-10-29
I've been having some trouble with my video card, an ATI Radeon 9200.  On my 64 bit (Gutsy) system, direct rendering isn't enabled and no amount of tweaking can fix it.  However, when I run it from the 32 bit installation CD, direct rendering (and compiz) works.

On 64 bit:
```
$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: www.mesa3d.org

```

On 32 bit:
```
$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

```

So it seems as though the radeon driver uses Mesa for 64 bit and Tungsten Graphics for 32 bit. 

Tungsten works, Mesa doesn't - any ideas how I can either make Mesa work, or switch to the Tungsten driver?

---

### Post by Ehtetur on 2007-10-29
I also got an ATI Radeon card and I'm running Gutsy x86_64
> $ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: ATI Technologies Inc.

I think you're running the default ATI that shipped with Ubuntu.
I enabled restricted drivers to get the ATI accelerated graphics driver installed:
System --> Adminstration --> Restricted Driver Manager.
Once enabled, it installs xorg-driver-fglrx and some dependencies.

In addition, for me to get compiz working, I had to install xserver-xgl.

---

### Post by jcfisher on 2007-10-29
Thanks for your help.  Unfortunately, when I open the Restricted Drivers Manager, it tells me that my hardware does not need any restricted drivers (this might be because ATI no longer officially supports my video card, and the open-source driver's documentation says it's fully compatible, which apparently isn't true).  How can I force it to use the ATI driver?

---

### Post by gimmy_bond on 2007-10-30
I have the same card, and also had the same problem. I went to:
apllications/add-remove. there in the repository under "system tools" you will find ATI Binary x.org driver. after the installation, the problem seem to have gone away.

---

### Post by jcfisher on 2007-10-31
Again, thanks.  Unfortunately direct rendering / compiz still didn't work after I installed the ATI X.org Binary Driver package.  My glxinfo has changed a bit, though:

```
$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: Mesa project: www.mesa3d.org

```

Any guesses?

---

### Post by Ehtetur on 2007-11-02
Look for Section "Device" in /etc/X11/xorg.conf and change Driver to "fglrx"
I'm guessing it's set to ati or vesa...

If that don't work, you can always backup xorg.conf and go nuclear: :evil:
> aticonfig --initial

---

### Post by jcfisher on 2007-11-05
Still nada - changing the driver in xorg.conf to fglrx causes no change, and running aticonfig gives the following output:

```
$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.

```

---

