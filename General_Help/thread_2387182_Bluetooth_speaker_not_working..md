---
title: "Bluetooth speaker not working."
date: 2018-03-15
forum: General Help
---

### Post by Autodave on 2018-03-15
Bought a USB bluetooth adapter that claims it works w/Linux.  I can pair it and it shows up in the list of bluetooth devices available, but I get this error message:

Connection Failed: blueman.bluez.errors.DBusFailedError: Protocol not available.

What do I need to do?  (This is my first time ever playing w/bluetooth.)

---

### Post by Autodave on 2018-03-17
bump

---

### Post by jeremy31 on 2018-03-17
Post results for ```
pactl list short | grep module-bluetooth
```

---

### Post by Autodave on 2018-03-17
That does nothing at all. I even tried it with sudo.

---

### Post by #&amp;thj^% on 2018-03-17
> **Autodave said:**
> That does nothing at all. I even tried it with sudo.

What dose this show then:
```
apt policy pulseaudio-module-bluetooth

```

---

### Post by Autodave on 2018-03-17
apt policy pulseaudio-module-bluetooth
pulseaudio-module-bluetooth:
  Installed: (none)
  Candidate: 1:8.0-0ubuntu3.8
  Version table:
     1:8.0-0ubuntu3.8 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
     1:8.0-0ubuntu3 500
        500 [http://us.a](http://us.a)

---

### Post by jeremy31 on 2018-03-17
Ok
```
sudo apt-get install pulseaudio-module-bluetooth
pactl load-module module-bluetooth-discover
```
See if your headset works after reconnecting

---

### Post by Autodave on 2018-03-17
Took some fiddling in pavucontrol but it works finally!  I was happy when it finally showed in the volume control after doing what you said. A little more playing and it finally works.  Thank you!!!!

---

### Post by kostkon on 2018-03-17
Maybe Autodave is on a derivative that does not install that package by default?

---

### Post by Autodave on 2018-03-17
Xubuntu 16.04 and updated constantly.

---

