---
title: "Freeze sonn as X Loads"
date: 2005-06-07
forum: General Help
---

### Post by Kaska on 2005-06-07
I just downloaded the Live CD, and soon as X loaded, it froze.  Did this twice.  I finnaly figured out what it was.  The startup sound was trying to be played and it couldn't be played so it just froze hard.  I have a Dell 8200, and was pretty sure it was related to this bug: [https://bugzilla.ubuntu.com/show_bug.cgi?id=1254](https://bugzilla.ubuntu.com/show_bug.cgi?id=1254) and that is why it didn't work.  I tried a few things, and finnaly at boot i used: "live acpi_irq_isa=7" and that made it work perfectly fine.  Bugzilla shows this bug as fixed, but under the live cd it certainly isn't.  I'm not sure if I should open another buzilla bug about this or not.

---

