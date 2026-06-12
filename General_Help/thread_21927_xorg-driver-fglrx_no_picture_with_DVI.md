---
title: "xorg-driver-fglrx no picture with DVI"
date: 2005-03-24
forum: General Help
---

### Post by slysy81 on 2005-03-24
I am having a problem getting DVI to work with fglrx. If I connect my monitor via DVI, it just goes to a blank screen when the graphical stuff would appear. If I connect it via VGA it works fine. Is there any configuration that needs to be done? Im using an ATI X800XT with Hercules 920Pro LCD monitor. Any help is much appreciated. If you need any more info please let me know!

---

### Post by emperor on 2005-03-24
Are you using a converter on the same connector or switching connectors?

If you are switching connectors, then you need to enable the other connector via "fireglcontrol". In Hoary, this utility does not get installed in the menu automaticly as with Warty; and ATI changed the name. I think it is in: /usr/X11R6/bin

---

### Post by slysy81 on 2005-03-25
Thanks for the suggestion but Im using the same connector with a convertor. If I change the driver to VESA its fine through DVI. I configured the driver by changing it in xorg.conf. I tried your suggestion anyway. Interestingly my card shows up as the following:

Card name : unknown
Chip type : unknown

Is this part of the problem maybe?

---

### Post by Leszek Tarkowski on 2005-03-25
AFAIK this is problem with some Radeon cards. For eample mine :( and yours. No picture with DVI + fglrx. But i have picture with radeon (xorg) driver. I didn't find solution so far. I tested in on debian, gentoo and now ubuntu. No go so far.... So if you will manage to do this, please give me a sign

---

### Post by jarno on 2005-04-19
[QUOTE=slysy81]If I connect my monitor via DVI, it just goes to a blank screen when the graphical stuff would appear. If I connect it via VGA it works fine.[/QUOTE]

Has anyone found a solution to this problem? I'm using Radeon 9250, and I am forced to the xorg driver, which doesn't provide 3D-acceleration. ](*,) 

--
    /jarno

---

