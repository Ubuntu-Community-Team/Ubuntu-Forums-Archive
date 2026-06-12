---
title: "Problem installing on either drive"
date: 2007-10-04
forum: General Help
---

### Post by Dave(dbd) on 2007-10-04
I can't seem to get ubuntu to install on either of my drives. Both are ata drives with multiple partitions. When installing on a partition on my secondary drive, installtion stalled on:

Booting ' /boot/grub/menu.lst'

Or something along those lines. I unistalled via windows and reinstalled on a different partition on a different physical hard drive. Btw, both are NTFS. This time I get something along the lines of

Check root=bootarg cat /proc/cmd line
or missing module, devices, cat /proc/modules ls /dev
ALERT! does not exist. droping to a shell

(something about a shell)

 /bin/sh: can't access tty; Job control turned off
(then I can type)


So ubuntu or wubi doesnt like me very much.

---

### Post by ZenWarrior on 2007-10-04
Should you attempt to reinstall on your primary drive, I have found it best to optimize the drive before installation.

First run something like CCleaner to remove all the junk and clutter. (You can even remove all the Hotfix installers. You'll never need them.) While in CCleaner, have it check/fix any minor registry problems. Set chkdsk to inspect the drive during the next restart.

Then restart and turn off every nonessential process and service. Some may require Task Manager. Others might even require that you go into Services and temporarily disable them. (They are the automatic ones that restart after the process is stopped in Task Manager.) When finished, you should see a very short list of processes in Task Manger.

Exit Task Manager and then run a defrag on the volume. With very little running and tons of useless files removed, your defrag should clear up some pretty big spaces. Restart with running chkdsk again. Now install Wubi/Ubuntu. 

Hope that helps some.

---

