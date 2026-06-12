---
title: "How do I remove the gdm splash image?"
date: 2006-11-07
forum: General Help
---

### Post by brottman on 2006-11-07
I know there is a splash manager tool gui that can do it, but I would like to know how to do this manually as well. Is there a config file somewhere that I can just change to not make the splash show up after I log in?

---

### Post by strabes on 2006-11-07
That's not a GDM theme; it's a splash screen. GDM themes change how your login screne looks.

You can remove the splash screen by using the Configuration Editor (run gconf-editor or Panel menu->System Tools->Configuration Editor) and then going to /apps/gnome-session/options/show_splash_screen, and unchecking the checkbox.

You can also CHANGE splash screens with the configuration editor on /apps/gnome-session/options/splash_image. Right click on splash_image key and choose edit key, where you see Key Value enter the new key value /path/to/your_splash.png. Now restart the X server with Ctrl-Alt-Backspace and login and you can see your new splash screen.

---

### Post by brottman on 2006-11-07
Thank you!!

---

