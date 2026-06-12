---
title: "Problem waking from suspend with joystick input"
date: 2017-12-05
forum: General Help
---

### Post by wrybread on 2017-12-05
I have a gaming computer that only has joysticks attached to it (no keyboard or mouse), and I'm trying to configure it to wake from suspend when the joystick or joystick button is pressed.

To configure the keyboard to wake the computer with a keypress, I set the contents of this file to "enabled":

 /sys/bus/usb/devices/1-1.5/power/wakeup

The joystick appears to the system as /sys/bus/usb/devices/2-1.1, but I get a "permission denied" error when trying to edit it's wakeup file, even as root. For example:

sudo -i
nano  /sys/bus/usb/devices/2-1.1/power/wakeup
[error writing to  /sys/bus/usb/devices/2-1.1/power/wakeup: permission denied]

I also tried "chmod 755 /sys/bus/usb/devices/2-1.1/power/" but no change.

If it matters, here's the output of lsusb:

```

Bus 002 Device 005: ID 0079:0006 DragonRise Inc. PC TWIN SHOCK Gamepad
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 0079:0006 DragonRise Inc. PC TWIN SHOCK Gamepad
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I'm trying to make it so either of the DragonRise joysticks wake the machine from sleep. I'm of course not married to this method of doing it.

Any tips?

---

### Post by wrybread on 2017-12-09
Sorry to do this, but I'm still out of ideas. So... bump. Anyone have any hints?

---

### Post by wrybread on 2018-02-22
Gar, one more time... bump?

---

