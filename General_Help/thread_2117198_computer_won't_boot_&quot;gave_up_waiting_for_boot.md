---
title: "computer won't boot &quot;gave up waiting for boot device&quot;"
date: 2013-02-17
forum: General Help
---

### Post by blackdalek on 2013-02-17
Upgraded memory in old Acer Aspire PC from 512Mb to 2Gb.

Now Ubuntu won't boot.

After "Starting Up..." it says
udevd [81] worker [143] terminated by signal 6 (Aborted)
udevd [81] worker [143] failed while handling '/devices/LNXSYSTM:00/device:00/PNPA03:00/device:0c'

Gave up waiting for root device

....then some more stuff then a busybox initramfs prompt.

How do I fix this?

---

### Post by blackdalek on 2013-02-17
Additional info:

This is running Ubuntu 11.10

RAM is in 2 x 1Gb modules.

Each 1Gb module works fine if installed singularly by itself in either of the two RAM slots. So both mobo slots and RAM is fine.

PC fails to boot Ubuntu if both modules are installed together.

Both modules are identical.

Is there some kind of bug in Ubuntu 11.10 which prevents more than 1Gb of RAM being installed?

---

### Post by Zteam on 2013-02-17
Sounds like your system has memory problems.

Try too boot up Memtest86+ from a livecd / liveusb and let it run over the night and see if you get any errors.

---

### Post by blackdalek on 2013-02-19
follow-up:

Went ahead and upgraded to 12.04 then on to 12.10 (had to take one of the 1Gb modules out)

Put the module back in to bring it back to 2Gb.
Now no errors - Got a new problem instead.
Now it gets to the purple tinted blank screen just before the logon screen, then the monitor turns off and on and PC reboots back to POST. This happens for infinite loop.

Next I will try to run memtest from a live CD when I get chance.
I will also look again at the BIOS version to see if there are any updates for it, but it seems unlikely this will be the case as I remember I only updated the BIOS on that machine about 2 years ago.... and it's not like a new version comes out every year. :(

---

