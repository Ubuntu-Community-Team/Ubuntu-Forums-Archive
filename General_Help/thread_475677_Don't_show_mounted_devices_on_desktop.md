---
title: "Don't show mounted devices on desktop"
date: 2007-06-16
forum: General Help
---

### Post by tL0z on 2007-06-16
Hello,

Is there any way to don't have shortcuts for the mounted devices on the desktop?

Thanks

---

### Post by aJayRoo on 2007-06-16
yeah you can edit the setting for that using gconf-editor (not as root) by typing
```
gconf-editor
```
into a terminal or the run application (alt-f2) screen.
Then using the side panel navigate to apps->nautilus->desktop and deselect the volumes visible option. Hope that helps.

---

### Post by tL0z on 2007-06-17
Thanks! ;)

---

### Post by miLl3niUm on 2007-06-17
Thanks! I also needed that.

---

### Post by Brando569 on 2008-01-10
sorry to dig up an old topic but how can i do this in kde?

---

### Post by aJayRoo on 2008-01-10
From memory:
Right click the desktop -> Configure Desktop...
Click the Behaviour icon
Select the Device Icons tab
Choose what you want to be shown on the desktop.

---

