---
title: "All Ubuntu based distros seem to have the battery monitor broken."
date: 2022-05-16
forum: General Help
---

### Post by Gordonbp531 on 2022-05-16
I have a 3 year old Lenovo Thinkpad, which has been fine in all areas using many different Ubuntu based distros up until the release of Ubuntu 22.04.
After I upgraded to 22.04, the battery monitor tells me the battery is not charging when plugged in.
It shows the battery charging on the log-in splash screen, but as soon as I log in, the display changes to not charging.
has anyone else noticed this?

---

### Post by #&amp;thj^% on 2022-05-16
Not sure I can help here, but what dose this return:
```
upower -i /org/freedesktop/UPower/devices/battery_BAT0  
```
Ok in point I'm interested in these values:
```
energy:              58.29 Wh
    energy-empty:        0 Wh
    energy-full:         58.3 Wh
    energy-full-design:  60 Wh
    energy-rate:         3.33 W
    voltage:             17.294 V
    charge-cycles:       9

```

---

### Post by Gordonbp531 on 2022-05-16
```
 native-path:          (null)
  power supply:         no
  updated:              Thu 01 Jan 1970 01:00:00 BST (1652732222 seconds ago)
  has history:          no
  has statistics:       no
  unknown
    warning-level:       unknown
    battery-level:       unknown
    icon-name:          '(null)'

```

---

### Post by #&amp;thj^% on 2022-05-16
You should file a bug-report on this.
Will it show nicer on a older kernel?

---

