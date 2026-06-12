---
title: "No Screens and Graphics menu :("
date: 2008-06-19
forum: General Help
---

### Post by Sigurney on 2008-06-19
So I have no screens and graphics menu anywhere. Not in System > Administration or ANYWHERE else. I am trying to get dual-monitors working correctly, and I edited my xorg.conf manually. When I rebooted after that I was automatically brought to a screen that looked like this [http://files.myopera.com/sjosul/blog/Screenshot-Screen%20and%20Graphics%20Preferences.jpg](http://files.myopera.com/sjosul/blog/Screenshot-Screen%20and%20Graphics%20Preferences.jpg) and I could edit my monitor brand/model screen sizes etc etc. How in gods name do I get to that screen without reediting xorg and rebooting everytime?

EDIT: I am using Ubuntu 8.04 Also, how do I stop/start xserver/gdm from command line?

---

### Post by avtolle on 2008-06-19
To add this to your menus, right click Applications, select Edit Menus. Scroll down to Other, in the right column should be a list of applications. Check Screens and Graphics, then close. Then, open Applications menu, and it should show up. OR

From terminal```
sudo displayconfig-gtk
```which will get you there as well.

HTH.

---

