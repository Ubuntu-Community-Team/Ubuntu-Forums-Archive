---
title: "Issue Getting Updates on Version 15.10"
date: 2016-07-03
forum: General Help
---

### Post by Richard_Alexander on 2016-07-03
I have a laptop running Ubuntu 15.10 that I want to upgrade to 16.04.  When I attempt to install the latest updates, it says that it can't as there is not enough space.  The space needed is 95Mb.  The free space on the HD is 135Gb.  Can someone explain why this would be and how to work around it?

---

### Post by grahammechanical on 2016-07-03
There is an explanation but I have no way of knowing if it applies to your system.

The update includes a kernel upgrade. You have a /boot partition and it is full. And so the new kernel cannot be added. Whatever the cause you can select Advance options for Ubuntu at the Grub boot menu and then select a kernel with recovery mode.

Then at the recovery menu select Clean - try to make free space. That option will run 2 commands. The clean & the autoremove command. You can also run those commands from a terminal.

```
sudo apt-get clean
sudo apt-get autoremove
```

The autoremove command will remove at least one kernel. You may want to run autoremove more than once to remove other kernels.

Regards.

---

### Post by oldos2er on 2016-07-03
Please post the output of both commands: ```
df -h

mount
```

---

### Post by Richard_Alexander on 2016-07-04
Mark this one solved.  The clean and autoremove (twice) did the trick.  System is now getting updates and even upgrading to 16.04.

---

### Post by mörgæs on 2016-07-04
No, you do that. 
See Thread Tools.

---

### Post by Richard_Alexander on 2016-07-07
> **mörgæs said:**
> No, you do that. 
See Thread Tools.

Got it and done.  Did not realize that I could do that.  Thanks for the tip.

---

