---
title: "Help Getting a udev Rule Working for Sony VAIO Stamina/Speed Switch"
date: 2015-02-18
forum: General Help
---

### Post by svet-am on 2015-02-18
I have a Sony VAIO Z610Y.  This is one of the VAIO's that has the speed/stamina switch for moving between the Intel graphics and nVidia graphics.  I see that there is a sysfs node for the switch located at /sys/devices/platform/sony-laptop/gfx_switch_status.  The contents of gfx_switch_status follow the current status of the switch accurately.

What I would *like* to do is write a udev rule that triggers when I move the switch and then runs the appropriate prime-select command to switch between the Intel and nVidia cards.

Here's the rule set I've come up with so far:

```
50-sony.rules
ACTION=="change", KERNEL=="sony-laptop", SUBSYSTEM=="platform", DRIVER=="sony-laptop", ATTR{gfx_switch_status}=="speed", RUN+="/scripts/sony-speed.sh"
ACTION=="change", KERNEL=="sony-laptop", SUBSYSTEM=="platform", DRIVER=="sony-laptop", ATTR{gfx_switch_status}=="stamina", RUN+="/scripts/sony-stamina.sh"

sony-speed.sh
#!/bin/sh
prime-select nvidia

sony-stamina.sh
#!/bin/sh
prime-select intel
```

If I run "udevadm test", it looks like the trigger is set up properly and will work as I expect.  If I then turn around and run "udevadm trigger", I see the appropriate script run as I expect.  What I'm strugglin with is the "live" application.  When I move the switch back and forth, I am not seeing my udev rule fire and call prime-select.

My *intent* (I don't know if this is correct) is for the udev rules to run when the contents of gfx_switch_status changes since that is the only thing being triggered by the switch.  Is this the proper approach to this problem?  Is there are different way I should be attacking this issue?

---

