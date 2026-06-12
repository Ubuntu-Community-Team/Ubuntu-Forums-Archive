---
title: "Can't even find GFXboot"
date: 2008-01-25
forum: General Help
---

### Post by SoberWarlock on 2008-01-25
I can't find GFXboot in Synaptic Package Manager. I am trying to install USplash screen and i'm having a hard time doing that. Or is there a way I can install these splash screens manually which would be less of a hassle. :confused:

---

### Post by divague on 2008-01-25
install startupmanager, go to the appearence tab. In the usplash themes section click on manage usplash theme->add and select the theme you want to use. Then in the combo usplash theme: select the theme you added. For the grub background menu it's kind of the same thing but in the bootloader themes section, and make sure the "Use background image for bootloader menu" is checked. (Just in case make a backup of /boot/grub/menu.lst)

---

