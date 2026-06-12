---
title: "Help! I Broke My Login!"
date: 2007-07-07
forum: General Help
---

### Post by osarusan on 2007-07-07
I checkmarked "Enable Accessible Login" in the Login Preferences manager, and now, when the login screen is supposed to load, I get a black screen and the mouse cursor turns into the "waiting" icon forever... It never brings up a prompt to allow me to log in!

Is there a way I can uncheck "Enable Accessible Login" without using Gnome? From the terminal, or whatever?

Thank you!

---

### Post by bettlebrox on 2007-07-07
Go to one of the virtual consoles (Ctl-Alt-F1) and login. Using *sudo* edit /etc/gdm/gdm.conf and look for this line:

[INDENT]AddGtkModules=true[/INDENT]

Change it to 

[INDENT]AddGtkModules=false[/INDENT]

And restart GDM:
[INDENT]sudo /etc/init.d/gdm restart[/INDENT]

If that doesn't work comment out (with a #) the two lines that start with AddGtkModules and GtkModulesList .

---

### Post by osarusan on 2007-07-07
I was able to get to that point, however AddGtkModules was already set to false, and commented out.

I think it may have something to do with the Login theme. I set it to "plain" but then I set it back to what it originally was. So if it wasn't enabling the accessible login, it may be that the login theme isn't loading. Is there a way I can change the login theme in gdm.conf?

---

### Post by CREEPING DEATH on 2007-07-07
Crap like this is why I went to Debian.  There is no reason and no excuses for the login screen to be broken, and it has been since 6.10.

CD

---

### Post by bettlebrox on 2007-07-07
> **osarusan said:**
> I was able to get to that point, however AddGtkModules was already set to false, and commented out.

I think it may have something to do with the Login theme. I set it to "plain" but then I set it back to what it originally was. So if it wasn't enabling the accessible login, it may be that the login theme isn't loading. Is there a way I can change the login theme in gdm.conf?

Look in /etc/gdm/gdm.conf-custom for a line starting with: GraphicalThemes=

Make a backup copy of the file first. :)

---

### Post by osarusan on 2007-07-07
I was able to fix it all by enabling automatic login. It logged me in ok, and i switched the themes around until it worked.

---

