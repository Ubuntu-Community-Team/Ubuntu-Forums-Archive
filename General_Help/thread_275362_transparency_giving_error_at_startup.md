---
title: "transparency giving error at startup"
date: 2006-10-11
forum: General Help
---

### Post by TommyMann on 2006-10-11
Composite extension not found
You must use XOrg &#8805; 6.8 for translucency and shadows to work.
Additionally, you need to add a new section to your X config file:
Section "Extensions"
Option "Composite" "Enable"
EndSection

I recently customized my desktop using crystal to create transparency. Everything seems to be working fine. I have transparency and what have you. How can I make this error message go away, or is there something secretly wrong with my computer?

-Tommy

---

