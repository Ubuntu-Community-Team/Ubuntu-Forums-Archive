---
title: "proper way to run a script on switch to battery/AC in Ubuntu 20.04?"
date: 2020-12-20
forum: General Help
---

### Post by Fallen Guru on 2020-12-20
Subject pretty much says it all, I'd like to run a custom script when the machine switches to battery / to AC, what's the cleanest ("most Ubuntu") way to do this?

Obviously I want something event-based (no polling). Systemd doesn't handle battery/AC events, I checked.

---

### Post by #&amp;thj^% on 2020-12-20
I have always found These basic steps are useful:

**Monitor your system:**
```

sudo udevadm monitor
```

This tells you what udev "sees".

With this running, plug in the power supply, and see what udevadm tells you. Unplug it, again: see what udevadm tells you. It will probably make no sense yet, but that's ok; you know how to monitor udev now, and that's useful.

and do this:
```

sudo udevadm info --path=/sys/class/power_supply/ac
```

or
```

sudo udevadm info --path=/sys/class/power_supply/battery
```

which gives you information about the AC and BATTERY systems. Like this:
```

P: /devices/platform/sunxi-i2c.0/i2c-0/0-0034/axp20-supplyer.28/power_supply/battery
E: DEVPATH=/devices/platform/sunxi-i2c.0/i2c-0/0-0034/axp20-supplyer.28/power_supply/battery
E: POWER_SUPPLY_CAPACITY=100
E: POWER_SUPPLY_CURRENT_NOW=0
E: POWER_SUPPLY_ENERGY_FULL_DESIGN=3200
E: POWER_SUPPLY_HEALTH=Good
E: POWER_SUPPLY_MODEL_NAME=battery
E: POWER_SUPPLY_NAME=battery
E: POWER_SUPPLY_ONLINE=0
E: POWER_SUPPLY_PRESENT=0
E: POWER_SUPPLY_STATUS=Full
E: POWER_SUPPLY_TECHNOLOGY=Li-ion
E: POWER_SUPPLY_TEMP=300
E: POWER_SUPPLY_VOLTAGE_MAX_DESIGN=4200000
E: POWER_SUPPLY_VOLTAGE_MIN_DESIGN=3300
E: POWER_SUPPLY_VOLTAGE_NOW=0
E: SUBSYSTEM=power_supply
```

[B]The E: lines are environment attributes you can use to write a udev rule.
[/B]
Write a basic udev rule (I usually just write one to create a log entry somewhere on my drive when the even happens; that way, I know I am triggering something. Then I go back and make the script useful.)

For example: SUBSYSTEM=="power_supply", ENV{POWER_SUPPLY_STATUS}=="Charging", RUN+="/path/to/some/script.sh"

or you might use POWER_SUPPLY_PRESENT=1 ... you'll have to experiment based on what values you see on your computer.

Place this udev script in /etc/udev/rules.d (a name like 80.power.rules would be conventional) and restart your computer. Technically you can just restart udev but I find that unreliable.

See if your script gets triggered when your AC is plugged in.

Refine your udev rule and the script it triggers.

_There is much more to udev, so dive in!_ :)

---

