---
title: "Shortcuts of wine gone from &quot;Applications&quot; Panel"
date: 2008-05-07
forum: General Help
---

### Post by godlike_panos on 2008-05-07
Initially I installed wine though add/remove and a few shortcuts were created in Applications panel as result of the installation. Then I unstalled the wine but the shortcuts were still in Applications so I removed them myself from "edit menus". Now I installed wine again but no shortcuts were created at all. How can I reset this so I can have the wine shortcuts again?

---

### Post by Achtung on 2008-05-07
Open /Home/<user>/.config/menus/applications.menu
Do a search for "wine".
Erase the </deleted> tag for every wine entry.
Save.

---

### Post by godlike_panos on 2008-05-07
> **Achtung said:**
> Open /Home/<user>/.config/menus/applications.menu
Do a search for "wine".
Erase the </deleted> tag for every wine entry.
Save.
Thanks friend. That did it

---

