---
title: "Canon LBP7010C printer do not wake up from sleep mode"
date: 2013-04-20
forum: General Help
---

### Post by leifwi on 2013-04-20
I have a Canon LBP7010 connected to a usb port on a stand alone PC, ubuntu 12.04. Canon CAPT driver v 2.50. After power on the printer works
fine, but after some time it goes to sleep mode. When trying to print it will not wake up, only way is to turn power off and on.

Is there a fix for this problem?

---

### Post by leifwi on 2013-08-14
I managed to solve the problem.

The solution is to diable the autosuspend function on the usb port.

Use the sudo lsusb to find the usb port, in my case:
Bus 007 Device 003: ID 04a9:271c Canon, Inc.

Enter command 
echo -1 | sudo tee /sys/bus/usb/devices/7-3/power/autosuspend

7-3 refers to Bus 007 Device 003 retreaved by the lsusb command.

---

