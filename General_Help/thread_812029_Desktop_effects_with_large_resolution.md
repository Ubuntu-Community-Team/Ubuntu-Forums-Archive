---
title: "Desktop effects with large resolution?"
date: 2008-05-29
forum: General Help
---

### Post by m0u53m4t on 2008-05-29
Compiz-Check is telling me that my resolution is too high to do effects (I'm running dual moniters through an ATI 8800 card).

Is there any way I can still get any kind of nice eye candy seeing as I've got a good card and it's not being utilized at all? Bit it making compiz work with this resolution, or an alternative program that supports this res?

---

### Post by alienexplorers on 2008-06-03
Exactly what resolution are you running?

---

### Post by Forlong on 2008-06-03
m0u53m4t, please post the output you got.

---

### Post by m0u53m4t on 2008-06-03
owen@ubuntu-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc R481 [Radeon X850XT-PE]
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz. 

Would you like to know more? (Y/n) y

 Your resolution is 2560x1024 but the maximum 3D texture size that your
 graphics card is capable of is 2048x2048. Thus Compiz won't be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again).

---

### Post by Forlong on 2008-06-04
You need to decrease your total resolution to at least 2048x1024, I'm afraid.
The fglrx driver does not support any greater resolution than that on your graphics card.

---

### Post by m0u53m4t on 2008-06-04
Ahh gutting, no way I can get any other kind of eye candy?

Even if its basic and doesn't require hardware accelleration?

---

### Post by TSJason on 2008-06-04
Technically you can override the limit by editing the /usr/bin/compiz file (it's just a shell scripts). You'll want to change the TEXTURE variable to = the largest dimension of your desktop, for example:

```
#TEXTURE_LIMIT=$(glxinfo -l | grep GL_MAX_TEXTURE_SIZE | sed 's/.*=[^0-9]//g')
TEXTURE_LIMIT=2560

```

DISCLAIMER: THIS MIGHT BREAK YOUR X SESSION AND VERY LIKELY WON'T WORK
but you might get lucky :-)

---

### Post by Forlong on 2008-06-04
The only other thing you could try is enabling Metacity's compositing manager -- but that only supports effects for programs that make use of it, like real transparency in the GNOME terminal (but not anywhere else) or the fancier multimedia popus and the new effect when running an application from the GNOME panel, of course.


edit: **[COLOR="Red"]Do not fiddle with /usr/bin/compiz[/COLOR]**
Instead, try running Compiz like this: ```
SKIP_CHECKS=yes compiz
```
If this fails, there's nothing you can do.

---

### Post by m0u53m4t on 2008-06-04
That doesn't work, it just screws up my graphics.

How do I enable the metacity one?

---

### Post by Forlong on 2008-06-04
> **m0u53m4t said:**
> How do I enable the metacity one?
```
gconftool-2 -s -t bool /apps/metacity/general/compositing_manager true
```

---

### Post by m0u53m4t on 2008-06-04
And what exactly does that give me? :P

Edit: Ooft, minimizing animations and stuff glitch a bit and arnt smooth at all :/

My question is, how come I can run the same resolution and have effects on vista? Is it just the fglrx driver? And if so can I run an open source alternative or anything?

---

### Post by Forlong on 2008-06-04
> **m0u53m4t said:**
> My question is, how come I can run the same resolution and have effects on vista? Is it just the fglrx driver?
Well, you can't really compare Vista's effects to Compiz but yes, it's a driver problem.
> **m0u53m4t said:**
> And if so can I run an open source alternative or anything?
Remove the fglrx driver via *System &#8594; Administration &#8594; Hardware Drivers* (reboot) and give it a try. I don't know how well supported your card is, though.

---

### Post by m0u53m4t on 2008-06-04
No dual screen, unfortunately.

Oh well, thanks anyway!

---

