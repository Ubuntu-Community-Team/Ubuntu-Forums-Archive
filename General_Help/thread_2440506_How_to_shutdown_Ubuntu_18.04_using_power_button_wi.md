---
title: "How to shutdown Ubuntu 18.04 using power button without monitor attached?"
date: 2020-04-11
forum: General Help
---

### Post by crabbychicken on 2020-04-11
Hi,

I have two installations of Ubuntu 18.04 lts - one on a desktop pc and one on a persistent usb.

I noticed that when a monitor is attached to the computer (turned on or off) pushing the power button will turn off the computer automatically after 60 seconds - GREAT!!!- both installations.

This power button does not work if the monitor is not physically attached to the computer - BOOOO!!! - to turn it off I have to either ssh in or hook up the monitor.

Is there a way to enable the power button to turn off the computer when no physical monitor is attached to the computer?

I have a virtual monitor in my startup applications - bash script and xrandr - but this does not help.

Thanks.

---

### Post by VeloxNeb on 2020-04-16
would've been nice to know which video driver you're using... ;-) 
 
assuming your (Gnome) Settings -> Power -> Suspend & Power Button -> When the Power Button is pressed:
is set to "Power Off" 

and this [https://www.linuxquestions.org/questions/ubuntu-63/trying-to-make-ubuntu-18-04-shutdown-on-power-button-4175636022/](https://www.linuxquestions.org/questions/ubuntu-63/trying-to-make-ubuntu-18-04-shutdown-on-power-button-4175636022/) doesn't help, please file a bug report.

---

