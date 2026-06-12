---
title: "Shutdown/Restart Hangs after crash"
date: 2007-03-05
forum: General Help
---

### Post by utkjamie on 2007-03-05
Yesterday Kubuntu froze up on me during a reboot and I had to go ahead and just kill the power. After restarting I began to get errors that write access was denied to certain file. I restarted in the hope that the problem would correct itself but then found myself staring  at an error telling me that I needed to run fsck. I then had to watch fsck list dozens of errors and what I assume were corrupted files to be fixed.

After getting back into Kubuntu everything appeared to be working fine -- although I believe some data files are now gone (those that I noticed, that is). The big problem right now, though, is that I cannot restart or shutdown the computer. Kubuntu begins the process, shuts down the desktop, flashes back to the desktop, and then the screen goes to black and it just hangs there. There are no error messages.

Sudo halt works (with a slight hang, however).

Any idea how to fix the problem?

---

### Post by vinchi007 on 2007-03-17
I have same hang problem, with reboot and halt, and all this started when I updated few days ago my ubuntu with program updates, but most important was kernel 10 -> 11 build. Now after this nice update problem occurred.

---

### Post by Blues- on 2007-04-30
Same problem here !
Anyone have a solution to this problem ?

---

### Post by vinchi007 on 2007-06-09
I figured out why this problem happened for me. I had auto-mount 2 ntfs partitions mounted in fstab for startup.
If you unmount them before shutdown or restart, linux will behave good and wont hang.

To make it automatic, I edited rc shut down script, dont remember name of it, you will see something like SxxxMOUNT or something similar in RC0 and RC1 folders. I put umount ntfs partitions commands with force option, and its good now, never hangs.

PS sorry for not providing you with step-by-step, Iam on the road with my mac.

---

