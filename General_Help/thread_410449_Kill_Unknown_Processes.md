---
title: "Kill Unknown Processes"
date: 2007-04-15
forum: General Help
---

### Post by zukakog on 2007-04-15
I've got a a CPU usage monitor applet that spikes every few seconds.  I opened up ksysguard and saw that it was an instance of sh initiated by root.  It just appears for a second and disappears, but it makes my whole system lag when it happens.  How can I figure out what this process is so I can kill it or renice it?

---

### Post by mhansen on 2007-04-15
sh is the Bourne shell.

You're seeing sh come up, as root, with no arguments?  That is, you see something like a root owned /bin/sh process with no options following it?

If so, I can think of no good reason why this should be happening.  Also, if that's the case, what version of Ubuntu are you running and which ports are open?  Do you keep your system updated regularly, espcially for security updates?

Otherwise, please post the arguments that follow the command.



Regards,
Mike

---

### Post by zukakog on 2007-04-21
Before, I didn't see the column that had the arguments for the processes because it was out of the window.  I had to move the column next to the process name and I could see it fine.  I opened ksysguard and checked again, but sh didn't appear like it did before.  I did, however, see an instance of adept_updater that kept spiking.  I killed it and haven't had a problem with it since.  Thanks for your help!

---

