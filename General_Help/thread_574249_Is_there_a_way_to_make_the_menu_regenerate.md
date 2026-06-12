---
title: "Is there a way to make the menu regenerate?"
date: 2007-10-12
forum: General Help
---

### Post by episodic on 2007-10-12
I deleted WINE from my menu instead of unchecking it. I need it back. It won't come back on the application menu. I've even uninstalled and reinstalled. How can I get it back?


Gutsy 7.1

Thanks!

---

### Post by Brucevdk on 2007-10-12
From the thread: [Wine is not in my Application's Menu]("http://ubuntuforums.org/showthread.php?t=477108")
> **Brucevdk said:**
> 
Anyways the following should solve your problem.

Open *~/.config/menus/applications.menu* in your favorite text editor and search for the following:
```

<Name>wine-wine</Name>
<Deleted/>

```

Remove the <Deleted/> tag and the wine menu should reappear in your applications menu.

---

### Post by puelly on 2008-07-09
Thanks

---

