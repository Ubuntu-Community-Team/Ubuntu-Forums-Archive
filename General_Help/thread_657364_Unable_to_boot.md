---
title: "Unable to boot"
date: 2008-01-03
forum: General Help
---

### Post by DariusJD on 2008-01-03
Okay. I am not dual-booting. I am running Ubuntu 7.10.

Recently, I did some updates via Synaptic and such. I do believe sysvinit was one of them but I think it failed to install. Last night, I restarted my computer (I was working fine) and when it attempt to boot up it just didn't...

I got something like:

Target filesystem doesn't have /sbin/init

Busybox v1.1.3.
/bin/sh: can't access tty; job control turned off

It sucks because I can only access things via this 7.04 live CD. Also, I looked on Synaptic and found that upstart was installed, so I uninstalled upstart and installed sysvinit WHILE ON THE LIVE CD.

However, when I booted up this morning using the live CD, I learned that the installation was discarded the moment I turned the computer off. Meaning, upstart is still installed. 

Is there a way to get my /sbin/init folder back? Am I going to have to reinstall Ubuntu using this 7.04 CD?

---

### Post by DariusJD on 2008-01-03
Also, I was reading some thread of people who have the same problem.

[http://ubuntuforums.org/showthread.php?t=295508](http://ubuntuforums.org/showthread.php?t=295508)

I can't even mount my filesystem because /dev/hda1 doesn't exist...

My /etc/fstab says:

> 
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0


...

---

### Post by p_quarles on 2008-01-03
When you ran the live CD, you were actually installing sysvinit into memory, not the hard drive. 

What I would suggest is trying to boot into the "System Rescue Mode" on the CD (in the initial menu, before it goes into the live mode). This will attempt to mount one of your partitions (choose the root partition, or the one marked "/"), and then will give you a command line interface with which you can perform rescue operations.

If the problem is, in fact, sysv-init, you'll be able to install that by typing this:
```
apt-get install sysvinit
```
Don't bother to uninstall anything, since the package manager will take care of any dependencies or conflicts. 

That said, the problem could also be a number of other things, including a corrupted filesystem. Try this first, and if it doesn't work there are other options to explore.

---

