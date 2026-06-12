---
title: "Hard drive swap changes suspend behaviour"
date: 2016-05-07
forum: General Help
---

### Post by DigiAngel on 2016-05-07
Well this is weird.  I swapped my hard drive (an SSD) to a different one after imaging the drive with partimage.  Everything works, but previous pm-suspend behaviour was:

```
Mouse lights stay on (Evoluent mouse)
Machine wakes on keyboard press
Power indicator on the workstation flashes
```

Now however pm-suspend makes it so the mouse lights are off and I have to press the power button on the machine to wake it back up...pressing a button on the keyboard doesn't work any more.  Has anyone seen this before?  Thank you.

---

### Post by DigiAngel on 2016-05-07
Not solved with adding echo "enabled" > /sys/devices/pci0000:00/0000:00:14.0/usb1/1-9/power/wakeup to /etc/rc.local

---

