---
title: "Bluetooth dongle that works"
date: 2018-07-31
forum: General Help
---

### Post by Jason_Hunter on 2018-07-31
I'm going mental. 

Whenever I leave my computer for 15 minutes, my bluetooth keyboard disconnects and it spends like 30 seconds to reconnect every time

Why?

Any dongle that works without this hassle?

---

### Post by DuckHook on 2018-07-31
[LIST=1]
[*]What flavour and version are you using? Is it Ubuntu 18.04?
[*]Is it a desktop computer using a USB bluetooth dongle?
[*]Do you have auto suspend turned on and set to 15 minutes?
[*]If so, have you tried turning this off?
[/LIST]
The issue is unlikely to be with your dongle, but with the fact that power is being turned off to your USB port after 15 minutes due to auto suspend. Upon resume, it takes 30 seconds for your dongle to reestablish handshake and communication with your keyboard. If you are using a laptop running on battery, turning off auto suspend may not be what you want. In that case, you can try the following methods to keep feeding power to only that one device/USB port:

[https://askubuntu.com/questions/185274/how-can-i-disable-usb-autosuspend-for-a-specific-device](https://askubuntu.com/questions/185274/how-can-i-disable-usb-autosuspend-for-a-specific-device)
[https://hamwaves.com/usb.autosuspend/en/index.html](https://hamwaves.com/usb.autosuspend/en/index.html)

Note that turning off any sort of auto suspend component on a laptop risks rapidly burning up your battery charge and losing data.

---

### Post by Jason_Hunter on 2018-08-01
1. Ubuntu 18.04
2. Desktop computer with USB dongle
3. What is the command to check if this is enabled? I don't believe I have such a feature enabled on a desktop computer that is always on; the monitor goes to sleep, though

---

### Post by DuckHook on 2018-08-01
> **Jason_Hunter said:**
> …I don't believe I have such a feature enabled on a desktop computer that is always on; the monitor goes to sleep, thoughSometimes, you don't have to have auto-suspend enabled for the system to power down USB ports. I'm not exactly sure why some systems approach USB power management more aggressively than others, but you can try the UDEV solutions I have already linked you to.

---

### Post by Jason_Hunter on 2018-09-20
I have: 
cat /sys/bus/usb/devices/5-2/power/control 
on

, which means: 

[COLOR=#003366][FONT=euroregular]The [/FONT][/COLOR]on[COLOR=#003366][FONT=euroregular] state means device autosuspend is not allowed[/FONT][/COLOR]

---

### Post by Jason_Hunter on 2018-09-20
Jesus, I've had this problem for years, with numerous bluetooth adapters; what is wrong here? 

Can someone just point me to a usb bluetooth dongle that works?

---

