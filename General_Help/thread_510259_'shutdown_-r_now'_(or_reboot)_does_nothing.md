---
title: "'shutdown -r now' (or reboot) does nothing?"
date: 2007-07-26
forum: General Help
---

### Post by oldtimer_3478 on 2007-07-26
I've been using Linux since slackware 1.0 (1993) and Unix in general since 1985.

In all that time, I cannot recall ever having 'shutdown -r now'  (or 'shutdown -i6 -g0 -y', reboot, or equivalent) not work.  Until now.

I have an Ubuntu 7.04 server install.  I type 'shutdown -r now' and it issues the warning "The system is going down for reboot NOW!" and then exits back to the shell.  That's it.  Nothing else happens.  The system stays up and no processes are killed.

'shutdown -h now' does work, but that doesn't do me any good when the server is 30 minutes away and I just want to reboot to install a new kernel.  I don't want to drive across town just to push the power button!

I suspect it has something to do with upstart, but I cannot be sure.  Since init is gone, this old timer is lost.

The server is a Dell 1550 and has the latest BIOS for that server.  I tried a couple things I found in other posts. I tried the 'acpi=force' kernel option, but that didn't work. I tried using 'apm power_off=1', but it couldn't find apm.ko. 

Any help would be appreciated!

Thanks!

---

