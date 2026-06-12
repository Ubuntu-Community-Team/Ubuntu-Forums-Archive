---
title: "Compiz not working after upgrading to Hardy"
date: 2008-04-29
forum: General Help
---

### Post by specialcharacter on 2008-04-29
Hello all,

I upgraded to Hardy and now compiz isn't working for me. I get the following output:

```

Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


```

The strange thing is that if I run hardy from the live cd, compiz works fine!


My system is a Dell XPS M1330, and the graphics card is "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller".

I removed "linux-backports-modules-2.6.22-14-generic", which i installed to get my card working under gutsy, but is no longer needed.

my xorg.conf is attached, along with the xorg.conf from gutsy.


Any ideas would be appreciated; I miss compiz!!

---

### Post by russo.mic on 2008-04-30
Did you try running compiz --replace?  

It won't by default run over metacity. 


Russo

---

### Post by specialcharacter on 2008-04-30
> **russo.mic said:**
> Did you try running compiz --replace?  

It won't by default run over metacity. 


Russo
Yeah, same error message.

As im using an intel card, I have 915resolution installed. Hardy Heron uses the correct resolution when running from the live cd, so I think I have something installed which is messing up my display.

I tried uninstalling 915resolution, and recieved the same error (and a horrible resolution).

Is there a way to uninstall all graphics drivers and start again?

---

