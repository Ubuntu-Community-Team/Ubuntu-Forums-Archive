---
title: "Login Screen fails to load"
date: 2008-06-11
forum: General Help
---

### Post by markins06 on 2008-06-11
I changed my splash screen and once I changed it and rebooted my login screen never loaded.


it just had a black screen (my background choice) and a 'loading' cursor. Any suggestions?

I did change my splash screen back to default under the command prompt but still no luck

Thanks

---

### Post by NikoC on 2008-06-11
IGNORE: I MISREAD YOUR POST AND THOUGHT YOU HAD A PROBLEM WITH THE LOGIN SCREEN, NOT THE SPLASH THEME...
Sorry 

And what if you delete the folder containing the theme? Gnome doesn't find it anymore and it should choose the default provided by ubuntu instead...

e.g. in a terminal type:
ls /usr/share/gdm/themes

This will get you a list of all your installed login themes, now knowing the name of the theme that you have recently chosen and is thus messing up your system you can in a terminal type:

sudo rm -r /usr/share/gdm/themes/theme_name

Then just reboot... hope it works,

Cheers.

---

### Post by markins06 on 2008-06-11
Thanks bro, that worked perfectly. I thought i did delete the login file but I did not. I didn't know the dir that the login was loaded into so I didn't delete the correct file.

Thanks for the input.

---

