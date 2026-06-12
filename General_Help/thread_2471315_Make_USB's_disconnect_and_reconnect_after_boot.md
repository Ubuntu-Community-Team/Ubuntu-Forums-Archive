---
title: "Make USB's disconnect and reconnect after boot"
date: 2022-01-26
forum: General Help
---

### Post by rehrnsberger on 2022-01-26
I am running Home Assistant in a Virtualbox on Ubuntu 20.04. I have the VM booting on startup. The problem is that the VM doesnt recognize usb devices unless they are plugged in while the vm is open. This is a problem as when the server reboots, the Z-Wave usb key I have does not get found so none of my devices are online. If i go unplug the usb and plug it back in, it gets found. Is there something I can change or a script i can put in place to make the usb disconnect and reconnect after the VM boots or x amount of seconds after booting?

---

