---
title: "Grub Customizer not working after upgrade to 12:10"
date: 2012-10-27
forum: General Help
---

### Post by Jonners59 on 2012-10-27
Since I upgraded to 12:10, now on 3 machines, none does Grub Customizer work.  It opens and seems to have saved my original settings.  I "Install" to "File" -> "Install to MBR...".

Also the same on Login Screen.  Can not make changes....

When I reboot Grub has not changed to my new settings.

Any ideas, please?

This is in 32-bit and 64-bit machines, all running xfce...

---

### Post by Jonners59 on 2012-10-28
Seems to also be logged in bugs.

[HTML]https://bugs.launchpad.net/grub-customizer/+bug/1067623[/HTML]

---

### Post by aabed91 on 2012-10-28
I used it to re-arrange my boot list in ubuntu 12.10 and it's work.

---

### Post by Jonners59 on 2012-10-28
> **aabed91 said:**
> I used it to re-arrange my boot list in ubuntu 12.10 and it's work.
Yup, but I found that the more complex, if that is a correct word to use - settings are not saved.  I used it in 12:04 to change the background image and other things.  That is still there but it does not load in 12:10.  This, I have found is a known bug, as per the link.

---

### Post by Jonners59 on 2012-11-30
Resolved.  Thanks to contacting Daniel directly.  Seems it is a probable problem with in Grub that caused the problem.  A step BACKWARDS, sadly.  Here is his eMail to me, I hope it is help for others who may fall foul of this.

> now I also tried setting a background image and it worked well. I used /usr/share/backgrounds/Gran_Canaria_by_ALF.jpg.

However I've seen there are spaces on your image path. So I replaced the underscores of my test image by spaces and voila… this doesn't show up on boot menu. If it really worked on old versions of grub2, then it's a problem of the new one. Grub Customizer quotes the image correctly, so update-grub found's it.

The easiest fix is renaming the directory containing your images from "Images for appearence" to "Images_for_appearence".

Hope it helps!

Bye

---

