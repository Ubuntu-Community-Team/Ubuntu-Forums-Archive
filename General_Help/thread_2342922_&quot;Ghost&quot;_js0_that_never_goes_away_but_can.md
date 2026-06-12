---
title: "&quot;Ghost&quot; js0 that never goes away but can be deleted"
date: 2016-11-11
forum: General Help
---

### Post by Powercat on 2016-11-11
Hey guys

I have xubuntu 16.04 LTS on my laptop and also my desktop.

Desktop doesn't have this issue, but my laptop has a /dev/input/js0 device appearing every time on boot, but I don't have a gamepad plugged in.

When I do plug a gamepad, it'll appear as js1, and the second as js2.

This causes a problem for RetroPi where a script tries to find the first joystick, but gets returned js0, the "ghost" device.

And since the script can't open that device, it crashes immediately and prevents RetroPi from loading ANY game.

Strangely tho, I can rm -rf /dev/input/js0 and that makes the script work succesfully cause then it detects js1 as first joystik.

However, it would be good to know why I have a js0 without joystick! What's making it appear?

Thanks!

---

### Post by Powercat on 2016-11-12
Anyone has any idea? How would I go about finding out what device is using /dev/input/js0?

---

### Post by Powercat on 2016-11-14
I reinstalled ubuntu and the issue persists, so there's gotta be something using it!!

---

### Post by Powercat on 2016-11-15
Anyone knows how to list devices? To find what could be making js0 show up?

Thanks

---

### Post by Powercat on 2016-11-15
Did some google searches, found this command:

~$ udevadm info -q all -a /dev/input/js0

The culprit is this one: "Acer BMA150 accelerometer"

I guess now I have to find a way to make it stop using /dev/input/js0

---

### Post by Powercat on 2016-11-15
Was able to resolve the issue by adding "blacklist acer_wmi" to /etc/modprobe.d/blacklist.conf

---

