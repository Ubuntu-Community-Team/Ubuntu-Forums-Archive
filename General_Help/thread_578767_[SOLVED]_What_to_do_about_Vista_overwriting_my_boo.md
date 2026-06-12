---
title: "[SOLVED] What to do about Vista overwriting my boot loader (GRUB)?"
date: 2007-10-17
forum: General Help
---

### Post by tj.milligan on 2007-10-17
Here's the situation. I have a triple boot: Edgy, XP (DX9 gaming) and Vista (DX10 gaming). Problem is, my vista install is beyond repair (rescue allows me to log in, but the desktop never appears) and I plan to reinstall it. I know this will overwrite my GRUB boot loader. My question is, after I re-install vista (at which point the install process will overwrite GRUB) how will I be able to get my GRUB back and thus be able to boot into Edgy?

BTW, the current boot is as follows:
GRUB: Edgy, "Windows". If I select "Windows", the Vista Boot Loader comes up with WinXP and Vista.

Also, my HDD is partitioned as follows:

hda1 - XP
hda2 - Vista
hda5 - ext3 /
hda6 - linux-swap
hda7 - ext3 /home

---

### Post by Pumalite on 2007-10-17
Reinstall Grub after you install Vista:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Jose Catre-Vandis on 2007-10-17
Boot with Live CD

Open a terminal

```
sudo grub
```
get's you into grub mode
```
find /boot/grub/stage1
```
this returns a location, note it down
```
root (hd0,0)
```
replace whatever is in the brackets with what was returned by the find command
(assumes you want to overwrite master boot record)
```
setup (hd0)
```
installs grub to mbr
```
quit
```

reboot and grub should be back

---

### Post by tj.milligan on 2007-10-17
Great! Thanks guys. I'll assume problem solved and give this a go.

---

### Post by Jose Catre-Vandis on 2007-10-20
If it is solved, please mark thread as solved :)

---

