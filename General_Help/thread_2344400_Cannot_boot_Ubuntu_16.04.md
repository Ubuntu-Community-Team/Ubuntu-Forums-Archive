---
title: "Cannot boot Ubuntu 16.04"
date: 2016-11-25
forum: General Help
---

### Post by franckstifler on 2016-11-25
I am having this issue on images when I boot, many services fail to start and I am unable to have the login screen.


```
[FAILED] Failed to start Bluetooth service.
See 'systemctl status bluetooth.service' for details.
[  OK  ] Started LSB: This starts a set of rethinkdb server instances.
[  OK  ] Started System Logging Service.
[  OK  ] Started Save/Restore Sound Card State.
[  OK  ] Started LSB: VirtualBox Linux Additions.
[  OK  ] Started LSB: daemon to balance interrupts for SMP systems.
[  OK  ] Started LSB: This services starts and stops the USB Arbitrator
[FAILED] Failed to start Thermal Daemon Service.
See 'systemctl status thermald.service' for details.
[  OK  ] Started LSB: Record successful boot for GRUB.
[  OK  ] Started Detect the available GPUs and deal with any system cha
[FAILED] Failed to start Avahi mDNS/DNS-SD Stack.
See 'systemctl status avahi-daemon.service' for details.
[  OK  ] Started LSB: automatic crash report generation.
[  OK  ] Started USB_ModeSwitch_2-1.2:1.0.
[FAILED] Failed to start Accounts Service.
See 'systemctl status accounts-daemon.service' for details.
[FAILED] Failed to start Modem Manager.
See 'systemctl status ModemManager.service' for details.
[FAILED] Failed to start Network Manager.
See 'systemctl status NetworkManager.service' for details.
[DEPEND] Dependency failed for Network Manager Wait Online.
```

---

### Post by yancek on 2016-11-25
The first bit of information which would be useful to know is, did this ever work?  Were you previously able to boot without errors?  If so, what changes were made just prior to seeing these errors?

If this is a new install, post some info on the computer hardware.

---

### Post by franckstifler on 2016-11-25
Yes, my O.S was working just fine I booted and logged in without difficulties until, it just went off and started bringing me those errors screen. It is now a new install, I have been using it for about 3months yet. And I frequently make updates.

---

