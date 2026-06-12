---
title: "searching iso file for installation"
date: 2007-10-01
forum: General Help
---

### Post by steve196 on 2007-10-01
(or something to that effect)
The installer after reboot fails to find the .iso (which is in d:\wubi\install) and gives me an option, to search the harddisks for it. This initially fails a few times, then i get to load some drivers (d: is /dev/hdc3, so no need for special drivers, normally ), then it finds an unrelated .iso file and insists on using that one.
How can i simply tell it where the file is, instead of having it done automagically wrong?
Thanks!

---

### Post by steve196 on 2007-10-04
Wow! I didn't think, that would be a difficult question.
Anyway, now the ubuntu refuses to even start, telling me that the install iso is not there, again giving me no chance, to tell it, where it is. It tells me to rerun the installer. Rerunning the installer produces not even an error message, just silently fails.

---

### Post by ago on 2007-10-04
If you abort the installation you have to uninstall wubi and reinstall. Simply rebooting will not work. When you uninstall the ISO you have downloaded is preserved.

The ISO should be in the wubi/install folder and its name is specified in menu.lst. Only certain ISOs are allowed.

---

