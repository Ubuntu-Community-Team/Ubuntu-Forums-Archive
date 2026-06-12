---
title: "Battery reading incorrect."
date: 2017-01-21
forum: General Help
---

### Post by impelus on 2017-01-21
[FONT=verdana]So I just installed Lubuntu 16.10 on an old Acer laptop. I got it working, but the battery status is reporting incorrectly. It shows 100% charge then soon enough drops down to 7% battery and then very soon after system hibernates because battery is being reported as too low.. I figured just the battery was bad, but looking into the battery status, it seems the energy level is incorrect.[/FONT]
[FONT=verdana]See below it shows a battery design of 130.754 Wh, but a current and full energy of 4200. The battery itself says it is 2000mah and apparently you can buy 4400mah batteries for this laptop.

When it drops to 7%, I check power again to see it is around 125wh which means the battery is probably at 96%, but since it is calculating that 125 against the 4200 instead of the 130, it is showing a critically low battery (3%).   

I'm unable to use this laptop on battery at all until I get this fixed. 

[/FONT]
[FONT=verdana]Thanks in advance for any help here.

Acer Aspire 3613WLCi. 
[/FONT]
```
$ upower -i /org/freedesktop/UPower/devices/battery_BAT0
native-path:          BAT0
vendor:               Acer
model:                Bat 4Cell
serial:               4368
power supply:         yes
updated:              Fri 20 Jan 2017 11:58:35 PM CST (103 seconds ago)
has history:          yes
has statistics:       yes
battery
present:             yes
rechargeable:        yes
state:               fully-charged
warning-level:       none
energy:              4273.76 Wh
energy-empty:        0 Wh
energy-full:         4274.15 Wh
energy-full-design:  130.754 Wh
energy-rate:         0.568279 W
voltage:             16.68 V
percentage:          99%
capacity:            100%
technology:          lithium-ion
icon-name:          'battery-full-charged-symbolic'
History (rate):
1484978315  0.568   fully-charged
```

---

