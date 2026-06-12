---
title: "led control?"
date: 2013-09-16
forum: General Help
---

### Post by Sketchworks on 2013-09-16
OK, so i have a acer Timeline X and some versions were offered 3g and both have wifi. well the thing is with wifi the led is orange and blinks all the time (dew to traffic i think) and with 3g it is blue. i know that its a single led that switches color and i got 2 other leds right next to it that are blue, the power in the middle will change blue when fully charged. The point is i wanna make that one wifi led switch to blue and stay that way without the 3g is it possible?

---

### Post by tgalati4 on 2013-09-16
Cover with electrical tape and it won't bother you.

Otherwise, look in /etc/acpi/events for LED events.

---

### Post by Sketchworks on 2013-09-16
there is no led events

---

### Post by tgalati4 on 2013-09-16
You probably need a module for your Acer that provides that level of control.  For example on an IBM Thinkpad, there is a module that provides LED control:  [http://manpages.ubuntu.com/manpages/hardy/man4/acpi_ibm.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/acpi_ibm.4.html)

If electrical tape doesn't work, then try some of these suggestions:  [http://askubuntu.com/questions/12069/how-to-stop-constantly-blinking-wifi-led](http://askubuntu.com/questions/12069/how-to-stop-constantly-blinking-wifi-led)

---

