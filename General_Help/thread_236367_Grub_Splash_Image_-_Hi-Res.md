---
title: "Grub Splash Image - Hi-Res"
date: 2006-08-14
forum: General Help
---

### Post by Mr_Congeniality on 2006-08-14
Well, I want to get the most out of my new laptop, and this topic's purpose is really just to give Ubuntu more love when the computer is booting up.

now I've read the how to for the GRUB splash image on the forums, but the resolution is bothering me.

I want the GRUB to display 1680x1050 resolution (and of course the splash image is going to be 1680x1050 as well).

What do I need to do to achieve this?

---

### Post by spiral777 on 2006-08-14
There is a good reason for the low resolution, none of the drivers have loaded yet. The resolution for most graphical bootloaders is pretty low, because it has to work without any drivers on any system.

---

### Post by Mr_Congeniality on 2006-08-14
SuSE and Fedora don't load any drivers and they seem to pull it off.

---

### Post by cptnapalm on 2006-08-14
> **Mr_Congeniality said:**
> SuSE and Fedora don't load any drivers and they seem to pull it off.

Built into the kernel itself, perhaps?

If I remember correctly, there is some odd problem with suspend and or hibernate if what ever it is which higher resolution boot up requires.  (A framebuffer thing, possibly.)

---

### Post by Mr_Congeniality on 2006-08-14
High-res boot-up should become a new feature in the next version of Ubuntu, but it might be to late to impliment that.  Probably will have to wait until next year.

However, I doubt that it is built into the kernel.  Do you remember when you start linux setup, there is a VGA option on the bottom, which allows you to select resolutions?  It then proceeds to boot the live version of ubuntu, and if you specified 1024x768 only 320x240 pixels of the screen were used, meaning no stretched boot up image.  The drivers aren't even loaded yet then, so there has to be a way to get the GRUB Splash Image to be high resolution.

---

### Post by Tomosaur on 2006-08-14
You can get a higher resolution usplash by altering the vga setting AND the usplash image, but you cannot raise the resolution of the Grub splash.

---

### Post by Mr_Congeniality on 2006-08-14
That's ghey.

---

### Post by videodrome on 2006-08-15
add either vga=799 or 795 to the end of the boot/grub/menu.1st line that boots yer kernel.

---

### Post by Mr_Congeniality on 2006-08-20
> **videodrome said:**
> add either vga=799 or 795 to the end of the boot/grub/menu.1st line that boots yer kernel.

and this will do it, am I right?  I'm gonna make sure I back up my original file first.

---

