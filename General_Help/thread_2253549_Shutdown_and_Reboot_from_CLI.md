---
title: "Shutdown and Reboot from CLI"
date: 2014-11-20
forum: General Help
---

### Post by lingpanda on 2014-11-20
Hello,

    I've used both ```
shutdown -r now
``` and ```
reboot
``` to reboot a server from command line. I also use ```
shutdown now -h
``` to shutdown the server. Is there a difference to reboot and if so what? Any other way to shutdown a server? Thanks.

---

### Post by nerdtron on 2014-11-20
I don't see any difference as I have been using poweroff and reboot for servers now.
From the man page, the poweroff, reboot and halt commands, without arguments will simply call the shutdown command.

> 
DESCRIPTION
       These programs allow a system administrator to reboot, halt or poweroff the system.

       When  called with --force or when in runlevel 0 or 6, this tool invokes the reboot(2) system call itself (with REBOOTCOMMAND argument passed) and directly reboots the system.  Otherwise this sim&#8208;
       ply invokes the shutdown(8) tool with the appropriate arguments without passing REBOOTCOMMAND argument.

       Before invoking reboot(2), a shutdown time record is first written to /var/log/wtmp



---

