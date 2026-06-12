---
title: "GDM Login Window opens... then fades"
date: 2008-07-03
forum: General Help
---

### Post by JGault on 2008-07-03
I'm trying to open the GDM login window settings so that I can allow the local administrator to logon as root.

It opens for maybe 1 second... Then fades.

Background: I changed the video settings from OpenGL to "software" in America's Army... Now it does the same thing and can't be run. I'd delete it, but I can't without being root. 

Everything else seems to work fine. Suggestions?

---

### Post by cariboo on 2008-07-03
Why log in as root, sudo is much safer. When I first started using linux, Redhat 6.0, if I remember correctly, I screwed up a whole lot of things running as root, on the other hand I learned a lot fixing the screwups.

Jim

---

### Post by JGault on 2008-07-04
Good question! 
I'm not too familiar with Linux security... I don't want to login as root all the time, just this one time so that I can remove the software that is configured incorrectly. Then I can reinstall. 

Still. More disturbing is the GDM window apparition. Is this tied to the software-rendering, or is this a symptom of some other bug. I can't find this problem anywhere in the forums. I'll likely have to reinstall.

Thanks for the reply Jim.

---

### Post by JGault on 2008-07-04
BTW Been to Williams Lake. Love the area.

---

### Post by Gunman1982 on 2008-07-04
I wouldn't concentrate on the issue with not getting a root login but rather on the issue on how to uninstall americas army as normal user. Is there a script you run which tries to uninstall it but says insufficient rights? or are you just trying to planly delete it? You can use sudo or the graphical pendant gksu for each of both:

sudo rm -r ~/americas_army_directory (deletes the whole aa directory in your home dir)

sudo ./script_which_uninstalls_americas_army (runs the script with root privileges)

---

