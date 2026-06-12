---
title: "Can't Correct for Daylight Savings"
date: 2008-03-25
forum: General Help
---

### Post by tnunamak on 2008-03-25
Since the time jumped forward an hour from daylight savings, my computer clock has remained unchanged. If I change it ahead manually, when I reboot it resets itself to the old time. I've changed the clock in the bios with no effect in Ubuntu. If I change my timezone one ahead in order to compensate, it changes it to two hours ahead... so apparently my computer thinks daylight savings has occurred in every time zone but central.

Any help?

---

### Post by Iowan on 2008-03-25
Mine works - also in Central. Have you tried syncing to timeserver?

---

### Post by tnunamak on 2008-03-25
I've synced with a few of the different servers listed, and it seems happy enough to do so, despite the incorrect time which I still get.

---

### Post by Iowan on 2008-03-25
You're in America/Chicago timezone?  I presume you got the update a few weeks ago to patch DST?

---

### Post by tnunamak on 2008-03-26
Ok... so I overlooked the fact that Canada/Mexico didn't make the DST change, so CST in Canada/Mexico, as well as other countries, is different than in the US. That should have been obvious although it is very counter-intuitive that if I travel directly north/south, within the same nominal time zone, the time changes. I didn't think to make sure that my time zone was actually selected to be in the USA...

Anyway... thanks for the help.

---

