---
title: "Can I bypass startup programs?"
date: 2007-03-02
forum: General Help
---

### Post by dresi on 2007-03-02
I'm having troubles with beryl freezing as soon as gnome boots up. The only thing I can do is ctr-alt-backspace back to login.

Is there anyway to bypass the programs defined in the sessions/startup programs like you can do in windows by holding down the ctrl key or something like that?

thanks in advance.

---

### Post by chggr on 2007-03-02
Remove the startup program from the startup programs list:
System -> Preferences -> Sessions -> Startup Programs

---

### Post by dresi on 2007-03-02
Well the problem was actually that I couldn't get into the desktop environment so I couldn't access the session manager. Beryl would lock my computer up as soon as I logged in.

I managed another solution though, I accessed ubuntu through KDE and manually changed the startup scripts in the startup folder.

But thanks anyways.

---

### Post by kpkeerthi on 2007-03-02
cd to ~/.config/autostart and remove the file corresponding to the startup entry

---

