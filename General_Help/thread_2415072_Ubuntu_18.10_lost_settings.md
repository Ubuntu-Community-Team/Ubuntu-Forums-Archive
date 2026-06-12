---
title: "Ubuntu 18.10 lost settings"
date: 2019-03-19
forum: General Help
---

### Post by jeffrey-dewit on 2019-03-19
I logged into Ubuntu for the first time in a few days and some programs have been removed from the sidebar and resetted to default settings.

Google Chrome was removed from sidebar and reset.
KeepassXC was reset.
GNOME System Monitor stayed in the sidebar but the icon has changed.
Firefox has some settings changed but others not.
In the terminal pressing tab no longer autocompletes commands.

These are the changes I have noticed so far don't know if there are others.
Rebooting doesn't reset them again but I wonder what caused this and whether it can happen again.

---

### Post by jdeca57 on 2019-03-19
How did you stop the system? Don't look at the few days you didn't use it but at the last time you did use it and what changes you made then and how you saved them. An orderly shutdown?

---

### Post by jeffrey-dewit on 2019-03-19
Nothing out of the ordinary as far as I can remember.

---

### Post by jdeca57 on 2019-03-19
> **jeffrey-dewit said:**
> Nothing out of the ordinary as far as I can remember.

OK, but when you reboot now changes are recorded. Chance is that something did happen but it wasn't something obvious, Just a guess.

---

### Post by oldfred on 2019-03-19
If you had a separate /home and system then does not find it, it creates a new blank /home folder in / with default settings.
So did you lose /home somehow?

Post these:
sudo parted -l
lsblk -f
cat /etc/fstab

---

### Post by jeffrey-dewit on 2019-03-22
I did have a seperate home drive. It died. I guess that explains that.

---

