---
title: "Diagnosing why my machine becomes so unreponsive I have to reset (Feisty)"
date: 2007-05-13
forum: General Help
---

### Post by monstermunch on 2007-05-13
Hi,

Today I was browsing the internet and writing emails, something I do all the time on Fiesty with no problems, and my session hanged. The mouse cursor would not move, none of my applications would response, I couldn't switch to a console with ALT-CTRL-F1 or reset my X-server. My hard drive was reading or writing constantly during this time which is unusual, also because I have 2Gb of RAM so never need to use swap. I tried ALT-TAB (switch application) at one point, after about two minutes the switch actually happened but my applications were still completely unresponsive. I tried the power button, which usually makes the machine shut down, but that didn't work either. My only option was a hard reset.

This has happened twice now. How can I diagnose this? I don't know where to look.

I was going to report this on launchpad but thought I would get prompter help here.

Thanks!

---

### Post by kebes on 2007-05-13
Go into the directory "/var/log" and see what messages were being generated at the time the problem occurred.

Also, you could keep a terminal open with "top" running (which shows the processes that are active at any given moment)... then if the problem occurs again, take a look at top and see if any process is running out of control.

---

### Post by strixy on 2007-05-13
Are you downloading torrents with Ktorrent?

---

