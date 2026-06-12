---
title: "Stellarium graphics issue in 16.04"
date: 2016-12-09
forum: General Help
---

### Post by Trogladyte on 2016-12-09
Hi all.

I've just installed 16.04 on a rather elderly Compaq laptop. It doesn't seem to like the OpenGL setup.  The log reveals 

Mesa version is fine. We should not see a graphics problem.
GLSL version number detected: 1.2
This is not enough: we need GLSL 1.30 or later.
You should update graphics drivers, graphics hardware or use the --mesa-mode option.
Else, please try to use an older version like 0.12.5, and try there with --safe-mode.

I'm a bit puzzled, as stellarium used to work just fine on 14.04 with an even older laptop.

Any ideas or explanations?

Thanks for taking the time to read this.

---

### Post by Impavidus on 2016-12-10
Ubuntu 16.04 comes with Stellarium 0.14.3, Ubuntu 14.04 with Stellarium 0.12.4, and it seems the newer version doesn't like your graphics hardware. It suggests trying with the --mesa-mode option. I don't know what that's supposed to do, but you can try. I guess it will switch to less fancy graphics to work on older hardware.

---

### Post by Yellow Pasque on 2016-12-10
[http://stellarium.org/wiki/index.php/FAQ#OpenGL_issues](http://stellarium.org/wiki/index.php/FAQ#OpenGL_issues)

> It suggests trying with the --mesa-mode option. I don't know what that's supposed to do, but you can try. I guess it will switch to less fancy graphics to work on older hardware. 

It will use the CPU to emulate the needed GLSL features. Don't expect good performance...

---

### Post by Trogladyte on 2016-12-12
So do I need to run it from the command line with that switch?

---

### Post by Trogladyte on 2016-12-12
> **Temüjin said:**
> [http://stellarium.org/wiki/index.php/FAQ#OpenGL_issues](http://stellarium.org/wiki/index.php/FAQ#OpenGL_issues)



It will use the CPU to emulate the needed GLSL features. Don't expect good performance...Actually that seems to run OK. I'm pleasantly surprised. Im guessing the graphics must be impressive if you can run the real deal.

---

### Post by sgage on 2016-12-13
Hi,

Newer Stellaria don't like older graphics HW. At some point they switched how they did graphics - I think it was when they went from 0.12 to 0.13. On my old Compaq Presario (ca. 2008), I have to use 0.12.6, which I compiled from source obtained at the Stellarium website. A list of the dependencies is given, along with instructions - it's aways compiled readily for me for several different distros of different vintages.

As I was poking around on their site just now, I saw this:

"Stellarium 0.12.7 has been released today!

Yes, the series 0.12 is LTS for owners of old computers (old with weak graphics cards). This release has ports of some features from the series 1.x/0.15:
- textures for deep-sky objects
- star catalogues
- fixes for MPC search tool in Solar System Editor plugin"

So I'm running LTS Stellarium on my LTS Ubuntu MATE right now :KS



> **Trogladyte said:**
> Hi all.

I've just installed 16.04 on a rather elderly Compaq laptop. It doesn't seem to like the OpenGL setup.  The log reveals 

Mesa version is fine. We should not see a graphics problem.
GLSL version number detected: 1.2
This is not enough: we need GLSL 1.30 or later.
You should update graphics drivers, graphics hardware or use the --mesa-mode option.
Else, please try to use an older version like 0.12.5, and try there with --safe-mode.

I'm a bit puzzled, as stellarium used to work just fine on 14.04 with an even older laptop.

Any ideas or explanations?

Thanks for taking the time to read this.

---

