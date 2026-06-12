---
title: "Accidentally Deactivated GDM in Service Control Panel"
date: 2006-11-11
forum: General Help
---

### Post by greggooch on 2006-11-11
Alright my situation is laughable - shouldn't have disregarded the warning about possibly rendering my system useless.  At any rate I was trying to restart the service and deactivated it.  The screen went blank and does the same thing after booting every time.

Fortunately I can still SSH into it and SCP my files out of it should I need to reformat but I'd rather not.  Anyone have a command I could run to restart it?

---==Gooch==---

---

### Post by David_T on 2006-11-11
What happens when you do:

sudo /etc/init.d/gdm start

?

---

### Post by greggooch on 2006-11-11
The screen still stays black.  I've also tried  /etc/init.d/gdm restart and it stops and starts successfully.  I've checked the runlevels and gdm is set to 2345 and rebooted.  Are these the correct runlevels?

---

### Post by scooper on 2006-11-12
> **greggooch said:**
> The screen still stays black.

Did you press Ctrl-Alt-F7 to force it to switch to the virtual terminal running X (and hopefully gdm)?

---

### Post by scooper on 2006-11-12
Another idea might be to run "startx" or "startx gnome" (?) from a text login to force X to start and then run gnomecc (or gnome-control-center?) so you can use the GUI admin panel to fix the login settings to reinstate gdm.  Sorry if I'm being vague - I'm slogging under Windoze at the moment.  Just hoping to provide things to try. :)

---

