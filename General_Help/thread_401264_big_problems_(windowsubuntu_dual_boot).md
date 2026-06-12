---
title: "big problems (windows/ubuntu dual boot)"
date: 2007-04-04
forum: General Help
---

### Post by lucas9000 on 2007-04-04
i came home this morning to find my computer monitor had gone black but the mouse cursor still showed up. i could move the cursor around but couldn't do anything (ctrl+alt+del didn't even do anything). i had left my computer on (as i usually do) overnight. (btw i was in win xp pro, even though my system is dual boot with ubuntu edgy 386.) so, i rebooted.

on reboot the bios screen came up as normal, and then the windows screen that shows xp booting (with that little animated progress bar thingy). but then it went to a screen that had a bunch of error messages that were something like "init..." (i didn't have time to write it down). i rebooted again and nada. so, i grabbed my ubuntu live cd to boot from that.

when i tried to boot the live cd in "safe graphics mode", i got this error screen:

> *Activating swap... [fail]
mount: Function not implemented
*Checking file systems...
fsck: error while loading shared libraries: /lib/libdevmapper.so.1.02: invalid ELF header
fsck died with exit status 127
[fail]
*File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
*A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
/bin/sh: can't open sulogin

*Attempt to start maintenance shell failed.
Continuing with system boot in 5 seconds.
init: rc-default process (3740) terminated with status 2

and it just hung there and didn't reboot or anything.

i then tried booting windows in safe mode, which gave me a bunch of error messages that said something like "multi(0)disk(0)rdisk(0)partition(1)..." again i didn't have time to write it all down because it rebooted on it's own, then after that reboot i got a bsod, it rebooted again on its own, and finally i just cut the power to the thing.

for probably a month prior i've had problems where my computer won't simply shut down. if i tell it to shut down, it gets to the end of the process and then just reboots on its own. if i cut the power by switching off the power supply, and then turn it on, it takes a while to turn on. i'll press the power button, then after a few seconds it will kind of "rev up" (i can hear the fans starting and stopping, then starting and stopping again, and see the lights from the mobo/etc turning on and off), until it finally just boots up.

my guess is the most recent problem is with the file system on my hard drive, but even if that were true shouldn't i still be able to boot from the ubuntu live cd? what is going on here? any help is very greatly appreciated!

---

### Post by acormack on 2007-04-04
I agree with your diagnosis that the harddisk is unwell - but that shouldn't stop the live cd booting.  

I am unclear if you actually tried booting ubuntu from the hard disk.

Did you try booting the live cd in normal (non-safe)  graphics mode?

Is it possible the cd is dirty?  



Is it the same version as the one you originally installed with?

---

### Post by lucas9000 on 2007-04-04
> **acormack said:**
> I agree with your diagnosis that the harddisk is unwell - but that shouldn't stop the live cd booting.  

I am unclear if you actually tried booting ubuntu from the hard disk.

no i did not because when i most recently installed windows (on a separate partition than ubuntu) it somehow got rid of grub so i could only boot into windows from the hard drive.

> Did you try booting the live cd in normal (non-safe)  graphics mode?

yes, i tried that before i tried safe mode, and it didn't work either (which prompted me to try safe mode).

> Is it possible the cd is dirty?

didn't look like it.  i can check again more closely when i get home from work, but i doubt this is the problem

> Is it the same version as the one you originally installed with?

yes.  i originally installed ubuntu from the exact same dvd.

---

