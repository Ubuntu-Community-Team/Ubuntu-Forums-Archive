---
title: "No Desktop on Boot"
date: 2007-05-21
forum: General Help
---

### Post by kasio on 2007-05-21
Hi,

Recently, when I start up Ubuntu, it loads the panels and launchers but not the main desktop. For example, there is no icons and I cannot right click on the desktop and no wallpaper. I think this may be a problem with Nautilus, as when I type 'nautilus' in the terminal, the desktop loads, along with my Home folder opening.

Hope someone can help...

Kassim (14 years old)

---

### Post by kasio on 2007-05-21
*bump*

Can any1 help me? I really need to get this fixed...

---

### Post by smcleish on 2007-05-22
I'm getting the same - but it's only happened in the last few days (since Sat 19th), and I don't think there's been a nautilus update for ages.

Simon

---

### Post by kasio on 2007-05-22
Please will someone, maybe a developer, try and respond.

I have to manually add nautilus to the start up programs.

There is also no "Nautilus" icon on the splash screen but ther is the "panel"

---

### Post by smcleish on 2007-05-23
This problem just went away; once I had it working, and saved the session, it worked OK. So perhaps the problem is that the system wasn't able to pick up old saved sessions for some reason. So when you have the desktop try accessing Sessions from the System Preferences and run "Save the current session" from Session Options.

---

### Post by yakitori3 on 2007-05-24
same problem, don't know how to fix any ideas please

---

### Post by ThrashJazzAssassin on 2007-05-25
Same for me

---

### Post by yakitori3 on 2007-05-26
going to alt f2 - gconf-editor got me back my home access directory
apps>nautilus>preferences>show_desktop to true

Hope that helps some.

---

### Post by kasio on 2007-05-27
saving the seesion with nautilus worked for me

---

