---
title: "Mount issues"
date: 2007-06-14
forum: General Help
---

### Post by rpalmer on 2007-06-14
I have two hard drives installed on my ubuntu box.  a 20GB for the OS and a 120GB for sharing files.   I created a folder for the 120GB to mount to,(/mnt/mirror) and added an entry in fstab.  It appears that I've done it correctly but for some reason the folder only shows 17GB of space even though it's mounted to a 120GB drive.  What am I doing wrong?

---

### Post by earobinson on 2007-06-14
yould you type df in the terminal and post the output

---

### Post by rpalmer on 2007-06-14
rpalmer@rypp-ubuntu704:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             18398028   3820092  13643360  22% /
varrun                  192992       272    192720   1% /var/run
varlock                 192992         0    192992   0% /var/lock
procbususb              192992        84    192908   1% /proc/bus/usb
udev                    192992        84    192908   1% /dev
devshm                  192992         0    192992   0% /dev/shm
lrm                     192992     33788    159204  18% /lib/modules/2eneric/volatile

---

