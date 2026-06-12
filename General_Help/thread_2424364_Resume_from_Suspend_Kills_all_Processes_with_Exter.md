---
title: "Resume from Suspend Kills all Processes with External Monitor"
date: 2019-08-07
forum: General Help
---

### Post by jpelly on 2019-08-07
[COLOR=#242729][FONT=Arial][FONT=inherit]When I resume from a suspend with my external monitor connected to my Thinkpad T460p, all previously running applications are gone and I'm presented with a fresh, blank desktop.[/FONT]
[FONT=inherit]First I'm presented with a "standard res" login screen. I log in, the laptop screen flashes multiple times, and I see the desktop on the laptop and external monitor for a second. Then both screens flash again and I'm presented with a "high res" login screen and have to re-enter my password.[/FONT]
[FONT=inherit]This only happens when the external monitor is connected; when it's not connected a resume restores all apps as it should.[/FONT]
[FONT=inherit]This is new behavior. Previously the external monitor wouldn't wake up on resume automatically (I had to manually turn it off / on). Only things I can think of that I did recently was played around with xrandr (to get the monitor to come on via a command) and installed some tlp and associated power management tools.[/FONT]
[FONT=inherit]I'm no expert, but it looks like there's a crash/restart of an X/Wayland session? It's been a while since I've used Linux / X.[/FONT]
[FONT=inherit]lsb_release -a No LSB modules are available. Distributor ID: Ubuntu Description: Ubuntu 18.04.2 LTS Release: 18.04 Codename: bionic[/FONT]


[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][/FONT][/COLOR]

---

### Post by jpelly on 2019-09-06
Nothing? Has no one experienced this?

---

