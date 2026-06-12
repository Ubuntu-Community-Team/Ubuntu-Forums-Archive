---
title: "Vbox"
date: 2007-11-15
forum: General Help
---

### Post by ghostcrab on 2007-11-15
ok I tried tried and tried I have a cheep philips pc web cam and it did work in virtual box 
but I keep have to reinstall the drivers everytime and it's like a shot in the dark to get it to work now with ubuntu 7.10 it work's great the model # is SIC4750/27
anyone could help me out this would be great thank you


```

mount -t usbfs -o devgid=$VBOX,devmode=664,nodev,noexec,nosuid none /proc/bus/usb

VBOX=$(grep vboxusers /etc/group | sed 's/vboxusers:x:\(.*\):.*/\1/')

```

---

