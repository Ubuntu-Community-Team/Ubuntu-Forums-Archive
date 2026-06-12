---
title: "Activity bar - power off command terminates all open applications / programs"
date: 2024-04-16
forum: General Help
---

### Post by pnuke on 2024-04-16
Hello, 

Ubuntu 22.04 minimal installation.

when I use the power-off command in the activity bar in the top right corner of the screen, everything is instantly killed and applications like Chrome will try to send a crash report upon next startup. 
Why is there no graceful shutdown (SIGTERM) ?

Is that something that needs to be configured?

---

### Post by ajgreeny on 2024-04-16
You simply need to shutdown all open applications before shutting down the operating system!

As far as I remember this has always been the case in all OSs but I have been using Linux only for almost 20 years now so can't really remember what happened in Windows-XP, my previous OS.
Maybe things are different now by default in Windows as the supported versions of that both use a hibernation version and not a complete shutdown but I've never really used either of those on a machine of my own so I could easily be wrong.

---

### Post by pnuke on 2024-04-23
by definition, poweroff sends a SIGTERM to all running processes and they stop gracefully. And the system is supposed to wait for that to happen. So in EVERY major OS you should be able to initiate a halt/shutdown/poweroff command without closing any program before. Of course you should have saved all open work. But nowadays with autosave features this is also no problem anymore. 

Windows is doing it _forever_. its always waiting for all programs to end gracefully. MacOS is doing the same, waiting for all programs to exit before proceeding with the shutdown.

But I will also report to Google maybe its just a bug of Chrome to not react to SIGTERM.

---

### Post by Impavidus on 2024-04-23
When you shutdown, all processes get the SIGTERM signal. This tells them to terminate. If the process doesn't terminate, it will get the SIGKILL signal a short time later, instantly terminating the process.

Many processes don't care about SIGTERM. The default effect of SIGTERM is identical to that of SIGKILL, and indeed many programmes simply terminate at once. Some might decide to ignore SIGTERM, which isn't any better, as they will get SIGKILL. Some processes handle SIGTERM and use it for some clean shutdown. But they can't ask the user whether to save the current work, overwriting existing files. Some applications might do this without asking, others don't save the user's files, but do create some recovery file that allows them to restore the unsaved changes the next time the application is started. Basically, the application may perform a clean shutdown, whilst recording that it was an emergency shutdown, requiring some recovery the next time the application is started.

---

