---
title: "automatic startx"
date: 2004-11-18
forum: General Help
---

### Post by Frescardo on 2004-11-18
How can I make it so that X is not started automatically? I would just change the runlevel in /etc/inittab but apparently ubuntu doesn't distinguish between the different levels as far as X goes.

Michael

---

### Post by ynef on 2004-11-18
The command that starts x (actually, it starts gdm) is in all of your runlevels -- which is a bit weird, perhaps, but still a choice that the Ubuntu team has probably thought about a lot. Anyway, to get rid of the automatic start for x, all you have to do is go to your favourite runlevel directory (if you boot into runlevel 2, which is the default, it's /etc/rc2.d/ ) and remove the symbolic link to gdm. It's the one that's named S99gdm, of course.

You have to do this as root, so the following commands will work for you:

sudo /bin/bash
cd /etc/rc2.d/
rm S99gdm
logout

Next time you restart (or change runlevel to the one you just edited, actually) x will not start automatically!

---

