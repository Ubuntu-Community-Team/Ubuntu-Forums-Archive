---
title: "Start Gaim Minimized at Login"
date: 2006-12-07
forum: General Help
---

### Post by charlie. on 2006-12-07
How do I set Gaim to start automatically at startup, logging in to all listed accounts and minimizing to the "system tray" area?

I've managed to work out how to *start* gaim at login, but not how to get it to minimize to the tray.

Thanks.

---

### Post by fuzziefuz on 2007-01-14
Hi! I'm also looking for a possibility to start gaim minimized, but nothing found so far... Did you find a solution in the meantime?

---

### Post by fuzziefuz on 2007-01-14
Found something! It's not perfect because you have to start gaim in away mode, but for me thats acceptable.

Just activate the "Iconify on away" plugin and start gaim in away mode (gaim -w).

Source:
[http://groups.google.at/group/alt.os.linux.mandrake/browse_thread/thread/91ae271135fa2974/b45a053559166707%23b45a053559166707](http://groups.google.at/group/alt.os.linux.mandrake/browse_thread/thread/91ae271135fa2974/b45a053559166707%23b45a053559166707)

---

### Post by Atomic Dog on 2007-01-14
I have gaim listed in my sessions.  It starts and stays minimized in the tray.

---

### Post by Buck2348 on 2007-01-14
> **Atomic Dog said:**
> I have gaim listed in my sessions.  It starts and stays minimized in the tray.
Same here.  But I can't start it with "gaim -w"--"invalid option".  Anybody know a way to un-minimize it with a terminal command?  I'd like to bind a hotkey to do that.

Thanks,
Buck

---

### Post by Ti-nérisson on 2007-02-07
"gaim -w" doesn't work for me either but in fact it isn't necessary. Since I've activated "Iconify on away" Gaim is minimized when it starts.

---

### Post by heratech on 2007-02-18
In the buddy list options plugin there is an option Hide the buddy list when created.
Regards

---

### Post by eustace on 2007-02-20
> **heratech said:**
> In the buddy list options plugin there is an option Hide the buddy list when created.
Regards

In Edgy by default there is no such option, you have to install the "extended preferences" plugin.

```

sudo apt-get install gaim-extendedprefs

```

Restart Gaim, go to Tools -> Plugins -> Extended preferences -> Configure plugin.

---

### Post by TimJBart on 2007-02-27
thank it has worked a treat.  Just noticed Skype has a box to tick:

"Do not show main window on startup"  

:)

---

