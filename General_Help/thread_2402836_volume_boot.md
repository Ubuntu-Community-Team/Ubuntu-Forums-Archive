---
title: "volume boot"
date: 2018-10-04
forum: General Help
---

### Post by martinscotland on 2018-10-04
Hello, i am getting a notice that says, the volume "boot has only 0 bytes space remaining. I am running Ubuntu 16.04 LTS. Any help would be delightful!. Thank you, Martin

---

### Post by oldfred on 2018-10-05
Are you using LVM or LVM with full drive encryption?
That has a separate /boot partition and you regularly need to houseclean old kernels. 

Post these:
sudo parted -l
df -H

---

### Post by martinscotland on 2019-02-17
Hey, so sorry on the time its taken to get back! No internet for the last 3-4 months. I&#8217;m still having the problem. well didn&#8217;t fix it the first time. Would you please be able to help? I'm not sure what " LVM or LVM with full drive encryption" means but if I can learn. Thanks.

---

### Post by oldfred on 2019-02-17
LVM is an advanced volume management system. Not really recommended for beginners, but if you want full drive encryption you need to use LVM. 

       LVM - Logical Volume Management.
LVM Advantages/Disadvantages Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)

---

