---
title: "ACPI power off still works when screen is locked or with unsaved data"
date: 2005-06-09
forum: General Help
---

### Post by 23meg on 2005-06-09
the subject sums up the point i want to bring up; when i hit the power button when the screen is locked, the computer shuts down without question. isn't this a security flaw, since it's not clear who's hitting the power button? you leave your computer with (say) unsaved sensitive work, someone hits the power button and all is lost when you're back.. is there something wrong with my ACPI configuration, or is this the way it's supposed to be? is there some underlying obstacle preventing this from being properly implemented?

i've noticed similar behaviour with apps that have unsaved data; they'll quit right away. this perhaps means that ACPI can't communicate with X and wait for it to confirm the shutdown. in Windows, for example, both behaviours are different; you can't shutdown with a locked screen, and apps ask if you wan't to save your work before shutdown.

maybe it all has to do with the fact that ACPI is still a work in progress in linux?

---

### Post by 23meg on 2005-06-13
is this the case with other operating systems as well? how about osx, for example? would it be possible to tweak the ACPI scripts to detect if the computer is locked and behave accordingly?

---

### Post by 23meg on 2005-10-02
this is still the same in Breezy. time to file another bug report i guess.

---

### Post by bdash on 2005-10-11
What if someone unplug the power cable? It is not safe to let anyone have a physical access to your computer...

---

### Post by 23meg on 2005-10-26
That's correct but you can't prevent the possible harm done by someone unplugging the power cable via software, whereas in the case of the power button you can.

---

