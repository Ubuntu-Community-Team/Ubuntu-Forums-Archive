---
title: "Saving terminal sessions/tabs"
date: 2008-04-29
forum: General Help
---

### Post by mivo on 2008-04-29
I usually have three tabs/profiles open in the Gnome terminal. Is there a way to save them so that they are automatically restored after a reboot? I believe the KDE terminal offers that option (been a while since I played with KDE, so not entirely sure).

---

### Post by pro003 on 2008-04-29
i'm not quite sure wht you mean by three profiles after reboot, but you can save session by:

```
System > Preferences > Sessions > Session Options
```

---

### Post by mivo on 2008-04-29
That's for the entire system, unfortunately. I basically want to only save the current terminal session, not the whole Gnome/system.

---

### Post by alex1973 on 2009-06-10
Have you found a solution?
Thanks.

---

### Post by nothingspecial on 2009-06-10
Use screen. When you first open the terminal run screen.

When you want to log out press Ctrl + A then Ctrl + D.

When you log back in type screen -r.

A list of detached screen seesions will be presented to you. Type screen -r process_id_number and the session you want will  reappear.

See man screen for everything it can do.

---

### Post by Baelus on 2009-06-10
> **nothingspecial said:**
> Use screen. When you first open the terminal run screen.

When you want to log out press Ctrl + A then Ctrl + D.

When you log back in type screen -r.

A list of detached screen seesions will be presented to you. Type screen -r process_id_number and the session you want will  reappear.

See man screen for everything it can do.

Will screen survive a reboot?

---

