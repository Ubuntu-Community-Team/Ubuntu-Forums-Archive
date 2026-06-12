---
title: "Shut down with invalid UPS low battery warning"
date: 2015-11-02
forum: General Help
---

### Post by Bill Roberts on 2015-11-02
Recently (last 3 months) I have been experiencing shut downs that start with a warning of a UPS Critical Low Battery when in actuality the battery is completely charged. This is occurring even after replacing the UPS with a new one from a different manufacturer.  It even happened right in the middle of upgrading to 15.10 and that was a real mess to clean-up.  Is any one else having a similar problem or have an answer?  This is a desktop PC , not a laptop.

---

### Post by tgalati4 on 2015-11-02
Check your power outlet connection.  Could be a loose wire that is causing the UPS to work overtime.  Also check your signal cable.  Finally, check the grounding at the outlet and make sure the power connector to the PC is tight.  A loose ground can cause erroneous signalling.  Your log files may show a pattern of signalling states that correspond to a physical condition.

---

### Post by Bill Roberts on 2015-11-02
"Your log files may show a pattern of signalling states that correspond to a physical condition." Which log files should I examine. 
The physical connections appear to be OK.
I have a file from "upower --monitor-detail" that shows the conditions during one of the interruptions.  I changed the gnome-power-manager to hibernate rather than shut down so the log shows the entire sequence. If you think it would b helpful, I'll post it.

---

### Post by tgalati4 on 2015-11-02
Go through /var/log/syslog for anything unusual.

---

### Post by Bill Roberts on 2015-11-02
From /var/log/syslog

Nov  2 14:54:21 desktop1 kernel: [ 6404.871752] usb usb4-port3: disabled by hub (EMI?), re-enabling...

From -monitor-detail

[14:54:04.577]	device changed:     /org/freedesktop/UPower/devices/ups_hiddev1
  native-path:          /sys/devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.0/usbmisc/hiddev1
  power supply:         yes
  updated:              Mon 02 Nov 2015 02:54:04 PM MST (0 seconds ago)
  has history:          yes
  has statistics:       yes
  ups
    present:             yes
    state:               fully-charged
    warning-level:       none
    time to empty:       56.0 minutes
    percentage:          100%
    icon-name:          'battery-full-charged-symbolic'

[14:54:21.163]	device removed:   /org/freedesktop/UPower/devices/ups_hiddev1

[14:54:22.491]	device added:     /org/freedesktop/UPower/devices/ups_hiddev1
  native-path:          /sys/devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.0/usbmisc/hiddev1
  power supply:         yes
  updated:              Wed 31 Dec 1969 05:00:00 PM MST (1446501262 seconds ago)
  has history:          yes
  has statistics:       yes
  ups
    present:             yes
    state:               empty
    warning-level:       none
    percentage:          0%
    icon-name:          'battery-empty-symbolic'

Apparently the USB connection to the UPS is getting disrupted by EMI.

---

### Post by tgalati4 on 2015-11-03
So either the cable is bad (unlikely), or the USB hub is failing, or the 5 VDC is failing on either the PC or the UPS.  Try a different USB port.

---

### Post by Bill Roberts on 2015-11-29
The only solution I found is to disconnect the UPS from USB altogether.

I am currently experiencing a similar problem on a different PC.  During upgrade to 15.10, it also shut down at a critical point. I am currently working on getting the upgrade completed.

I am convinced this is a software issue, since the other PC is connected to a different UPS on a completely different circuit and had NOT experienced this problem in the past.

---

### Post by tgalati4 on 2015-11-29
File a bug against the kernel version that you are running.  During the bug filing process, you will have a chance to look through similar bugs and see if there is a pattern between the kernel version, USB interference, and UPS disruption.

---

