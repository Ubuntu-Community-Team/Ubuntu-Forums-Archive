---
title: "live CD failed - mounting snapshot - nodule ext2 not found -  could not boot Windows"
date: 2005-05-18
forum: General Help
---

### Post by John Macdonald on 2005-05-18
When I booted from the 5.04 Live CD, it failed during the step "Enter preinstalled session".

I looked in /var/log/syslog and the last few lines were (copied back from paper, so there may be typos):

...: casper: Mounting snapshot
...: casper: Scanning for swap devices
...: casper: Using swap devices:
...: main-menu[3144]: (process: 15440): FATAL: Module ext2 not found
...: main-menu[3144]: (process: 15440): cp:
...: main-menu[3144]: (process: 15440): unable to open `/target//etc/network/interfaces'
...: main-menu[3144]: (process: 15440): : Input/output error
...: main-menu[3144]: WARNING **: Configuring 'casper-udeb' failed with error code 1
...: main-menu[3144]: WARNING **: Menu item 'casper-udeb' failed.

I didn't see anything earlier in syslog that looked obviously wrong (but I'm just going on Unix/SuSE experience, this is my first look at details of Ubuntu).  There were a couple of minor items that I don't think were problems:

- a number of times during the earlier steps there was an informational item about missing modules: ide-mod, ide-probe-mod, ide-detect, and ide-floppy

- when scanning hardware, it found my ethernet interface, an Intel PRO/100 VE, and stated that eepro100 was blacklisted and e100 was loaded successfully, which sounds like it knew what it was doing

Finally, after I gave up and ejected the CD and rebooted, the system would not reboot (the message was something like "remove the disk or...; press any key to retry").  I had to use the Windows recovery disk to boot.

My system is a Compaq Presario 6000.  It has only one disk (I'll add a second when I actually install).

---

