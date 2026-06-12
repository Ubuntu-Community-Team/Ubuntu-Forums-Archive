---
title: "Boot directory woes"
date: 2017-02-03
forum: General Help
---

### Post by asearle on 2017-02-03
Hallo Everyone,

Some time ago I installed Ubuntu 14.04 for a friend and unfortunately set the boot-directory to fixed size (it was a clickable option).  Anyway, now the boot directory fills up with kernels and then, periodically, updates stop working. Arrgghh!

I have been trawling the internet for solutions and found one which was to set "autoremove" but now his boot directory is filling up with old (somehow recovered) kernels which had been deleted but now, whenever there is an update, reappear. I need to find out where I set the autoremove and remove that option.

Apparently in newer versions this problem was fixed but can anyone tell me how to fix this installation now that it already has the problem. i.e. maybe with a script or a setting but I have certainly got the wrong one.

Also now one kernal didn't finishing installing so the PC won't boot: What my friend has to do is to go into options and choose a previous kernel to boot from which as a non-computer-savvy person, is freaking him out. So how do I get the system to disregard the last badly installed kernel and return to booting from the last valid kernel?

Any tips would be a great help.

Many thanks,
Alan

---

### Post by Bashing-om on 2017-02-03
asearle; Sure;

Should not be a big deal to fix.
Boot up from an older kernel and post back:
```

df -h
df -i
sudo apt update
sudo apt upgrade
dpkg -l | grep linux-
ls -al /boot/

```
and we see what it will take.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

