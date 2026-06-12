---
title: "Will not load after update to Hardy"
date: 2008-04-25
forum: General Help
---

### Post by romis on 2008-04-25
Once the update to Hardy finished and I restarted Ubuntu got to the loading screen, where the bar bounced back and forth (which seems new, it used to fill up) and then took me to a commandline. So I hit CTRL+ALT+F1 the next time I restarted to see if it would tell me anything useful:

> 
[96.088193] ata1.00: revalidation failed (errno=-5)
[131.231050] ata1.00: revalidation failed (errno=-5)

checkroot - bootarg cat/proc/cmdline

ALERT! /dev/disk/by-uuid/c55541f8-6ff0-4b68-8da3-7566dff56275 does not exist. Dropping to a shell!



I'm in 2nd newest kernel right now, which isn't recognizing my NVidia restricted driver, and telling it do and restarting doesn't seem to work.

Does anyone have any ideas as to what it might be?

---

