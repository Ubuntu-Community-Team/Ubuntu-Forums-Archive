---
title: "gnome-bluetooth-manager will not run"
date: 2006-09-05
forum: General Help
---

### Post by adam.tropics on 2006-09-05
Ok, too-may guide-itus again. Anyway, trying to run gnome-bluetooth-manager gives me:

```
adam@adam-laptop:~$ gnome-bluetooth-manager
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/gnomebt/manager.py", line 274, in ?
    BTManager ().main ()
  File "/usr/lib/python2.4/site-packages/gnomebt/manager.py", line 85, in __init__
    if not self.btctl.is_initialised():
gobject.GError: Can't get device id of hci0
```

Added to that, hcitool scan, gives 'Device not available: No Such Device'

I have no clue, but it all worked a couple months ago.

Anyone?

The stage I am trying to get to....again, is the ability to send and recieve files from bletooth Nokia N80, via bluetooth dongle.

---

### Post by mlind on 2006-09-05
hci0 refers probably to local device which is your BT dongle.

What gets appended to /var/log/syslog when you restart the bluetooth service?
```

sudo /etc/init.d/bluez-utils restart

```

What does **hcitool dev** report?

---

