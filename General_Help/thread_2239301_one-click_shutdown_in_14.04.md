---
title: "one-click shutdown in 14.04"
date: 2014-08-13
forum: General Help
---

### Post by freesitebuilder on 2014-08-13
Just upgraded from 12.04 to 14.04

Is there a way to shut down immediately from the menu, rather than click the menu icon and then click the button that appears on the screen? Probably not, as the menu item is "shutdown ..." rather than"shutdown" but I thought I'd ask anyway.

TIA

---

### Post by CantankRus on 2014-08-13
In the terminal
```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true
```

---

