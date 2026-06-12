---
title: "Rules.d thinkpoint settings breaks keyboard layout(?!)"
date: 2015-05-21
forum: General Help
---

### Post by niklp2 on 2015-05-21
Hi, as usual on a new ubuntu (MATE LTS in this instance) install on a thinkpad, I'm having issues setting the Trackpoint speed/sensitivity.

The only thing I could get to work persistently after reboot was creating a rules.d script:

```
# rules file to persist trackpoint settings
SUBSYSTEM=="serio", DRIVERS=="psmouse", WAIT_FOR="/sys/devices/platform/i8042/serio1/serio2/sensitivity", ATTR{sensitivity}="250", ATTR{speed}="180"

```

Whilst this works very nicely for setting up my thinkpoint, upon rebooting with this script in place, my keyboard is now effectively en-US instead of en-UK, despite the former not being installed in the system. This is very weird. Removing the script fixes the problem on reboot.

Any takers?

---

### Post by niklp2 on 2015-05-24
Still no clue why that didn't work, but I fixed my original issue with the advice here, after much hacking about:
[http://askubuntu.com/questions/339107/why-doesnt-my-trackpoint-configure-save-despite-udev-rule](http://askubuntu.com/questions/339107/why-doesnt-my-trackpoint-configure-save-despite-udev-rule)

---

