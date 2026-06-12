---
title: "Ubuntu keeps on logging me out"
date: 2008-02-14
forum: General Help
---

### Post by Trapper Dave on 2008-02-14
As it says in the title, Ubuntu will log me out at random yet short (around 5 - 20 minute) intervals. Also if I go to System > Preferences > Screensaver, it will also log me out. Does anyone know how I can fix it?

---

### Post by Trapper Dave on 2008-02-15
I have just realised, that when I get logged out from my trying to view the screensaver options and Ubuntu reboots and I log back in that there are some error messages:
[LIST]
[*]"The panel encountered a problem while loading "OAFIID: Deskbar_applet" Do you want to delete the applet from your configuration?"

[*]"The panel encountered a problem while loading "OAFIID: GNOME_MixerApplet" Do you want to delete the applet from your configuration?"

[*]"The panel encountered a problem while loading "OAFIID: GNOME_Panel_TrashApplet" Do you want to delete the applet from your configuration?"
[/LIST]

---

### Post by Carl H on 2008-02-15
This sounds like either a broken/corrupt screensaver, or a screensaver that your graphics driver can't handle. 

Try changing your screensaver to "none" and see what happens.

---

### Post by Trapper Dave on 2008-02-15
Is there anyway that I can do that from the terminal? Trying to access the options to change it will cause the machine to reboot/log me out.

---

### Post by Trapper Dave on 2008-02-15
I've just realised something with regards to this, my machine will only reboot/log me out, if I select the screensaver option on my non-default screen. Would that have anything to do with it, and would I have anyway to disable it on that screen? 

I've disabled the screensaver from starting as I think that that was the cause of the rebooting.

---

