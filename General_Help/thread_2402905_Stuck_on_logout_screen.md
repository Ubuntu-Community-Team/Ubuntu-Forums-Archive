---
title: "Stuck on logout screen"
date: 2018-10-05
forum: General Help
---

### Post by ubuntini2 on 2018-10-05
Hi
Running Ubuntu Mate 18.04 LTS.
Last evening was copying files to opt directory (don't ask!) and ran out of space.

Logged out and wasn't able to log in again.
Rebooted, still stuck at logout screen(attached)
After entering pw, the OS seems to try and log in, but I'm kicked back to the logout screen
I normally only see this screen if I manually logout.

To make matters more frustrating my Grub menu is hidden so am unable to even switch to Windows (its a dual boot system) on boot.

I assume the issue is related to 100% full drive and or directories.
Any suggestions?

---

### Post by ajgreeny on 2018-10-05
Boot to a live system on USB and then you can both see the situation of your installed system's disk usage, and if necessary, also remove some of those files, or move them elsewhere if you must keep them.

From the live system run ```
df -hT
``` which should show the usage of all partitions.

Just out of interest, as you have a dual boot system, why have you hidden the grub menu; how do you manage to boot Windows?
Is Windows on a separate hard drive which you boot to from the UEFI menu at boot instead of grub?

---

