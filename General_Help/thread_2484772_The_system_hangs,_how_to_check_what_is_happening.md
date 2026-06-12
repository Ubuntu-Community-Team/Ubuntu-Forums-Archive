---
title: "The system hangs, how to check what is happening?"
date: 2023-03-09
forum: General Help
---

### Post by py-ohayo on 2023-03-09
Hello, 
Since few days my Ubuntu 22.04 hangs quite frequently, so I need to reboot.
Another indication that something is going wrong - the mouse suddenly starts moving jerkily.
How to check system integrity ?
Thanks.

---

### Post by py-ohayo on 2023-03-09
Sometimes the system crashes and restarts by itself.

---

### Post by Autodave on 2023-03-09
Sounds more like a hardware problem than an OS problem.  I would start with checking the power supply and then moving on to the RAM.  IF you are using ANY USB hubs, start by disconnecting all of them and seeing if that takes care of your problem.

---

### Post by py-ohayo on 2023-03-09
I checked power supply. Here it is:
```
pavel@MISSURI:~$ upower -d
Device: /org/freedesktop/UPower/devices/line_power_ADP0
  native-path:          ADP0
  power supply:         yes
  updated:              jeu. 09 mars 2023 16:35:20 (3909 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    warning-level:       none
    online:              yes
    icon-name:          'ac-adapter-symbolic'

Device: /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               SMP
  model:                L17M3PB1
  serial:               1242
  power supply:         yes
  updated:              jeu. 09 mars 2023 17:39:21 (68 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               pending-charge
    warning-level:       none
    energy:              14,09 Wh
    energy-empty:        0 Wh
    energy-full:         44,47 Wh
    energy-full-design:  45 Wh
    energy-rate:         2,897 W
    voltage:             11,361 V
    charge-cycles:       N/A
    percentage:          31%
    capacity:            98,8222%
    technology:          lithium-polymer
    icon-name:          'battery-good-charging-symbolic'

Device: /org/freedesktop/UPower/devices/DisplayDevice
  power supply:         yes
  updated:              jeu. 09 mars 2023 16:35:21 (3908 seconds ago)
  has history:          no
  has statistics:       no
  battery
    present:             yes
    state:               pending-charge
    warning-level:       none
    energy:              14,09 Wh
    energy-full:         44,47 Wh
    energy-rate:         2,897 W
    charge-cycles:       N/A
    percentage:          31%
    icon-name:          'battery-good-charging-symbolic'

Daemon:
  daemon-version:  0.99.17
  on-battery:      no
  lid-is-closed:   no
  lid-is-present:  yes
  critical-action: HybridSleep
pavel@MISSURI:~$
```

Seems Ok. How to check RAM ?

---

### Post by py-ohayo on 2023-03-09
Well I have battery in pending state, but it is in this state since 3 ... 4 months, but these new problems appeared recently.
> pavel@MISSURI:~$ upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               SMP
  model:                L17M3PB1
  serial:               1242
  power supply:         yes
  updated:              jeu. 09 mars 2023 17:47:21 (30 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               pending-charge
    warning-level:       none
    energy:              14,09 Wh
    energy-empty:        0 Wh
    energy-full:         44,47 Wh
    energy-full-design:  45 Wh
    energy-rate:         2,897 W
    voltage:             11,361 V
    charge-cycles:       N/A
    percentage:          31%
    capacity:            98,8222%
    technology:          lithium-polymer
    icon-name:          'battery-good-charging-symbolic'

---

### Post by dragonfly41 on 2023-03-09
> [COLOR=#000000]Another indication that something is going wrong - the mouse suddenly starts moving jerkily.[/COLOR][COLOR=#000000]

I am also experiencing quirks. in my case on clicking an app in left dock panel the apps is dragged to desktop and when i click esc it resets the drag but mouse pointer moves aroundbut does not click through.

A few tips from my recent hunting for a solution.
when you experience a hang, instead of rebooting (as I too used to do, which is lengthy) try hitting Ctrl+Alt+F1 to simply reenter your session.

Also try Gnome Tweaks to change theme.

I am also following ths dated thread ..

[/COLOR][https://bugs.launchpad.net/ubuntu/+source/rapidsvn/+bug/402892](https://bugs.launchpad.net/ubuntu/+source/rapidsvn/+bug/402892)
to look for clues. Gnome related.

---

### Post by py-ohayo on 2023-03-09
The problem seems solved: I used looped python code for web-scarping.
I have observed that over time the swap volume is constantly increasing.
I think the system crashes when the swap reaches its maximum, 2GB in my case.
Here is a snapshot of the **htop** command shortly before the system crashed.
I changed the resource management in the Python code, and now it looks OK.
[IMG]https://i.postimg.cc/MZ9FSrfJ/20230309-183626.jpg[/IMG]

---

### Post by mIk3_08 on 2023-03-09
> **py-ohayo said:**
> The problem seems solved: 

On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

