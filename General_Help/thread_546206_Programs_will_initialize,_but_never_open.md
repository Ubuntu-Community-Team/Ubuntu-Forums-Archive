---
title: "Programs will initialize, but never open"
date: 2007-09-08
forum: General Help
---

### Post by onetb on 2007-09-08
This issue has only come up three times, and it eventually goes away, but it is quite inconvienient.

I will try start a program (any program) and the bottom panel will show it as if the program is open, but it never does.  Shortly thereafter, it will disappear from the bottom panel.  There is not error code.  Restarts do not fix the issue.  All that has fixed it has been to shut the system down and wait.  The first time, it took very little time to start working again.  The second time, it took about two hours before the shut-down/restart resolved the issue.  This time, about a half an hour.  Anyone have any ideas about what might be causing this?

Just a bit of additional info, I have been having other problems associated with broken or weak leads on the MoBo, such as lines of color on the monitor and several buttons only working sporadically.

---

### Post by gashcrumb on 2007-09-08
When this starts happening, open up a terminal and run:

ps -deaf | grep defunct

check and see if the program you tried to run shows up in the resulting list.  Another thing to check is run "top" and see what the load average is and check the CPU usage.

However, it could very well be that you've got some serious hardware issues.  When you start a program GNOME creates an entry in the taskbar as a notification that helps indicate that you've started the program.  It could very well be that the program is silently crashing, and the notification eventually times out, which is when the entry for the program disappears from your task bar.

You might want to go into your computers BIOS and set it to do a full RAM test during POST just to double-check that some of your RAM hasn't been damaged.  Sounds though like you might need to consider replacing that motherboard.

---

### Post by onetb on 2007-09-08
I believe these are hardware issues.  The laptop that is having the issue is a Compaq Presario V5305.  I have had it for about 10 months.  My last Compaq/HP product, an HP Pavillion zv6131, had mobo issues at about 10 months as well.

Should all be covered by warranty, but it is b.s. that each of these have had similar issues in about the same time.

HP/Compaq, say goodbye to my patronage!

---

