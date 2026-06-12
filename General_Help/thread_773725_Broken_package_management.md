---
title: "Broken package management"
date: 2008-04-29
forum: General Help
---

### Post by boubbin on 2008-04-29
Im running Kubuntu hardy and my system in in finnish so i have made hard translations of the output of the apt-get:

root@supervisor:/home/boubbin# sudo apt-get upgrade
Loading packages list... Ready
Forming the tree of dependencies 
Reading state information...Ready
These packages have been let to wait:
  prboom
0 updated, 0 new, 0 removed and 1 to update.
1 wasnt installed fully or it was removed
Do you want to continue [Y/n]? y
Configuring: papercut (0.9.13-5) ...
Starting papercut detection : papercut

papercut seems to be already running.
.
[: 77: ==: unexpected operator
failed
invoke-rc.d: initscript papercut, action "start" failed.
dpkg: error handling papercut (--configure):
 subprocess post-installation script returned errorcode 1
Errors were encountered while processing:
 papercut
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@supervisor:/home/boubbin#

---

### Post by boubbin on 2008-04-29
found the problem now!
i edited /etc/init.d/papercut and the first line was:
#! /bin/sh
but "==" were used in the file that is bash-spesific, so i just removed one "=" and got it working.

---

