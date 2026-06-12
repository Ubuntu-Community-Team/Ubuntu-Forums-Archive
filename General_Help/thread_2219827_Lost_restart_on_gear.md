---
title: "Lost restart on gear"
date: 2014-04-25
forum: General Help
---

### Post by DigiAngel on 2014-04-25
Topic says it...not a big deal, but eh...click the gear on the upper right hand and I get shutdown, but not restart.  This happened after I upgraded to 14.04.

---

### Post by deadflowr on 2014-04-25
When you click on shutdown and the shutdown window opens, is restart one of the two options?

---

### Post by DigiAngel on 2014-04-25
It is....again this is more cosmetic then anything else :)

---

### Post by mcduck on 2014-04-25
That's the correct way for 14.04, restart doesn't have a separate option in the menu and is only an option in the shutdown dialog.

---

### Post by deadflowr on 2014-04-25
> **mcduck said:**
> That's the correct way for 14.04, restart doesn't have a separate option in the menu and is only an option in the shutdown dialog.

I think it was set so that if either shutdown or restart were selected you ended up with the same shutdown dialog box, which has both, either way.
Probably decided they should cut down on the redundancy.

---

### Post by mcduck on 2014-04-25
Makes sense to me, no reason to have the same option presented to user twice.

By the way, the restart option will appear in the menu automatically if you disable the shutdown confirmation dialog (I'm not sure if the option is in any settings menu, but at least it's available in dconf at *com.canonical.indicator.session suppress-logout-restart-shutdown*)

---

### Post by DigiAngel on 2014-04-27
Thanks for the responses all.

---

