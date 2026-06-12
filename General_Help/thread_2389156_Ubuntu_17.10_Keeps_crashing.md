---
title: "Ubuntu 17.10 Keeps crashing"
date: 2018-04-12
forum: General Help
---

### Post by repsaks on 2018-04-12
Hey, recently Ubuntu (or GNOEM?) started crashing. It didn't happen very often at first but now it happens daily.

The screen turns black with a bunch of ```
@^@^@^@^
``` printed and then goes straight to the login screen (no reboot).

I've tried changing to an earlier kernel and reinstalling GNOME.

Any suggestions on how I can go about trying to diagnose the problem?

---

### Post by dino99 on 2018-04-12
glance at 'journalctl -b' warnings (white highlighted lines) and errors (red lines)
/var/crash/ is the place for crash file you can report via 'ubuntu-bug thecrashfilename' or simple right click on the file and select 'report with'

---

### Post by repsaks on 2018-04-13
Thank you, I will take a look next time it happens!

I gave upgrading to 18.04 a shot, no crash since then.

I'll update the thread in a day or two.

---

### Post by repsaks on 2018-04-15
Looks like upgrading to 18.04 solved the problem.

---

