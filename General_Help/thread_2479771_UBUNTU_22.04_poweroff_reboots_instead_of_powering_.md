---
title: "UBUNTU 22.04: poweroff reboots instead of powering off"
date: 2022-10-06
forum: General Help
---

### Post by frederiz on 2022-10-06
Hi, 

since I've moved to 22.04 (reinstall from scratch of 20.04 and 18.04 NUCs 10i7) nor **sudo poweroff **nor **sudo shutdown -P now **command lines are working as expected THEY ARE REBBOTING THE NUC RATHER THAN SHUTTING THEM OFF
the only way to switch the 2  NUC 10 running Desktop and Server version of Ubuntu 22.04 is the GUI (right top button of the window manager) or to unplug powercord.
Please can you help me to fix this issue or report to Canonical the bug.

---

### Post by frederiz on 2022-10-11
Partially solved: Last fix (apt update) fix shutdown -P now behaviour and now it is working as expected: The system shtuddown and does not reboot. BUT poweroff command still still reboots instead of powering off the system. :(

---

### Post by frederiz on 2022-10-11
Hi, 

Few days ago I've posted here on 2 commands that did not run as expected: 
[LIST]
[*]**sudo shutdown -P now **
[*]**sudo poweroff**
[/LIST]
Last kernel update fixed 50% as **shutdown -P now** is currently doing the job as expected, 
BUT **poweroff** doesn't ==> It continues to reboot the system instead of powering it off.:(

Second BUG **update-grub** does not update configuration as expected as **GRUB_TIMEOUT=10 **set into **/etc/default/grub** is not implemented.

Please, as my computers are headless NUCs (without display, kbd, mouse) it doesn't worth to wait 30 seconds before to boot. 5 or max 10 are long enough!

---

### Post by ajgreeny on 2022-10-11
I  am not certain because I can't remember when I last shutdown using such a command, but from **man poweroff** it looks as if you may need command ***poweroff -p*** to get a complete shutdown/poweroff.

---

### Post by ajgreeny on 2022-10-11
Threads merged and moved to **General**!

Please do not create duplicate (or very nearly duplicate) threads as it is very confusing for other users

---

### Post by frederiz on 2022-10-14
Hi -p option is available for halt command, 

halt -p is equivalent to poweroff, both are poing to poweroff state ( when command are right coded).

---

