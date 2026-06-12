---
title: "Filled up disk leads to kernel panic on boot"
date: 2013-02-22
forum: General Help
---

### Post by dargaud on 2013-02-22
Hello all,
I have a problem with a familly computer I admin remotely.
The login screen was all screwed up and I couldn't login remotely with VNC.

Via ssh I searched for a while and since there were many updates in the pipe, I did "aptitude update" "aptitude full-upgrade" which failed with tons of strange dependency problems.
After a while I noticed that the disk was full, so I freed 4G and tried to resume the update. No go.
I did a reboot, but now I have a kernel panic, no matter what version of the kernel I try (even in recovery mode).

So how do I fix this mess ? It's probably impossible remotely, but even if I were in front of it I wouldn't know what to do.
Thanks

---

### Post by dargaud on 2013-02-22
No takers ?

---

### Post by TheFu on 2013-02-22
I did an update a few weeks ago that filled the /boot partition.  Fortunately, it filled before trying to rebuild the initrc.img, so picking an older kernel worked, I cleaned up about 10 old kernels, forced the installations to finish (apt-get install -f) and all was fine.

I would think the steps required would be
* install a new kernel
* reinstall grub
* force initrd.img to be rebuilt

but I honestly do not **KNOW** the answer.  The easy answer would be to restore from a backup prior to the issue.

It is best to avoid filling file systems (or running out of inodes) on Linux/UNIX machines.  There is a reason that running above 90% gives a warning. Bad things happen.

---

### Post by dargaud on 2013-03-14
I installed a new drive and copied a backup of the user directory in it and sent it by mail for the user to put in his PC instead of the old disk. It worked fine on my system but impossible to get it to boot there. Can't even get to grub. I'll try again next week when I'm in front of the PC.

---

### Post by TheFu on 2013-03-14
Sounds like some sort of hardware failure. PSU, GPS, disk controller, or a stupid SATA cable.

This sort of issue is why I create 2-10G OS/App partitions on HDDs for remote administration. There is always a way to remote in. All the local person needs to know is how to select a different boot option.  Putting /home on a different partition from the apps/OS is still a best practice.

OTOH, if this is for a business, then only buying hardware that support DRAC/RIBLO remote access cards can pay for themselves with the first issue. This hardware lets us remotely power off/on a system and watch the BIOS from anywhere. Not just a reboot, bot a complete power down.

---

### Post by dargaud on 2013-05-24
A direct reinstall on the machine solved the problem. I could probably have solved it by messing with grub, but 10 min for a full install followed by 10 minutes to copy the user directory while a system update goes on is simply easier.

---

