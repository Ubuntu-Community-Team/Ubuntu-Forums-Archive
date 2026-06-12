---
title: "Problems with Macbook Air fans, they wont stop going full blast"
date: 2015-03-24
forum: General Help
---

### Post by whatamidoingahh on 2015-03-24
[COLOR=#000000]I recently installed Ubuntu 14.04.2 and I am having some issues with the fans. Shortly after start up they ramp up to what sounds like full speed. I installed macfanctld when I run [/COLOR]

[COLOR=#000000]macfanctld -f this is what I get[/COLOR]

[COLOR=#000000]Running in foreground, log to stdout.[/COLOR]
[COLOR=#000000]Using parameters:[/COLOR]
[COLOR=#000000]temp_avg_floor: 45[/COLOR]
[COLOR=#000000]temp_avg_ceiling: 55[/COLOR]
[COLOR=#000000]temp_TC0P_floor: 50[/COLOR]
[COLOR=#000000]temp_TC0P_ceiling: 58[/COLOR]
[COLOR=#000000]temp_TG0P_floor: 50[/COLOR]
[COLOR=#000000]temp_TG0P_ceiling: 58[/COLOR]
[COLOR=#000000]fan_min: 2000[/COLOR]
[COLOR=#000000]log_level: 0[/COLOR]
[COLOR=#000000]Found applesmc at /sys/devices/platform/applesmc.768[/COLOR]
[COLOR=#000000]Found 1 fan.[/COLOR]
[COLOR=#000000]Found 33 sensors:[/COLOR]
[COLOR=#000000]1: TB0T - Battery TS_MAX Temp [/COLOR]
[COLOR=#000000]2: TB1T - Battery TS1 Temp [/COLOR]
[COLOR=#000000]3: TB2T - Battery TS2 Temp [/COLOR]
[COLOR=#000000]4: TBXT - ? [/COLOR]
[COLOR=#000000]5: TC0E - ? [/COLOR]
[COLOR=#000000]6: TC0F - ? [/COLOR]
[COLOR=#000000]7: TC0P - CPU 0 Proximity Temp [/COLOR]
[COLOR=#000000]8: TC1C - ? [/COLOR]
[COLOR=#000000]9: TC2C - ? [/COLOR]
[COLOR=#000000]10: TCGC - ? [/COLOR]
[COLOR=#000000]11: TCHP - ? [/COLOR]
[COLOR=#000000]12: TCMX - ? [/COLOR]
[COLOR=#000000]13: TCSA - ? [/COLOR]
[COLOR=#000000]14: TCXC - ? [/COLOR]
[COLOR=#000000]15: TH0A - ? [/COLOR]
[COLOR=#000000]16: TH0B - ? [/COLOR]
[COLOR=#000000]17: TH0C - ? [/COLOR]
[COLOR=#000000]18: TH0F - ? [/COLOR]
[COLOR=#000000]19: TH0R - ? [/COLOR]
[COLOR=#000000]20: TH0V - ? [/COLOR]
[COLOR=#000000]21: TH0a - ? [/COLOR]
[COLOR=#000000]22: TH0b - ? [/COLOR]
[COLOR=#000000]23: TH0c - ? [/COLOR]
[COLOR=#000000]24: THSP - ? [/COLOR]
[COLOR=#000000]25: TM0P - ? [/COLOR]
[COLOR=#000000]26: TPCD - ? [/COLOR]
[COLOR=#000000]27: TS2P - ? [/COLOR]
[COLOR=#000000]28: TW0P - ? [/COLOR]
[COLOR=#000000]29: Ta0P - ? [/COLOR]
[COLOR=#000000]30: Th1H - ? [/COLOR]
[COLOR=#000000]31: Tm0P - Battery Charger Proximity Temp [/COLOR]
[COLOR=#000000]32: Ts0P - Palm Rest Temp [/COLOR]
[COLOR=#000000]33: Ts0S - ? [/COLOR]
[COLOR=#000000]Error: Can't open /sys/devices/platform/applesmc.768/fan1_min[/COLOR]
[COLOR=#000000]Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual[/COLOR]
[COLOR=#000000]Error: Can't open /sys/devices/platform/applesmc.768/fan1_min[/COLOR]
[COLOR=#000000]Error: Can't open /sys/devices/platform/applesmc.768/fan1_manual[/COLOR]

[COLOR=#000000]The last 2 errors repeating. Is there a fix to this or a way to control the fans?[/COLOR]

---

### Post by whatamidoingahh on 2015-03-25
What I did to resolve this issue was reinstalling Ubuntu but I used an older version, 14.04. I tried 14.10 but after installing that my laptop would only boot into mac recovery mode. I selected the startup disk to boot straight into OS X Mavericks. I deleted the Ubuntu partitions, deleted rEFind. Recreated the Ubuntu partitions and went through a normal installation. Reinstalled rEFind in OS X and loaded into Ubuntu with no fan issues.

---

