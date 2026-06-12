---
title: "Restart a crashed application"
date: 2007-12-01
forum: General Help
---

### Post by HokeyFry on 2007-12-01
Question. Is it possible via some sort of script or something to have a program that crashes restart itself? For example, if Exaile crashes due to one of my Gstreamer plugins (I'm assuming that is what causes it), how do I have the computer run a script that tells Exaile to reopen and play something at random? Is this even possible?

---

### Post by navaburo on 2007-12-01
If the application closes when it crashes, then it is easy to restart it. You can try the following:

Open up a terminal.

Run ps and note the PID of that terminal's bash process (so you can kill it later when you want to stop the script).

To repeat a command, run something like this, replacing date with the command of your choice:

```

while true; do date; done

```

press Control-C to stop it.

Just make sure that you DO NOT replace the ; after date with a & or bash will not wait for the program to close before running it again, and you will get an unpleasant surprise.


Good luck (and do submit a bug report for reproducible crashes).

---

### Post by SunnyRabbiera on 2007-12-01
I wish there were a universal way to restore apps, on any os as there isnt one...
but if it were implimented it could limit software freedom

---

### Post by navaburo on 2007-12-01
you could write a script using the above as a starting point so that in the end it would be like:

```
zombie app
```

where zombie is the script and app is the application you want to rise from the dead each time it crashes.

---

