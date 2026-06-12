---
title: "Accidentally changed the partition UUID where Ubuntu is installed, now I can't boot"
date: 2017-12-18
forum: General Help
---

### Post by funkymarxist on 2017-12-18
I can't boot Ubuntu, since I've changed the partition UUID by mistake. I'm getting the message "Gave up waiting for root device! "

I've looked up online for solutions for this problem, such as reinstalling Grub, but it didn't work. I tried editing /etc /fstab but I can't seem to find the new UUID for the Ubuntu partition which is dev/sda6.

Thanks in advance for the help!

---

### Post by yancek on 2017-12-18
Use the Live DVD or flash drive you are booting and open a terminal and run this command:  sudo blkid
Look at the output for the UUID corresponding to sda6.  You will likely need to change the entries in fstab and grub.cfg before being able to boot.

---

