---
title: "Hard drive filling up  -  Anyone else?"
date: 2007-07-05
forum: General Help
---

### Post by nick.carstensen on 2007-07-05
Anyone else having issues with hard drive filling up when not doing anything.  I am just running the same command over and over (df -k) and notice the used is going up and up.  This will happen for a few days, then the disk becomes full.  Doing a df -k shows full, but a du  -h --max-depth=1 shows about 60% used.

A Reboot takes care of the issue for awhile, but I would like to know what is causing this.  Is there anything to watch what is getting written to disk to see what is filling up the drive?

I am on Feisty 2.6.20-16 kernel.  Using Kubuntu.

Thanks for the help.

---

### Post by PaulFr on 2007-07-06
Not happening here. Can you narrow it down to a directory tree, say **/var** or **/tmp** ? Since you say a reboot solves the problem for a while, it would seem to be in /tmp or /var/tmp. Check file sizes in these directories periodically to see any obvious choices.

If no obvious choices are present, you can use **sudo lsof -r +D /tmp > /tmp/file** to find out what files are open in /tmp (change +D /tmp to +D <dir> as per your findings). Then you can compare the first snapshot to the last to see which files have grown. Hope this helps.

---

