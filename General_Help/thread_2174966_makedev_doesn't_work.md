---
title: "makedev doesn't work"
date: 2013-09-17
forum: General Help
---

### Post by RogerDavis on 2013-09-17
I want to use makedev to try some things with my USR modem.  When I try to invoke make dev, I get "roger@roger-desktop:~$ sudo makedev,  -  [sudo] password for roger:,  -  sudo: makedev: command not found".  I tried to uninstall and reinstall (Software center says I have it already), but no success.

Also, - roger@roger-desktop:~$ cd /dev; ./MAKEDEV ttyS4   -   bash: ./MAKEDEV: No such file or directory   -   roger@roger-desktop:/dev$ 

I was able to update it with Synaptic Package Manager, but no change to these results.

Any ideas on what's next?

Thanks!

---

### Post by spjackson on 2013-09-19
Try "sudo MAKEDEV" or "sudo /sbin/MAKEDEV".

---

### Post by RogerDavis on 2013-09-19
Maybe I missed the point, but I just now got it to work as below (note that I previously did try upper case with no luck) :
roger@roger-desktop:~$ sudo cd /dev; ./MAKEDEV ttyS4
[sudo] password for roger: 
sudo: cd: command not found
bash: ./MAKEDEV: No such file or directory
roger@roger-desktop:~$ cd /dev
roger@roger-desktop:/dev$ sudo ./MAKEDEV ttyS4
sudo: ./MAKEDEV: command not found
roger@roger-desktop:/dev$ MAKEDEV ttyS4
mknod: `ttyS4-': Permission denied
makedev ttyS4 c 4 68 root dialout 0660: failed
roger@roger-desktop:/dev$ sudo MAKEDEV ttyS4
roger@roger-desktop:/dev$

---

