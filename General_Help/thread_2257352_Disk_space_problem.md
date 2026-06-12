---
title: "Disk space problem"
date: 2014-12-19
forum: General Help
---

### Post by kevin134 on 2014-12-19
Ok so I'm new too linux. I had my Windows unexpectedly wiped off my hard drive by a friend of mine. So instead of installing Windows again I decided to install Linux unbuntu. Everything went smooth got it running perfectly fine. Until yesterday after downloading a few movies it came up with not enough disk space. Which is confusing because I am sure I allocated 500GB of space when I installed it.
what is the best option to do now?
Will I need to completely reinstall Linux again??

---

### Post by mörgæs on 2014-12-19
Welcome to the fora.

Please run **df -m** and post the output in CODE tags.

---

### Post by kevin134 on 2014-12-19
Hopefully this is what you ment.


kevin@kombat87:~$ df -m
Filesystem                  1M-blocks  Used Available Use% Mounted on
/dev/mapper/ubuntu--vg-root    465124  3132    438343   1% /
none                                1     0         1   0% /sys/fs/cgroup
udev                             1907     1      1907   1% /dev
tmpfs                             384     2       383   1% /run
none                                5     0         5   0% /run/lock
none                             1917     1      1917   1% /run/shm
none                              100     1       100   1% /run/user
/dev/sda1                         236    37       188  17% /boot
kevin@kombat87:~$

---

### Post by kevin134 on 2014-12-19
I've reinstalled Linux from scratch again. But now I'm having another issue. When I'm trying to install apps it only comes up with use source. Sorry for all the newbie questions.

---

### Post by sotiris2 on 2014-12-19
How exactly are you trying to install applications?

---

### Post by oldfred on 2014-12-19
Your post shows vg-root, which is a LVM install.
You can select LVM or it defaults to LVM with full disk encrytion, but I consider LVM more advanced and it needs different tools, procedures than standard partitioned installs.
Do you want/need encryption?

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

