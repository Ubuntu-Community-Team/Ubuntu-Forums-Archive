---
title: "Shutdown dialog change from Breezy to Dapper"
date: 2006-08-02
forum: General Help
---

### Post by Neil Crighton on 2006-08-02
I couldn't find this searching, so sorry if it's already been answered.

In the breezy shutdown dialog (the choices that came up when you select shutdown/logout or whatever it's called from the menu), you had a choice to shutdown and 'save current settings'.  This wasn't hibernating, it just saved the layout of your windows and the directories they pointed to so they'd be preserevd next time you restart.  Dapper does not give you this option.   My problem is that my current setup is stuck on the setup I had the last time I shutdown and 'saved current settings' in Breezy.

Could anyone tell me how to (in Dapper) change what windows appear in which workspace areas, and which directories they point to when Gnome loads?

Thanks.

---

### Post by Neil Crighton on 2006-08-06
No-one else has had this problem?

Do you have any ideas where else I could look to find a solution?

---

### Post by professor_chaos on 2006-08-07
This should do the trick for you. From the terminal.
```
gnome-session-save
```

I'm not sure why the devs decided to take this out of dapper. I think it was a good feature.

---

### Post by Neil Crighton on 2006-08-08
Thanks very much, that works.  I've discovered another way I probably could have done this in the system/preferences/session gui menu.

---

