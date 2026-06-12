---
title: "Battery detected but not charging"
date: 2024-02-12
forum: General Help
---

### Post by luncaaa on 2024-02-12
Hello!

I have an acer aspire V5 running lubuntu and I recently bought a new battery for it. At first, it worked fine but now, after some months of not using the laptop, it is no longer charging. This is the information I get when running **upower -i /org/freedesktop/UPower/devices/battery_BAT1**
```
  native-path:          BAT1  
  vendor:               SANYO
  model:                AL12B32
  serial:               16911
  power supply:         yes
  updated:              lun 12 feb 2024 19:24:55 (93 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               pending-charge
    warning-level:       none
    energy:              0 Wh
    energy-empty:        0 Wh
    energy-full:         48,2073 Wh
    energy-full-design:  48,84 Wh
    energy-rate:         0 W
    voltage:             8,787 V
    charge-cycles:       N/A
    percentage:          0%
    capacity:            98,7045%
    technology:          lithium-ion
    icon-name:          'battery-caution-charging-symbolic'
```

I've tried running **busctl call --system org.freedesktop.UPower /org/freedesktop/UPower/devices/battery_BAT1 org.freedesktop.UPower.Device Refresh, **but it didn't work. Similar posts suggest removing the charger, starting the laptop and connecting the charger again, but I cannot do that as the battery is completely empty. What can I do?

---

### Post by Autodave on 2024-02-12
Did you buy the battery from Acer or somewhere else?  I have had very poor results with after-market batteries.

---

### Post by luncaaa on 2024-02-13
From somewhere else, it's a really old laptop... But I don't understand why the battery is detected but it doesn't charge when it even says that it can hold charge (not like it's maximum charge was 0W because it broke or something)

---

### Post by Autodave on 2024-02-13
I understand your frustration.  Been there, done that.  Still have the scars.

Assuming that you do not have any powered USB hubs in use, I would tend to believe that the battery is junk.

Is this battery easily removable?  If so, you can try removing it and every cord from the laptop.  Let it sit like that for at least 10 minutes.  Put the battery back in and plug the charger into the laptop.  Do not power up the laptop.  Note your charging lamp on the laptop.....does it show that it is charging?  If so, leave it like that for an hour at least and see if the light finally changes to show that the battery is fully charged.  After at least an hour, power the laptop back on and see what it says about the battery.

---

