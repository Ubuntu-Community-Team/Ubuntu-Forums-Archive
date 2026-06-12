---
title: "[K]Ubuntu failure to shut down"
date: 2008-02-17
forum: General Help
---

### Post by xenomorph99 on 2008-02-17
Hi,

Everything has been working well (in terms of shutting down, at least) since I had 7.10 installed (i.e. since it came out) but now the machine will not shut down properly.

It seems to have started since I had some trouble with Truecrypt in that the machine would hang when copying large files to a TC volume. I've since cured that by adding the sync option in TC but now I'm encountering this shutdown issue.

Previously, it would hang when reporting shutting down the Samba daemon but I removed Samba and now it hangs just after reporting shutting down the "ConsoleKit daemon"

Any ideas on how to fix this or so I have to reinstall Kubuntu again?

EDIT:
This is what is in the /var/syslog file if it helps:

Feb 17 18:48:38 ka-desktop init: tty4 main process (4774) killed by TERM signal
Feb 17 18:48:38 ka-desktop init: tty5 main process (4775) killed by TERM signal
Feb 17 18:48:38 ka-desktop init: tty3 main process (4779) killed by TERM signal
Feb 17 18:48:38 ka-desktop init: tty1 main process (4781) killed by TERM signal
Feb 17 18:48:38 ka-desktop init: tty6 main process (4782) killed by TERM signal
Feb 17 18:48:38 ka-desktop init: tty2 main process (4777) killed by TERM signal
Feb 17 18:48:38 ka-desktop init: rc2 main process (4776) killed by TERM signal
Feb 17 18:49:51 ka-desktop syslogd 1.4.1#21ubuntu3: restart.
Feb 17 18:49:51 ka-desktop kernel: Inspecting /boot/System.map-2.6.22-14-generic
Feb 17 18:49:51 ka-desktop kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Feb 17 18:49:51 ka-desktop kernel: Symbols match kernel version 2.6.22.
Feb 17 18:49:51 ka-desktop kernel: No module symbols loaded - kernel modules not enabled. 
Feb 17 18:49:51 ka-desktop kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Feb 17 18:49:51 ka-desktop kernel: [    0.000000] BIOS-provided physical RAM map:

/end

Ta,
K

---

### Post by xenomorph99 on 2008-02-17
I've also tried booting from an Xubuntu Live CD and running fsck etc on all partitions in case something got screwed when I had to power off after Truecrypt hung.

No result - everything was clean.

Ta,
K

---

