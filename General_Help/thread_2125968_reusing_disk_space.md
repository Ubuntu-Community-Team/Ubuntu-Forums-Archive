---
title: "reusing disk space"
date: 2013-03-15
forum: General Help
---

### Post by malakar.subhendu on 2013-03-15
I had a earlier version of ubuntu (12.04) on my machine and then installed mint 14 as a third OS(other being windows). I want to get back the disk space used by ubuntu and use it as data drives. How to do that. I had formatted them as ext4 and done a update-grub. But i want to merge the two drives and gparted is not allowing me to do that. (it says please unmount all drives with number more than 7). The /dev/sda8 and /dev/sda9 are my present working partitions so i can't unmount them. How to get the disk space back. Forgot to mention that after formatting them as ext4 , i'm not able to create any file in it.

---

### Post by agillator on 2013-03-15
Run gparted from a live cd, either the Ubuntu installation cd or a gparted live cd. You can do nothing with mounted partitions and running from a live cd solves that problem. Now, the reason you can do nothing with sda8 and sda9 mounted is that if you remove sda7 (or 6 or 5 or . . . ) all the subsequent partitions will be renumbered. This can cause problems if you are not expecting it. You don't actually lose anything that is in the partitions, it is just that the computer can't find them because the number has changed. Look at your fstab, for example. See how many partitions are mounted by /dev/sda(x). Using block ids in fstab gets around this problem. What I can't remember right now is whether you have to reload GRUB if the boot partition changes number. I think you do. That isn't hard, but you need to be ready to do it, so look that up just in case.

---

### Post by malakar.subhendu on 2013-03-16
Thanks for the reply, but i found a better link which worked for me.

[http://unix.stackexchange.com/questions/13733/adding-an-unused-partition-to-a-linux-filesystem/13734#13734](http://unix.stackexchange.com/questions/13733/adding-an-unused-partition-to-a-linux-filesystem/13734#13734)

---

