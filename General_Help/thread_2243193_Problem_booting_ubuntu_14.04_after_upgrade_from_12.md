---
title: "Problem booting ubuntu 14.04 after upgrade from 12.04- stuck in buzy box"
date: 2014-09-07
forum: General Help
---

### Post by johnnnz on 2014-09-07
I am having problem booting ubuntu 14.04 after upgrading from 12.04.
I get this message-
  	 	 	 	   [INDENT]
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
Gave- Check rootdelay= (did the system wait long enough ?)
- Check root = (did the system wait for the right device ?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/0a776846-5d7e-4688-a506-9a8536239afd does not
exist . Dropping to a shell!


Busybox v1.21.1 (Ubuntu 1:1.21.0-2ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)[/INDENT] I have seen some other people questions with the same problem but no answer that work for me or too technical to understand- I am a new ubuntu user.
The problem seem to occur when the light on my laptop CD tray comes on after I start the computer and is stuck closed.
Will doing a clean reinstall solve the problem? or is there a simple way to correct the problem?
Thanks
John.

---

### Post by Bashing-om on 2014-09-07
johnnnz; Ho Boy !
What a question:
> 
Will doing a clean reinstall solve the problem? or is there a simple way to correct the problem?

Where a "clean reinstall" may indeed be the faster/easier solution, but, but we learn nothing.
This is ubuntu, where with time, effort and patience the system is always fixable - not saying I always know the solution.
Here though we can surmise that the system can not determine the path to it's boot files. I can surmise that in that old 12.04 install there existed many old kernels and now with the upgrade there are space constraints and the new kernel did not install properly ???.
There are a number of avenues we can pursue seeking a solution.

May I suggest we look at the /boot partition from grub and see what exist ?
Can you boot to the grub menu ?
IF so what results -:
with the latest kernel highlighted, press the 'c' key for command line mode ;
We want to see now what the system sees for kernels:
what results are seen:
```

ls -lh (hd0,msdos1)
ls -lh (hd0,msdos1)/
ls -lh (hd0,msdos1)/boot

```
Here "hd0" is the 1st hard drive and "msdos1" is the 1st partition on that 1st hard drive, in that it is reasonable to "assume" that ubuntu is installed at that location. Else we will have to hunt up the proper location and adjust the seeking to find code accordingly .

Alternately, we could look things over from a liveDVD if ya got one on hand ( always a good thing to have !).

It is but
[INDENT][INDENT][INDENT]give the kernel a helping hand
[/INDENT][/INDENT][/INDENT]

---

