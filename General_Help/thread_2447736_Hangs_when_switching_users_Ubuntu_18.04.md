---
title: "Hangs when switching users Ubuntu 18.04"
date: 2020-07-24
forum: General Help
---

### Post by james_creasy2 on 2020-07-24
[COLOR=#242729][FONT=Arial][FONT=inherit]Repro:[/FONT]

[LIST=1]
[*]Login to user 1
[*]Let computer go to sleep
[*]Use the power button UI menu to choose "Switch User"
[*]Select user 2
[*]Type password
[*]Computer hangs
[/LIST]
[FONT=inherit]
It often (or maybe always) shows terminal output and stops at "Thunderbolt" something. Requires power off and reboot to proceed.[/FONT]
[FONT=inherit]
I could not search up any recent results for this, only one for Ubuntu 7 and one for Ubuntu 11, neither of which seem to apply to me.[/FONT]
[FONT=inherit]
Any help for how to diagnose is appreciated[/FONT]
[FONT=inherit]
Ubuntu 18.04 
Intel NUC 
Dell 2407WFPb connected via DVI 
Logitech M510 with dongle 
Ethernet (wifi off) 
USB keyboard 
USB camera[/FONT]

[/FONT][/COLOR]

---

### Post by collisiondomain on 2020-07-29
Someone on Launchpad ([https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1866416](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1866416)) seems to have found a workaround. Does that work for you?

---

