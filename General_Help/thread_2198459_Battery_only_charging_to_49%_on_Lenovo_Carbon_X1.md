---
title: "Battery only charging to 49% on Lenovo Carbon X1"
date: 2014-01-08
forum: General Help
---

### Post by adamgrushcow on 2014-01-08
Hey everyone,

I've ran into a little issue with my new Lenovo Carbon X1. It had windows 8 preinstalled on it, but I have since switched over to Ubuntu because I can't stand windows. My issue is my battery won't charge beyond 49%. I have looked around and realized I must have set my computer up under windows to optimize battery (protecting the battery long term). Unfortunately I can't change it back now, but supposedly there is a lenovo dependency package that is supposed to alleviate these issues. Unfortunately it isn't compatible with ubuntu....

Does anyone have a work around or a way to fix the battery charge?

Thanks in advance

---

### Post by sj_ on 2014-02-27
I have the same issue with my X1 and Linux Mint Debian 201403 RC. Does anybody have the solution ?

---

### Post by sj_ on 2014-05-14
Finally I've managed to fix that. You need to install TLP as it mentioned here [http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html#installation](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html#installation)
then just run

> sudo tlp fullcharge to see if it starts charging
then you have to setup

> /etc/default/tlp file with your settings

uncomment this 2 lines and enter your values

# Battery charge thresholds (ThinkPad only, tp-smapi or acpi-call kernel module 
required)
# Charging starts when the remaining capacity falls below the START_CHARGE_TRESH
# value and stops when exceeding the STOP_CHARGE_TRESH value.
# Main battery (values in %)
> START_CHARGE_THRESH_BAT0=75
STOP_CHARGE_THRESH_BAT0=90

---

