---
title: "Ubuntu Dapper crashes at startup"
date: 2007-05-21
forum: General Help
---

### Post by modex on 2007-05-21
Hello everyone...I'm facing a serious problem (at least for me) with my Ubuntu 6.06.I have done some searching but can't find something helpful.I hope this is the right place.
This is what happend. Lasta night when tried to shutdown the system, while shuting down my Ubuntu hangs up. It didn't respond to Alt-Ctrl-Del  so I reset the pc.
This morning when I tried to boot it, in the boot screen where it shows what's been mounted, It mounts the filesystem then  freezes for a couple of seconds and then I get this error:

[B]/etc/init.d/rc: line 111: /etc/default/rcS: Not a directory
*INIT: Entering runlevel 2
/etc/init.d/rc: line 111: /etc/default/rcS: Not a directory[/B]

I tried to boot in recovery mode but the same thing happens.
I managed to read the init.d/rc file and these are lines 111 and 112 where the error occur:

[B] . /etc/default/rcS
export VERBOSE[/B]

I then tried to reinstall GRUB in case the initrd file in the menul.lst was corrupt but once more nothing happens!!!
PLZ I'm desperate. I can't "afford" reinstalling it from scratch.What can I do

Thnx in advance.

---

