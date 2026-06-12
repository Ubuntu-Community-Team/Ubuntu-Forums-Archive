---
title: "What effect does disconnecting power has on Ubuntu 12.04?"
date: 2014-08-06
forum: General Help
---

### Post by arroy_0209 on 2014-08-06
Since the mouse stopped working I tried to shutdown the computer with commands like sudo halt or shutdown now but in both cases complete shutdown was not successful. The computer hanged thrice this way (in fact I tried ctrl-alt-del which resulted in reboot) and I was forced to disconnect power to computer. What damages are likely due to this? How do I check and are there any steps to be taken? Thanks.

---

### Post by Bucky Ball on 2014-08-06
```
sudo shutdown -h now
```

Boot the machine and see if anything is amiss. Unpredictable what damage pulling the power cable out may cause. Likely not much. Check your drives and see if the data is still intact. Too many variables, but hard drives would be the first to look at. ;)

Good luck.

---

### Post by JKyleOKC on 2014-08-06
Bucky Ball is correct, but I can tell you that simply rebooting and seeing if it comes up isn't really enough. You need to run a disk check, in addition, to determine if any individual files have been damaged.

Current journaling file systems such as EXT4 are pretty resiliant and often tolerate unexpected shutdown with no harm, but since all versions of Linux use some type of disk buffering in memory to speed things up, there's always the chance that such a shutdown can interrupt a disk writing action in the middle of its activity. If that happens, the usual result is one or more unreadable sectors. If they happen to be part of an archive file that you don't often access, you can go for literally years without discovering the damage. However if they are in a critical system file, you may not be able to reboot and in the worst case may have to do a complete reformat and reinstall everything.

It's good to remember that "raising elephants is so utterly boring" as a memory aid for the magic SysRq keys that the kernel recognizes. They are "REISUB" and to use them, you press and hold SysRq, then each of the keys in turn while waiting a couple of seconds between each. This will shut things down in an orderly fashion, preventing disk damage. The final "B" key in the sequence triggers a reboot. And since this is implemented in the kernel itself, at a level where most program loops can't prevent it from being recognized, it's far better than just pulling the plug.

Of course, if the elephants fail to do the job, then killing power is about the only alternative left...

---

