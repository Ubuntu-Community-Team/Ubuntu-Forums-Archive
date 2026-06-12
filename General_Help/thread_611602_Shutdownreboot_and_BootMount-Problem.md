---
title: "Shutdown/reboot and Boot/Mount-Problem"
date: 2007-11-13
forum: General Help
---

### Post by Helmi on 2007-11-13
Hi,

i got two weird problems left with gutsy that i wanted to solve now:

- on boot some of my smbfs/cifs-shares don't get mounted. These are all on the same network machine. Others mount well. If i do 'sudo mount -a' after boot everything mounts without errors. I couldn't find anything in the logs.

- when trying to shutdown via the icon on the gnome desktop the desktop hangs (applications don't hang - for example pidgin windows still open if someone writes me) and i can't click anywhere - it takes about 2-5 minutes for the shutdown/reboot-panel to appear. That is on every try.

Any ideas?

Thanks!

---

### Post by JasonF on 2007-11-13
> **Helmi said:**
> Hi,

- when trying to shutdown via the icon on the gnome desktop the desktop hangs (applications don't hang - for example pidgin windows still open if someone writes me) and i can't click anywhere - it takes about 2-5 minutes for the shutdown/reboot-panel to appear. That is on every try.

Thanks!

Re-adding 'Power Manager' (command was gnome-power-manager if you deleted it instead of just disabling it) to my gnome session fixed this for me.

---

### Post by Helmi on 2007-11-13
indeed - seems like that fixes it ;) thanks. thought i could save some power while not needing energy management on my desktop pc ;)

thaaanks ;O

---

