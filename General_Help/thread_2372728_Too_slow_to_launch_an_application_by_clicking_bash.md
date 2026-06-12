---
title: "Too slow to launch an application by clicking bash script on Desktop"
date: 2017-09-28
forum: General Help
---

### Post by jimhce on 2017-09-28
Hi,

I am running Ubuntu 14.04.5, I have a couple of bash scripts to launch application on Desktop, but that launching process seems very slow and there is no sign if the launching is in process or not. Too often, I made seveal clicking resulting launching 4 -5 same applications such as VLC players or Chromium browsers. Is there anyway to see some signs, for example, a spin icon on screen?

Thank you

---

### Post by TheFu on 2017-09-28
Yes, there is a way. Write a script wrapper that starts up whatever visual queues you want BEFORE launching the real program - save the PID, so you can kill that program once the real program shows up in the process table for 5 seconds (or whatever value you like).

This is a fairly basic script.  The ABSG should have examples.

OTOH, a slow launch means something is wrong with the computer.  Might be useful to try to solve that.  I'd start by looking at what is using the CPU and RAM on the system.  Also, make certain the storage is working well - no errors, not full or near full.

---

### Post by mc4man on 2017-09-28
> **jimhce said:**
> Hi,

I am running Ubuntu 14.04.5, I have a couple of bash scripts to launch application on Desktop, but that launching process seems very slow and there is no sign if the launching is in process or not. Too often, I made seveal clicking resulting launching 4 -5 same applications such as VLC players or Chromium browsers. Is there anyway to see some signs, for example, a spin icon on screen?

Thank you
Post the contents of your launcher (.desktop
Probably you can just add this line
```
StartupNotify=true
```

---

