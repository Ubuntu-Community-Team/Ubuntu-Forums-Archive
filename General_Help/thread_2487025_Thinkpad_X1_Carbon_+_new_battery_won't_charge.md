---
title: "Thinkpad X1 Carbon + new battery won't charge"
date: 2023-05-20
forum: General Help
---

### Post by kurt18947 on 2023-05-20
Machine is a Thinkpad X1 Carbon gen 3. I bought it off Ebay. The battery was getting tired so I looked at Ebay offerings where I've had good luck in the past. No, the battery may not be as good as a recently manufactured Lenovo battery but it'll do. The battery came fully charged which may not be the greatest from what I understand but it works and has several hours life. The problem came after I'd been using the machine for 15 minutes or so on battery. The battery symbol in the upper right corner was white and wasn't showing charge. When it got down to 90% and still no charge, I knew I had a problem. 

I have this machine set up dual boot with Windows 10 so I tried that before I contacted the seller. In Windows the battery showed charging just as it should. I shut down Windows and booted back into Ubuntu 22.04. This time the battery symbol was green and showing the little lightning bolt indicating charge. I gather from this that this machine requires a start in Windows in order to enable charging of a new battery. Thinkpads are generally Linux friendly but does anyone have a clue about why a boot in Windows is required for a new battery? The battery does seem to charge as expected in Ubuntu after it has been booted once in Windows. This sort of thing is why I recommend to people that want to rip out Windows to keep it in a small partition. It would be nice to not require a boot in Windows but I don't have a clue what to change in Ubuntu to enable charging of a new battery. Does anyone? Or is this just a peculiarity of 3rd party batteries?

---

### Post by #&amp;thj^% on 2023-05-20
Mine is a 7th Gen X1, and in the bios there is a setting for service battery, that should have ticked before the replacement was plugged in. (Not sure if you did that before)
Then you should not have any charging problems.
EDIT I forgot to add checks via "cli"
```
cat /sys/class/power_supply/BAT0/capacity
56

```
the 56 represents percent charged.
More info with:
```
find /sys/class/power_supply/BAT0/ -type f | xargs -tn1 cat
cat /sys/class/power_supply/BAT0/uevent
POWER_SUPPLY_NAME=BAT0
POWER_SUPPLY_TYPE=Battery
POWER_SUPPLY_STATUS=Not charging
POWER_SUPPLY_PRESENT=1
POWER_SUPPLY_TECHNOLOGY=Li-poly
POWER_SUPPLY_CYCLE_COUNT=25
POWER_SUPPLY_VOLTAGE_MIN_DESIGN=15400000
POWER_SUPPLY_VOLTAGE_NOW=15467000
POWER_SUPPLY_POWER_NOW=0
POWER_SUPPLY_ENERGY_FULL_DESIGN=60000000
POWER_SUPPLY_ENERGY_FULL=56570000
POWER_SUPPLY_ENERGY_NOW=31680000
POWER_SUPPLY_CAPACITY=56
POWER_SUPPLY_CAPACITY_LEVEL=Normal
POWER_SUPPLY_MODEL_NAME=L19C4PC0
POWER_SUPPLY_MANUFACTURER=Celxpert
POWER_SUPPLY_SERIAL_NUMBER= 1532
cat /sys/class/power_supply/BAT0/serial_number
 1532
cat /sys/class/power_supply/BAT0/technology
Li-poly
cat /sys/class/power_supply/BAT0/power_now
0
cat /sys/class/power_supply/BAT0/present
1
cat /sys/class/power_supply/BAT0/power/runtime_active_time
0
cat /sys/class/power_supply/BAT0/power/runtime_status
unsupported
cat /sys/class/power_supply/BAT0/power/autosuspend_delay_ms
cat: /sys/class/power_supply/BAT0/power/autosuspend_delay_ms: Input/output error
cat /sys/class/power_supply/BAT0/power/runtime_suspended_time
0
cat /sys/class/power_supply/BAT0/power/control
auto
cat /sys/class/power_supply/BAT0/hwmon4/uevent
cat /sys/class/power_supply/BAT0/hwmon4/in0_input
15467
cat /sys/class/power_supply/BAT0/hwmon4/power/runtime_active_time
0
cat /sys/class/power_supply/BAT0/hwmon4/power/runtime_status
unsupported
cat /sys/class/power_supply/BAT0/hwmon4/power/autosuspend_delay_ms
cat: /sys/class/power_supply/BAT0/hwmon4/power/autosuspend_delay_ms: Input/output error
cat /sys/class/power_supply/BAT0/hwmon4/power/runtime_suspended_time
0
cat /sys/class/power_supply/BAT0/hwmon4/power/control
auto
cat /sys/class/power_supply/BAT0/hwmon4/name
BAT0
cat /sys/class/power_supply/BAT0/manufacturer
Celxpert
cat /sys/class/power_supply/BAT0/energy_now
31680000
cat /sys/class/power_supply/BAT0/type
Battery
cat /sys/class/power_supply/BAT0/capacity
56
cat /sys/class/power_supply/BAT0/cycle_count
25
cat /sys/class/power_supply/BAT0/voltage_now
15467000
cat /sys/class/power_supply/BAT0/status
Not charging
cat /sys/class/power_supply/BAT0/alarm
0
cat /sys/class/power_supply/BAT0/model_name
L19C4PC0
cat /sys/class/power_supply/BAT0/voltage_min_design
15400000
cat /sys/class/power_supply/BAT0/capacity_level
Normal
cat /sys/class/power_supply/BAT0/energy_full_design
60000000
cat /sys/class/power_supply/BAT0/energy_full
56570000


```
This machine is a Lenovo as well.

---

