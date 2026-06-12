---
title: "Is it possible to reduce KERNEL boot time?"
date: 2005-10-22
forum: General Help
---

### Post by temcat on 2005-10-22
Using InitNG I was able to reduce total boot time by about 20 seconds (see my HOWTO at [http://ubuntuforums.org/showthread.php?t=80423)](http://ubuntuforums.org/showthread.php?t=80423)). But I notice that a significant amount of time at boot (about 15 seconds) is spent in kernel - even before InitNG launches. Is it possible to cut kernel boot time, too? Any help is appreciated.

---

### Post by Ace2016 on 2007-05-27
What i did was when i was running the generic kernel i ran lsmod and coppied that to a text file as a referance point, then i compiled the modules that i thought should be compiled in, there were stuff like backlight in lsmod that were loaded even though my system does not support it so i didn't compile those, and i compiled in all the filesystem types i use, then i removed support for all the stuff that ubuntu staticly compiled in but my system doesn't have. Then i installed the kernel. The next step was to remove all the stuff ubuntu was adding to the initrd file, it had lots of modules my system never uses, so i got rid of them, and i also added the nvidia.ko from /lib/modules/2.6.21-2016/kernel/drivers/video/nvidia.ko. That reduced the amount of stuff that has to be read from the hard disk before the system can boot, so i guess this might speed stuff up on slower drives. 

For some strange reason the initrd was built missed stuff like modules.dep, which i fixed by coppying it from /lib/modules/2.6.21-2016/modules.dep into the initrd.

Good luck and tell me if it has any impact on the speed

---

