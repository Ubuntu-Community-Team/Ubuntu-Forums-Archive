---
title: "DBUS: Get a system-wide shareable dbus socket"
date: 2018-05-30
forum: General Help
---

### Post by dnutiu on 2018-05-30
Hello,

I've been working for some time now, along with my friend on a remote controlled car. We're currently developing it on a raspberry pi zero w running the latest raspbian stretch.

We've wrote several modules for reading and controlling sensors and we have integrated them with D-BUS, however we have a slight problem.
Since we don't have that much experience with D-BUS and our modules are run via systemd we've included the following piece of code in every systemd service file:
```
Environment=DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/0/bus
```

The problem is, that in order for this to work we need a root shell open all the time, because otherwise the /run/user/0/bus socket disappears.

Could you please give us some information on what we could do in order to solve this?

Thank you!
All our work is available here: [https://github.com/vnemes/BLECar](https://github.com/vnemes/BLECar)

---

