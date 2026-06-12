---
title: "Hang on boot (intermittent) - Running on Hyper-V"
date: 2024-05-23
forum: General Help
---

### Post by Just4Fun20 on 2024-05-23
Sorry to ask basic questions but I'm unsure where to look.  I need guidance on where to get information (log files??) on boot hang status.

I'm running Windows 10 with Hyper-V.  I've done this for at least 6 years.  My previous instance was a 20.04 VM which had been upgraded to 22.04.  For 24.04 I started from scratch and just built a new instance.  When it's running I'm not having any problems.  

When I shutdown (which isn't really that often) I do so by following the proper power off procedures.  No issues with the shutdown.

When the VM comes back up it's very hit or miss as to whether is will come up or not.  Sometimes it stops on the Hyper-V screen.  Sometimes it makes it to a point where it shows just an X.  When it hangs, I leave it be for up to 5 minutes, but it doesn't change.  Then, if it will take it, I issue an "action" - "shut down" from the Hyper-V bar.  If that doesn't work I'm forced to "action" - "turn off". Regardless, then I "start" the VM power up sequence again. It can take anywhere from 1- 8 tries to get the system to properly boot up.  

So, back to the original request.  Where can I find some kind of log on this?  Is it persistent through boot or do I need to try to SSH into the machine (if it's up that far) and look for something?  Perhaps I could enable some sort of logging?  

Thank you very much for any nudges in the right direction.  It's not a critical problem but it's a bit alarming when I'm on the 4 or 5 reboot and haven't got it running yet.

---

### Post by currentshaft on 2024-05-24
I would check /var/log/kern.log and syslog to see what's going on.

You can also edit the grub configuration to print debug output instead of a splash screen.

Lastly, Control+Alt+F1 through F7 will get you to a serial console if graphics aren't working.

Good luck my friend.

---

### Post by Just4Fun20 on 2024-05-24
Perfect.  Thank you very much.

---

