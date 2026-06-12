---
title: "Back to 386 kernel??"
date: 2006-08-15
forum: General Help
---

### Post by AlliumPorrum on 2006-08-15
My Ubuntu server is still crashing all the time when I use any client application that creates a socket connection to it. 

One thing I could try is to go back to 386 kernel from my current 686 one, and see if it helps. Could someone please tell me how to do this??

---

### Post by Arisna on 2006-08-15
```
sudo aptitude install linux-image-386
```

Type that at a console to install the 386 image.  You can then select the 386 image at boot.  If you are satisfied with this, you may remove the 686 image meta-package at a later time using the following:

```
sudo aptitude remove linux-image-686
```

---

### Post by kpkeerthi on 2006-08-15
search for 'linux-image' in Synaptic. This should list all kernels available in the repository. Select 386 kernel for installation. Reboot and choose the appropriate kernel from GRUB boot menu. If X fails to start, do:
```

sudo aptitude install linux-restricted-modules-`uname -r`

``` and you should be fine.

---

### Post by AlliumPorrum on 2006-08-15
Yeah, that made it, thank you very much! There seems to be something wrong with 686 kernel, because now all connections are working just fine. Me happy!:rolleyes:

---

### Post by az on 2006-08-15
Install linux-386 instead of linux-image-386.   The former depends on the corresponding restricted modules package, too.

What kind of CPU do you have?

---

### Post by skale on 2006-08-15
Yeah, I tried the 686 kernel and X wouldn't load!

Stupid Pentium 4. :mad:

---

### Post by az on 2006-08-15
> **skale said:**
> Yeah, I tried the 686 kernel and X wouldn't load!

Stupid Pentium 4. :mad:

Well, as mentioned, did you just install the linux-image package or the linux-686 package?  If you are using a binary-only video driver (ATI or Nvidia), that's what's gonna happen if you don't install the corresponding linux-restricted-modules package.

The restricted-modules are not dependant on the linux-image package since a lot of people do not use them (binary-only is evil) but the linux-686 metapackage brings everything in.

---

