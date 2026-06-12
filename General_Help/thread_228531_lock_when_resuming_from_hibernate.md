---
title: "lock when resuming from hibernate"
date: 2006-08-03
forum: General Help
---

### Post by abandoned_hussam on 2006-08-03
when I press the power button, the logout dialog menu appears but then and without me touching anything, the computer successfully hibernates.
Now when I resume from hibernation, the same logout dialog menu appears. I click cancel and find myself in my desktop again. My question is how to I make it lock the desktop when I hibernate?

---

### Post by tagbre on 2006-08-03
check the file /etc/default/acpi-support
there's an option to lock the screen on resume...it's supposed to be activated by default.

---

### Post by abandoned_hussam on 2006-08-03
Ok, I reinstalled thew packages acpid acpi and acpi-support and now when I manually hibernate from gnome-power-manager, it does indeed lock on resume.
But now, pressing the power botton shuts down the computer instead of hibernating. How do i make the power button hibernate?

---

