---
title: "How to change Kde Login Manager?"
date: 2008-05-19
forum: General Help
---

### Post by cruzeiro on 2008-05-19
Hi all,
I have kubuntu on my machine with KDE 3.5, i have aptituded the kdmtheme, now in my control panel (kcontrol) i have under look&feel the KDMmanager.
i install my theme and i apply it on my machine, but at reboot of X or machine reboot i see the same bad theme that i have on my control panel under "advanced -> Login manager"
and i don't know how to say as default the KDMmanager and not the Login manager.
anyone know how i can set it? thanks!!

---

### Post by cruzeiro on 2008-05-20
up up up

---

### Post by Exsecrabilus on 2008-05-20
Try setting the theme settings to *Selected only* and checking the box next to the theme you want.

---

### Post by brexsis on 2008-06-20
i have the same problem, but i dont see that option like in gnome "use selected only".

---

### Post by Zorael on 2008-06-20
KDM works a bit weird. Or rather, the way Kubuntu sets its distro-specific defaults works a bit weird. Bear with me:

Upon start of KDM, it checks its configuration files, [FONT="Courier New"]kdmrc[/FONT] and [FONT="Courier New"]backgroundrc[/FONT] located in [FONT="Courier New"]/etc/kde3/kdm/[/FONT].

**If and only if** the Theme= tag in kdmrc is set to **@@@ToBeReplacedByDesktopBase@@@** *and* the Wallpaper= tag in backgroundrc is set to **default_blue.jpg**, it will proceed to *import* Kubuntu settings from [FONT="Courier New"]/etc/default/kdm.d/20_kubuntu_default_settings[/FONT]. These settings will override any earlier settings in kdmrc and backgroundrc.

Do you see the problem? Using KDE tools to modify the greeter (login manager) will break the importing. I believe just applying any change will replace @@@ToBeReplacedByDesktopBase@@@ with just a blank field. Obviously, changing the wallpaper (note: in backgroundrc) will in the same way break things.

If you do this, the only way to get it "right" again is to set all the settings the way you want them, from the ground up. If you examine said 20_kubuntu_default_settings file, you will see what this entails; there aren't a whole lot of tags to change. You'll want to pay extra attention to  Theme= and UseTheme=. If the latter isn't set to true, then well, whatever you set the first one to will be irrelevant. The greeter themes are located in [FONT="Courier New"]/usr/share/apps/kdm/themes/[/FONT].

I generally leave the kdmrc and backgroundrc files alone, and instead make my changes manually (with a text editor) in 20_kubuntu_default_settings. It's a bit of work (but hey, Gnomelings have to do their work in gconf tools), but it is easier to change stuff there; kdmrc is fairly large.

I have attached virgin kdmrc and backgroundrc files if you lost yours. But basically, you'd just need to restore those Theme= and Wallpaper= tags and it will properly import stuff again. Alternatively just go over the whole of kdmrc and change stuff the way you want. If so, pay *extra* attention to Theme=, UseTheme= and UseBackground=. If you don't set FaceSource= to "PreferUser", noone but root will be able to change people's face pictures, too. Again, refer to the 20_kubuntu_default_settings file to get an idea of what it actually changes.

I hope that made sense.

---

