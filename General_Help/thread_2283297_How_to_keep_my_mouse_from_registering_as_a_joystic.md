---
title: "How to keep my mouse from registering as a joystick?"
date: 2015-06-20
forum: General Help
---

### Post by mikevaughn on 2015-06-20
I'm using a Roccat Tyon mouse, purchased because Roccat's known for their good Linux support. It generally works great, but udev is recognizing it as a gamepad. This causes issues in a number of games, so I usually need to unplug it before playing if I want to use my wireless Xbox 360 controller(s). I've tried fixing the issue by following the steps outlined [here]("http://ubuntuforums.org/showthread.php?t=1595666") , with no results.

Here are the current contents of /etc/udev/rules.d:
60-ssd-scheduler.rules
70-persistent-net.rules
90-roccat-arvo.rules
90-roccat-iskufx.rules
90-roccat-isku.rules
90-roccat-koneplus.rules
90-roccat-konepuremilitary.rules
90-roccat-konepureoptical.rules
90-roccat-konepure.rules
90-roccat-kone.rules
90-roccat-konextdoptical.rules
90-roccat-konextd.rules
90-roccat-kovaplus.rules
90-roccat-lua.rules
90-roccat-pyra.rules
90-roccat-ryosmk.rules
90-roccat-ryostkl.rules
90-roccat-savu.rules
90-roccat-tyon.rules
99-persistent-joystick.rules
README

The content of 99-persistent-joystick.rules:
```
KERNEL=="js?", ENV{ID_VENDOR}=="©Microsoft", ENV{ID_MODEL}=="Xbox_360_Wireless_Receiver_for_Windows", NAME="input/js0"
KERNEL=="js?", ENV{ID_VENDOR}=="ROCCAT", ENV{ID_MODEL}=="ROCCAT_Tyon_Black", NAME="input/js4"
```

Ideally, this would reserve the js0-js3 slots for my wireless 360 controllers, and assign the mouse to js4, but it's not having that effect (or any other effect as far as I can tell). I also tried removing the rules starting with "90-roccat-" to make sure they weren't doing something weird, but this also had no visible effect.

Any help with this would be greatly appreciated. :)

---

### Post by stefan_achatz on 2015-07-08
The following code deactivates the joystick part of the Tyon. Don't use this if you want to configure your X-Celerator as analog axis.
```
SUBSYSTEM=="usb", ATTR{bInterfaceNumber}=="02", ATTRS{idVendor}!="1e7d", ATTRS{idProduct}!="2e4a|2e4b", RUN+="/bin/sh -c '/bin/echo -n %k >/sys${DEVPATH}/driver/unbind'"
```

---

### Post by mikevaughn on 2015-07-08
That solved it. Many, many thanks!! :D

---

### Post by mikevaughn on 2015-07-08
Looks like I spoke too soon. That rule also disables my wireless keyboard w/ built-in touchpad. Any idea how I should modify it so it will *only* deactivate the joystick part of the Tyon, without touching anything else?

---

### Post by stefan_achatz on 2015-07-08
Typos fixed, testing equality instead of inequality:
```
SUBSYSTEM=="usb", ATTR{bInterfaceNumber}=="02", ATTRS{idVendor}=="1e7d", ATTRS{idProduct}=="2e4a|2e4b", RUN+="/bin/sh -c '/bin/echo -n %k >/sys${DEVPATH}/driver/unbind'"
```

---

### Post by mikevaughn on 2015-07-08
That got it. Thanks, you're awesome!! :D

---

