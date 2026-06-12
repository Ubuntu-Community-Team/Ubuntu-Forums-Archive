---
title: "upower won't hibernate - ignore other devices"
date: 2022-03-29
forum: General Help
---

### Post by atomz4peace on 2022-03-29
Hi,

I'm trying to test if upower can really hibernate my laptop on a certain power percentage but it's not working. My upower.conf says:

UsePercentageForPolicy=true
PercentageLow=51
PercentageCritical=50
PercentageAction=50
CriticalPowerAction=HybridSleep

My goal is to hibernate at 50%, then I already have wake on lan set so when power comes on in the house, the wol will be sent from another system.

But when my battery goes below 50%, nothing happens. upower -d shows this. I'm recharging now. 

> Device: /org/freedesktop/UPower/devices/line_power_AC
  native-path:          AC
  power supply:         yes
  updated:              Tue 29 Mar 2022 10:18:15 AM PDT (1479 seconds ago)
  has history:          no
  has statistics:       no
  line-power
    warning-level:       none
    online:              yes
    icon-name:          'ac-adapter-symbolic'


Device: /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               Panasonic
  model:                42T4620
  serial:               896
  power supply:         yes
  updated:              Tue 29 Mar 2022 10:42:15 AM PDT (39 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               charging
    warning-level:       none
    energy:              18.29 Wh
    energy-empty:        0 Wh
    energy-full:         57.95 Wh
    energy-full-design:  84.24 Wh
    energy-rate:         42.046 W
    voltage:             12.298 V
    time to full:        56.6 minutes
    percentage:          31%
    capacity:            68.7915%
    technology:          lithium-ion
    icon-name:          'battery-good-charging-symbolic'
  History (charge):
    1648575735  31.000  charging
  History (rate):
    1648575735  42.046  charging


Device: /org/freedesktop/UPower/devices/ups_hiddev0
  native-path:          /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/usbmisc/hiddev0
  vendor:               CPS
  model:                UPS CP1000AVRLCD
  serial:               BFC7101.4K1
  power supply:         yes
  updated:              Tue 29 Mar 2022 10:42:45 AM PDT (9 seconds ago)
  has history:          yes
  has statistics:       yes
  ups
    present:             yes
    state:               fully-charged
    warning-level:       none
    time to empty:       54.5 minutes
    percentage:          100%
    icon-name:          'battery-full-charged-symbolic'


Device: /org/freedesktop/UPower/devices/DisplayDevice
  power supply:         yes
  updated:              Tue 29 Mar 2022 10:41:45 AM PDT (69 seconds ago)
  has history:          no
  has statistics:       no
  ups
    present:             yes
    state:               fully-charged
    warning-level:       none
    time to empty:       54.5 minutes
    percentage:          100%
    icon-name:          'battery-full-charged-symbolic'


Daemon:
  daemon-version:  0.99.11
  on-battery:      no
  lid-is-closed:   no
  lid-is-present:  no
  critical-action: HybridSleep

I do have a UPS but I want to ignore that. I have no idea why the displaydevice shows as a power or what it even is. The laptop T500 has only one battery.

I'm wondering if upower sees multiple batteries and/or the UPS so never suspends until it runs out of power and just crashes. 

upower --monitor-detail

shows the power events coming from BAT0, but also shows events from the UPS saying 100%. 

Any idea why it will not hibernate and/or how to ignore the other devices and just focus on BAT0? I'm sure I can write my own custom script to poll and suspend but can't upower just do it as well?

Then of course, when power comes back and the battery is 20% but charging, how do I ensure it won't sleep again? :-)


Thank you!

---

### Post by GhX6GZMB on 2022-03-29
As you're posting here, I assume you are running some variant of Ubuntu. Which one seems to be a big secret.

Hibernate is per default disabled in (x)ubuntu, apparently for security reasons.

Enabling it takes a bit more than modifying upower. Attached is a recipe I wrote after going through that process myself.
Note that going through those steps will only enable Hibernate. The 50% etc. you'll have to work out yourself.
Newer (x)ubuntu installations do not have a swap-partition, but just a swap-file. I've never been able to get Hibernate to work with just a swap-file, and most feedbacks I read say the same.
A swap-partition works every time.

Cheers.

---

### Post by atomz4peace on 2022-03-29
Sorry about that. ubuntu 20.04.4 LTS. hibernate is working fine on a swap file for me via cmd line. I had to go through a few steps to enable like this [https://www.linuxuprising.com/2021/08/how-to-enable-hibernation-on-ubuntu.html](https://www.linuxuprising.com/2021/08/how-to-enable-hibernation-on-ubuntu.html).

That's all good. I can hibernate via terminal, then send WOL package and it all comes back. Just curious if upower can somehow ignore the other devices or if I have to go custom with a polling script like we see here: [https://unix.stackexchange.com/questions/84437/how-do-i-make-my-laptop-sleep-when-it-reaches-some-low-battery-threshold/289129#289129](https://unix.stackexchange.com/questions/84437/how-do-i-make-my-laptop-sleep-when-it-reaches-some-low-battery-threshold/289129#289129)

Anyone else worked with upower?

---

