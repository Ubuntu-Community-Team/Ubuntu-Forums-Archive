---
title: "Help me learn about cron"
date: 2007-11-01
forum: General Help
---

### Post by TeeAhr1 on 2007-11-01
I want to schedule a daily task, so that my calendar (korganizer), which is always running in the system tray, comes to the foreground at 7:00 every morning, so it's the first thing I see when I turn my monitor on.  I tried to add "kontact --module korganizer" to kcron, but that didn't work.  Is there a flag I need to set to bring a task to the foreground?  Thx...

-pete

---

### Post by Green_Star on 2007-11-01
if korganizer is already running in yor system tray, then what command do you issue to get it to foreground? (I am not asking you about how you do it with your mouse, i want to know is there any terminal command can do that), i believe it will work if you run that command using cron job.

so it is not about cron, but about korganizer, i never used korganizer so i can not help you in finding such kind of commands to get it into foreground.

good luck

---

### Post by TeeAhr1 on 2007-11-01
Looking at the man page, these two seem like possible candidates:

       --display <displayname>
              Use the X-server display &#8216;displayname&#8217;.

       --session <sessionId>
              Restore the application for the given &#8216;sessionId&#8217;.

But I'm not sure what those are asking for... :???:

EDIT: I just looked at the log for this morning, and cron says it ran it, but I got nothin'.

---

