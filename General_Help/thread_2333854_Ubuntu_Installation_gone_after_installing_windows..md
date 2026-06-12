---
title: "Ubuntu Installation gone after installing windows."
date: 2016-08-13
forum: General Help
---

### Post by The_Forgotten_King on 2016-08-13
I upgraded from windows 32 bit to windows 64 bit, and after the installation, I went to reinstall grub, but it failed. Now, my ubuntu installation (both partitions, / and /home) don't show up on the table. Using Gpart finds /, but not /home, where all of my data is. Is there a way to find it? No new data has been written.

---

### Post by yancek on 2016-08-13
What 'table' are you referring to? Windows won't show a Linux entry to boot, you would have to manually configure it yourself.  How did you try to install Grub if you can't boot Ubuntu?  Live CD?  Boot any Linux Live CD/flash drive and open a terminal and as root/sudo run the following commands:

fdisk -l 
parted -l

Lower case Letter L in both commands.  Post the output here.

---

### Post by carl4926 on 2016-08-14
In a default ubuntu install there is no separate /home partition, unless you know you specifically created such /home is in /

---

### Post by carl4926 on 2016-08-14
> **carl4926 said:**
> In a default ubuntu install there is no separate /home partition, unless you know you specifically created such /home is in /
And you can usually access all this from Ubuntu Live

---

