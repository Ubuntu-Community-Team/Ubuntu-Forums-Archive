---
title: "Ubuntu 24.04 Laptop, not shutting down automatically at low battery."
date: 2024-07-21
forum: General Help
---

### Post by swantayle on 2024-07-21
Hey, Guys.
I'm running Ubuntu 24.04, and I'm wondering if there is a setting i can adjust to automatically shutdown at a certain battery percentage.

i bought a cheap battery off of Temu and every time the laptop runs it to 0 i have to leave it plugged in for 8 hours for the battery to be recognized and start charging properly and the machine wont turn on even when plugged in in the interim, so I'm fairly desperate to avoid this.

---

### Post by swantayle on 2024-07-21
i think i found a solution to this based on an answer for an older version.
[https://askubuntu.com/questions/1107397/no-low-battery-notification-on-ubuntu-18-04](https://askubuntu.com/questions/1107397/no-low-battery-notification-on-ubuntu-18-04)
i edited the /etc/UPower/UPower.conf file and adjust the the percentage levels under the UsePercentageForPolicy Section

> UsePercentageForPolicy=true

# When UsePercentageForPolicy is true, the levels at which UPower will
# consider the battery low, critical, or take action for the critical
# battery level.
#
# This will also be used for batteries which don't have time information
# such as that of peripherals.
#
# If any value is invalid, or not in descending order, the defaults
# will be used.
#
# Defaults:
# PercentageLow=20
# PercentageCritical=5
# PercentageAction=2
PercentageLow=20
PercentageCritical=15
PercentageAction=10

&

> # The action to take when "TimeAction" or "PercentageAction" above has been
# reached for the batteries (UPS or laptop batteries) supplying the computer

> CriticalPowerAction=PowerOff

Follow with: sudo systemctl restart upower

---

### Post by swantayle on 2024-07-21
and just confirming after testing this worked as expected :)

---

