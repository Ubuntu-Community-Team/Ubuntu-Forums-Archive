---
title: "ATI card not working in GNOME + GLX but working in GNOME"
date: 2008-03-09
forum: General Help
---

### Post by misternewbie on 2008-03-09
I installed mt card successfully in GNOME mode. I checked fglrxinfo & glxinfo and it stated that the card was installed and it is direct rendering, but when I log on into GNOME + GLX session and checked fglrxinfo & glxinfo, it showed Mesa not ATI nad it is not direct rendering. Is there any solution to this problem or is my card unsupported?

---

### Post by uberlube on 2008-03-09
ATI cards aren't supported very well. Grab yourself an Nvidia as soon as humanly possible.

---

### Post by misternewbie on 2008-03-09
> **uberlube said:**
> ATI cards aren't supported very well. Grab yourself an Nvidia as soon as humanly possible.

Ya It is, but i seen people with an ATI have effects (beryl/compiz) running somewhat smoothly. Is there anyway to make my card work in GNOME +GLX or is it impossible?

EDIT: my card is x1300 sorry for not mentioning it before.

---

### Post by imbjr on 2008-03-09
I'm not sure why you have problems - but I have an ATI 1300 and have stuff like the desktop effects working - so it is possible.

Basically, I let the restricted drivers manager handle the install and it seemed to be handled ok. This is all under Gutsy mind - Feisty was less able.

---

### Post by Peter09 on 2008-03-09
Try going here and downloading ENVY. 
 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It will install the correct drivers for your card, although with ATI there is no guarantee of success.

PC

---

### Post by misternewbie on 2008-03-10
Thank everyone, I finally got it working. If I upgraded to Gutsy will I still have every settings or will I have to re-do the process?

---

