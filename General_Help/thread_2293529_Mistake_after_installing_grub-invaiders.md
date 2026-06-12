---
title: "Mistake after installing grub-invaiders"
date: 2015-09-05
forum: General Help
---

### Post by SIRivanhoe on 2015-09-05
During instalation  i ve got mistake and now cant remove grub-invaiders

:~$ sudo apt-get autoremove
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
The packages will be REMOVED: WILL BE REMOVED
grub-invaders
0 upgraded, 0 installed new packages, to remove the packages marked 1 and 195 not upgraded.
not fully installed or removed packages 1.
After this operation, the amount of disk space will be at 54,3 kB.
Do you want to continue? [Y / n] CONTINUE? y / N
(Reading database ... for the moment found 169,432 files and directories.)
Deleted grub-invaders (1.0.0-12) ... REMOVING
Creating a configuration file grub ...
dpkg: error processing package grub-invaders (--remove): MISTAKE
subprocess installed post-removal script returned error code 1
When processing the next packet errors occurred:
 grub-invaders
E: Sub-process /usr/bin/dpkg returned an error code (1)

I cant even upgrade packets

---

### Post by ajgreeny on 2015-09-05
I suspect that the error message you see in the output:-
```
0 upgraded, 0 installed new packages, to remove the packages marked 1 and 195 not upgraded.
```may mean that you need to make sure the system is fully updated with ```
sudo apt-get update
sudo apt-get upgrade
```  Then try the autoremove again.

---

### Post by SIRivanhoe on 2015-09-06
does not work. mistake halts upgrade. I ve mark broken package for hold, and then upgaded system. I ve marked it for unhold, but truely if broken package was kept
mistake is the same without any changes.

---

