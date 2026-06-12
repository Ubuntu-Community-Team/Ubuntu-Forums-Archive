---
title: "Start-up failure ubuntu 12.04"
date: 2014-02-03
forum: General Help
---

### Post by ibates on 2014-02-03
This thread follows on from an earlier unsolved thread entitled ***Boot failure, failed boot-repair***. 

This new thread is opened because it has become obvious from the earlier thread that there does not appear to be any problems with boot.  It is the loading of the Start-up components which fail thus preventing the system from loading and thus stopping the running of the system.

When attempting to start in *Recovery Mode* and just before the loading of the start-up components halts, there is a FATAL Error message displayed.

*Loading essential drivers .... FATAL: Error inserting echo (/lib/modules/3.2.0-58-generic-pae/kernel/drivers/staging/echo/echo.ko): unknown symbol in module, or unknown parameter (see dmesg)*

While seemingly impossible to positively relate the time line of the message in *dmesg* with that of the error message on the loading screen, examination of *dmesg* does show the following line at about the point in the procedure where the failure seems to occur.  This line is:

[I]echo: module is from the staging directory, the quality is unknown, you have been warned.
[    4.643299] echo: Unknown parameter `FRAMEBUFFER'[/I]

After that point in *dmesg* errors and warnings start to appear until the procedure stops whereas prior to that point there were no errors or warnings.

(The *dmesg* log appears in the earlier post shown above).

I do not know how to view the contents of the file */lib/modules/3.2.0-58-generic-pae/kernel/drivers/staging/echo/echo.ko* and thus have no idea how to correct it, even if that could be done.

Is this likely to be the cause of the failure to start-up, and can anyone help with this problem?

---

### Post by steeldriver on 2014-02-03
Hmm I think I can guess what might have happened (pasting an 'ech*o' *that you should have executed as a command?) but let's see the output of

```

grep -r 'echo' /etc/modprobe.d/ /etc/modules

```

---

### Post by ibates on 2014-02-03
That was quick!

Where do I find the terminal to enter that command?  I can boot from the LiveCD, or I can get a terminal at root level in Recovery Mode from the HDD.

---

### Post by steeldriver on 2014-02-04
Yes sorry in the absence of a complete boot you would need to do that from recovery mode or failing that from a live CD (after mounting the system drive)

We're just looking for instances where the echo command might have got misinterpreted as a reference to the echo kernel module

---

### Post by ibates on 2014-02-04
I have attempted to do the *grep* from both the Recovery Mode (root), and also after booting up from the LiveCD.  I thought I had mounted the device, but the *grep* did not look appropriate.  I think I was looking at the report from the LiveCD boot.  I do not think I had mounted the device.  In recovery mode, it simply returned */dev/sd.. not a directory*.

Could you please advise me how to mount the device after booting from the Live CD so as to do the *grep*.  I will then post the report.

Thanks.

---

### Post by ibates on 2014-02-04
OK; I think I have worked out how to mount the device after booting up with LiveCD.  I am then able to *cd* to the device ID in */media/* and have access to the entire file system.

From a terminal while in that device folder I have then run the command you detailed above

*grep -r 'echo' /etc/modprobe.d/ /etc/modules*

The contents of */etc/modules* following that command is:

[I]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp[/I]



This does not look particularly encouraging.

What now?

---

### Post by steeldriver on 2014-02-04
OK well it seems like my initial guess has not thrown up anything - I was hoping you'd find a rogue mention of 'echo' either in one of the files in /etc/modprobe.d/ or in the main /etc/modules file - you didn't

Back to the drawing board I guess - let's hope someone else has some ideas

---

### Post by oldfred on 2014-02-06
Closed see this thread.
[http://ubuntuforums.org/showthread.php?t=2203962](http://ubuntuforums.org/showthread.php?t=2203962)

---

