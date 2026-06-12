---
title: "GnomeBaker icon HUGE in Unity on 12.04."
date: 2012-10-20
forum: General Help
---

### Post by stchman on 2012-10-20
Hello all.

I installed GnomeBaker from the PPA as Brasero is real good at making coasters.

In the Unity launcher the GnomeBaker icon is freaking HUGE.

Is there a fix?  I know it's pretty superficial, but just asking.  It appears that a bug report was filed and nothing was resolved.

Thanks.

---

### Post by uconvert on 2012-11-18
This icon has been driving me nuts as well. The fix is quite simple. Copy the icon /usr/share/icons/hicolor/48x48/apps to your home folder. Then open the icon image with GIMP - click on image > scale and you will see that it is actually a 100x100 pixel image. Correct the size to 48x48 and save as gnomebaker.png. Then (sudo) copy the corrected image to /usr/share/icons/hicolor/48x48/apps. I am running gnome classic on Ubuntu 12.04, so I right-clicked on my applications to edit menus, then chose the new icon image and the icon appears in uniformity with the others. Don't know about unity, I am on a 10 year old Compaq and can't run it, but it should adjust to the new icon.

---

