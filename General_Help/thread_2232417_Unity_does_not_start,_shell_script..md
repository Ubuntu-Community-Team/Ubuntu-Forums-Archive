---
title: "Unity does not start, shell script."
date: 2014-07-01
forum: General Help
---

### Post by bob89 on 2014-07-01
Ok, so, I have a unbootable ubuntu(I can boot in to text base by holding Alt-F4.)
So, I made this SH file, 
It works, but my dash/search results are not working.

Also, my panel is not working, but I don't care about that as much
Here is my .sh file

```
startx
service lightdm start
compiz
setsid unity
```

How do I start unity correctly, with search results.

---

### Post by deadflowr on 2014-07-01
How are you running this script?
As root?

If so, stop.
The 3 commands for startx, compiz and setsid unity, should all only be run by a normal user.(non-root)

What you could try is restarting lightdm, changing the start option to restart. 
But starting, or restarting lightdm should be dropping you into the login screen.
So, I'm not clear on that issue.

More info on what exactly is happening when you startup will be most helpful.
I guess...

---

### Post by grahammechanical on 2014-07-02
Perhaps it is better to fix what is wrong with the normal loading process of Ubuntu, even by doing a reboot. Are you aware that we have a Recovery Mode? We select it at the Grub boot menu. We get these options

1) Resume   -  resume normal boot - loads with an open source video driver
2) Clean      -  try to make free space
3) dpkg       -  repair broken packages
4) failsafeX -  run in failsafe graphic mode - broken from my experience
5) fsck       -  check all file systems
6) Grub      - update grub bootloader
7) network  - Enable networking - necessary if we want to install packages or update/upgrade
8) Root      - drop to a root shell prompt
9) System-summary

We can also, from the Grub menu, load into an earlier kernel. Which is sometimes useful if a kernel update is causing the problem.

Regards.

---

