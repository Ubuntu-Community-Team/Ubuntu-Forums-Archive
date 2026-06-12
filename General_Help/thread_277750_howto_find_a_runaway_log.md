---
title: "howto find a runaway log?"
date: 2006-10-15
forum: General Help
---

### Post by jimisdead on 2006-10-15
My harddrive space is disappearing at about 10Kb/s... i guess i have a runaway log file somewhere but I can't find it... after a restart my harddrive space is back to where it originally was, but after a while it starts disappearing again.

Does anyone know a good way of finding what files are being written to? what files are growing? something like that. thanks.

---

### Post by wieman01 on 2006-10-15
Most of the log-files are in this folder:
> cd /var/
That's something to begin with.

---

### Post by bobosity on 2006-10-15
I'm sure there is an easier way but this will work:

open two terminals and put:

sudo du -x --max-depth=1 / |sort -n

into both. Hit return on one. Wait a few minutes and hit return on the other. Compare the two lists. If you find that /var changed significantly just repeat with 

sudo du -x --max-depth=1 /var |sort -n

and keep drilling down

---

### Post by Dr. Nick on 2006-10-15
In the edgy version their will be a gui that shows where all the space is going which will help some. In the mean time I would just look at /var or use the log viewer somewhere in gnome to see the large files.

All your hardware work?

---

