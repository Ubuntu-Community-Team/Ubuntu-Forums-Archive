---
title: "Computer freezes when running this command..."
date: 2007-08-12
forum: General Help
---

### Post by samjh on 2007-08-12
My computer (Ubuntu 7.04 Gnome) seems to freeze randomly, requiring a hard restart.  It doesn't happen often, but it happens every two or three days.  Today I decided to go back through the system logs to see what might be causing it, and noticed that this was the last message before freezing:

/USR/SBIN/CRON[6879]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

What is it?  I didn't actually run it myself, so I don't know if it's part of an automated script that is supposed to run behind the scenes, or what it actually does.

Why would this be causing the computer to freeze?

---

### Post by forbajato on 2007-08-12
From the man page for run-parts it looks like it runs all the executable files in a directory.  The --report option prints the names of any scripts that produce output either to stderr or stdout.  Then the command is telling run-parts to operate of the /etc/cron.hourly directory.  Is there anything in that directory that could be causing the freeze?

Another possibility is that for some reason the system is not changing to the root directory properly and hangs before it gets to the run-parts command (that is what the && means - finish the first command (cd to root) then do the next one).  Any ideas why this may be happening?

---

