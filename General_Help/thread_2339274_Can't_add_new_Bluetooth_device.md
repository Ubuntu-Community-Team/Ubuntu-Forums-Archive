---
title: "Can't add new Bluetooth device"
date: 2016-10-06
forum: General Help
---

### Post by jamesva3 on 2016-10-06
Using ubuntu 16.04, I know bluetooth is active as it can search and recognize other bluetooth devices however after selecting a bluetooth mouse to connect, the 'next' button is greyed out and i cannot proceed. My problem is a bit vague, but hopefully it won't be difficult to diagnose... and yes I have the hardware switch for bluetooth switched to on, haha.[IMG]http://imgur.com/a/o16Js[/IMG]

screen cap of the bump in the road: [http://imgur.com/a/o16Js](http://imgur.com/a/o16Js)

---

### Post by jeremy31 on 2016-10-06
It looks like the mouse has a MAC address that I don't think is valid but we can try through terminal
```
bluetoothctl
```
With the mouse in pairing mode then do
```
scan on
```
Hopefully it finds the mouse and it doesn't show a 00:00:00:00:9F:7D MAC address

Then do ```
pair MAC Address
trust MAC address
connect MAC address
exit
```

I just did it that way with a Logitech travel mouse and I was able to use the mouse after the connect command

---

### Post by jamesva3 on 2016-10-06
Fantastic! How did you know something was wrong with the mac address? Kudos to you for an easy fix!

---

