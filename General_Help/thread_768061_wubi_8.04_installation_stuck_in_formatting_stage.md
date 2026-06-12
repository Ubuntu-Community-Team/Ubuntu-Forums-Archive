---
title: "wubi 8.04 installation stuck in formatting stage"
date: 2008-04-26
forum: General Help
---

### Post by mataal on 2008-04-26
[FONT="Lucida Console"]hi,

i ran the wubi installer (with desktop environment Kubuntu) on windows overnight and in the morning i saw it asked me for a reboot.
on reboot, the boot screen appeared fine and i started the installation of Kubuntu.
However, everytime i do this the installation starts up ubiquity and gets stuck at the screen "Formatting swap scape in partition #1 of host/disks/swap.dsk..."

any ideas how do i proceed on this?

-ashish
[/FONT]

---

### Post by rainpl on 2008-04-26
I've got the same problem, posted logs in another thread: [http://ubuntuforums.org/showthread.php?t=766320]("http://ubuntuforums.org/showthread.php?t=766320")

---

### Post by ago on 2008-04-26
This is normally due to fragmented swap.disk

Uninstall, reinstall and run jkdefrag on c:\ubuntu\disks\swap.disk BEFORE rebooting
Then reboot and see if it works

Pleas post your findings here: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/222546](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/222546)

---

### Post by mataal on 2008-04-26
[FONT="Lucida Console"]@ago: thanks a bunch. 

what i did was to delete the swap and root .disk files. defrag my hard drive a couple of times. used "fsutil file createnew" to create 'less' fragmented ones and reboot to continue installation.

-ashish[/FONT]

---

