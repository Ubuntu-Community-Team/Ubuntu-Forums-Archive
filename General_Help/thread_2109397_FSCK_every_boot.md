---
title: "FSCK every boot"
date: 2013-01-27
forum: General Help
---

### Post by pjalegria on 2013-01-27
Hi

After upgrade Lubuntu 12.04 to 12.10 on my Acer Aspire One 8GB SSD, I get fsck every boot... i dont now how to fix it. My fstab: > #/etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda1 during installation
UUID=59b9a797-e2a8-47df-a6b3-cdfc442f0932 / ext4 noatime,nodiratime,discard,errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=f924e3ca-7324-45e5-b52b-999cd813db14 none swap sw 0 0

#Reduce SSD Wear
tmpfs /var/log/apt tmpfs defaults 0 0
tmpfs /var/log tmpfs defaults 0 0
tmpfs /tmp tmpfs defaults 0 0
tmpfs /var/tmp tmpfs defaults 0 0

I find this bug Bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1073433?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1073433?comments=all), maybe is related!!!

---

### Post by TheFu on 2013-01-27
There are 3 reasons that an fsck is run beyond a check for clean just before mounting:

[LIST=1]
[*]Improperly closed file system (not "clean")
[*]/forcefsck file in the root directory
[*]Settings from tune2fs that say to run it after X reboots or X days. I think this is set to 30 by default, but don't quote me.
[/LIST]
So, the only hope we have to determine which of the 3 options is to remove the others from possibility.  



**man tune2fs**
will explain how to check the file system fsck period. -c and -i options are what you are looking for - maybe.



I would start by checking the log files in /var/log/ for warnings and errors.  This command should help.

$ sudo egrep -i 'warning|error' /var/log/* | more


If it happens at every reboot and the forcefsck and time-to-next fsck is not less than 1 for the file system, then only option 1 remains.  Are you 100% certain that the file system is being cleanly unmounted when you shutdown?



This solved thread might help too: [http://ubuntuforums.org/showthread.php?t=1680978](http://ubuntuforums.org/showthread.php?t=1680978)

---

### Post by pjalegria on 2013-01-27
When i do "sudo tune2fs -l /dev/sda5" i get "Filesystem state: not clean" even after a fsck on boot!!!

---

### Post by TheFu on 2013-01-27
> **pjalegria said:**
> When i do "sudo tune2fs -l /dev/sda5" i get "Filesystem state: not clean" even after a fsck on boot!!!

You can't run that when the file system is mounted (i.e. booted and in use).  
Are you booting off a USB drive or CD and running it?  I keep a gparted CD around (actually on a USB flash drive) for stuff like this.

I would boot off a flash drive and manually run # **fsck -f /dev/xxxxxx**
That should give you a better idea if this is a chronic issue or not.

---

### Post by pjalegria on 2013-01-27
I run # fsck -f /dev/sda1 from Grub recovery and i dont get any error, after that i reboot and still do fsck!!!

---

### Post by TheFu on 2013-01-27
Do you think the "discard" option might be an issue?  The man pages says that it is off by default until sufficient testing has been completed.

Besides that, I don't have a good answer besides a failing SSD or controller or software bug. 

Do you have SMART enabled? Anything interesting inside that data?

---

### Post by pjalegria on 2013-01-27
I remove "discard" option, no change!!! but i discover, if close network-manager before shutdown it solve the problem!!!!

---

### Post by pjalegria on 2013-01-28
As suggestion at #10 of [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1073433](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1073433), if I unckeck "available to all users" in all connections, wired, wireless and mobile, it solve the problem.

---

### Post by TheFu on 2013-01-28
> **pjalegria said:**
> As suggestion at #10 of [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1073433](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1073433), if I unckeck "available to all users" in all connections, wired, wireless and mobile, it solve the problem.

**Seems that you definitely found a bug and a workaround!**
Very nice work!  Please mark the thread as solved in the "thread tools" above.

Sorry that I wasn't able to help at all. ;)

---

