---
title: "XWindows configuration doesn't work with my monitor"
date: 2016-04-15
forum: General Help
---

### Post by james216 on 2016-04-15
I have an IntelNUC that I installed Ubuntu 14.04LTS Desktop on.  I have 2 monitors.  The one I used during the installation process which hangs on the wall in my bedroom, and the one that the NUC needs to use on my desk in my workshop which is an old TV with HDMI support(since that's the NUC's video out).  I can confirm that on monitor A Ubuntu is installed, and works.  When I go to put it on Monitor B the NUC starts up and after the NUC splash screen the monitor flickers and goes to the "no signal screen".   I have sshd running on the machine so I can log in via ssh and make changes, but I don't know how to fix the issue.  Everything I've tried on various forums/question and answer sites has not given me the information I need to resolve this problem.

I have tried to use monitor B to install Ubuntu, but I get the same issue with the installer, and can't see the installer to process the install.

Please help.

---

### Post by james216 on 2016-04-18
I have added "nomodeset" to my /etc/default/grub file and have run update-grub.  This partially fixes the problem.  I am now able to see something on the monitor.  I get a bunch of white character stripes and scrambled characters.  It eventually boots me into "low graphics", but I get a dialog that lets me do pretty much nothing.  I chose any of the options and none of them really work.  Literally "create new profile"  ends in a circle with no way to create a new profile.

---

