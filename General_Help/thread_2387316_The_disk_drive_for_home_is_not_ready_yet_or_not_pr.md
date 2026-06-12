---
title: "The disk drive for /home is not ready yet or not present"
date: 2018-03-17
forum: General Help
---

### Post by Keith_Beef on 2018-03-17
OK, this is more or less the same question as in [another thread]("https://ubuntuforums.org/showthread.php?t=1507558"), and I've not yet tried commenting out the lines in /etc/fstab as advised there.

I found that my daughter had been using the main computer (I'm typing this from a laptop), and had left it at the login chooser; when I tried logging in, I got more or less the session I had left in hibernation, but none of the applications were responsive (I had Firefox, evince, geany and a terminal open). When I tried doing ls ~ I got an I/O Error. Nothing was working as I expected, so I did a complete power off and reboot. On rebooting, I got console messages of "the disk drive for /home is not ready yet or not present" (same on a couple of other file systems).

I'm trying to understand what's happened. The entries in /etc/fstab have a UUID, not a label or device, but I have a comment line before each one, like "During install, /home was on /dev/sdf1".

I've also tried doing fsck on /home, using the UUID, and I get a response "unable to resolve UUID=b6ea...." 

That other thread mentions
[>  You get this message because you disconnected that disc and is still mounted when the system is booting.]("https://ubuntuforums.org/showthread.php?t=1507558&p=10136133#post10136133")

I thought that mounted filesystems were listed in /etc/mtab; if I boot from a live CD, will it help fix the problem if I go and delete any lines in /etc/mtab that refer to these filesystems that are giving me the "not ready yet or not present" messages?

Thanks in advance for any help you can give me.

---

### Post by deadflowr on 2018-03-17
Is home on a different hard drive or just a different partition?

---

### Post by Keith_Beef on 2018-03-17
/home is on a physical drive with one or two other filesystems (maybe /films or /music); things like /boot, /var and /lib and / are on other physical drives.

---

### Post by deadflowr on 2018-03-17
Are they showing in fdisk or parted list commands like
```
sudo parted-l
sudo fdisk -l
```

You might also double check that the UUID did not change somehow (they really should not have changed)
```
sudo blkid
```

and also triple check that the disks aren't dying:
[https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")

You can run/install all of these from a live session.

---

### Post by Keith_Beef on 2018-03-17
Thanks, deadflowr, I'll give those a try.

---

