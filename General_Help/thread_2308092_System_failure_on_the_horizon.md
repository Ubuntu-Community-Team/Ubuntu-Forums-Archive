---
title: "System failure on the horizon?"
date: 2015-12-30
forum: General Help
---

### Post by Superdude_123 on 2015-12-30
I'm hoping you guys can help me out. I've been toying with my old Debian server and lately, I've had issues when i load things in GNOME. So thinking that GNOME was the problem, I did an distribution upgrade + auto remove of some stuff, then purged my GNOME to bring my system to a fresh start. Now the good news is that my MATE isn't problematic, however, if I load programs in while using X-org, it seems to hang my system. For a few minutes, I still have SSH control, but then the system becomes completely unresponsive. Lately, while I still had SSH control, I decided to kill X-org's PID hoping that would solve the problem, and then resorted to also trying the following with the following out come. I'm wondering if any of you can give me a clue on what's going on here in my system:

fobar@DebianServer:~$ sudo service lightdm restart

Message from syslogd@DebianServer at Dec 30 22:23:10 ...
 kernel:[ 3648.883001] CPU: 0 PID: 1965 Comm: Xorg Not tainted 3.16.0-4-686-pae #1 Debian 3.16.7-ckt11-1+deb8u3

Message from syslogd@DebianServer at Dec 30 22:23:10 ...
 kernel:[ 3648.883007] Hardware name: Dell Computer Corporation OptiPlex GX400               /OptiPlex GX400               , BIOS A05 10/05/2001

Message from syslogd@DebianServer at Dec 30 22:23:10 ...
 kernel:[ 3648.883012] task: f4431560 ti: f4636000 task.ti: f4636000

Message from syslogd@DebianServer at Dec 30 22:23:10 ...
 kernel:[ 3648.883047] Stack:

Message from syslogd@DebianServer at Dec 30 22:23:10 ...
 kernel:[ 3648.883084] Call Trace:

Message from syslogd@DebianServer at Dec 30 22:23:10 ...
 kernel:[ 3648.883289] Code: 00 55 89 e5 3e 8d 74 26 00 31 c0 5d c3 8d 74 26 00 55 89 e5 3e 8d 74 26 00 8b 40 18 85 c0 74 0e 8b 80 94 00 00 00 8b 50 14 31 c0 <89> 42 40 5d c3 ba 00 90 27 f8 b8 80 90 27 f8 e9 f2 b3 11 00 0f

Message from syslogd@DebianServer at Dec 30 22:23:10 ...
 kernel:[ 3648.883354] EIP: [<f82770ea>] r128_driver_irq_uninstall+0x1a/0x1f [r128] SS:ESP 0068:f4637d40
Write failed: Broken pipe <= At this point my SSH connection dropped

---

