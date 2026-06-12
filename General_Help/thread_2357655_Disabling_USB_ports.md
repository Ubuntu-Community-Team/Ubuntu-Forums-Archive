---
title: "Disabling USB ports"
date: 2017-04-04
forum: General Help
---

### Post by alexwaltz on 2017-04-04
I have an Ubuntu 14.04 that is in a public spot and my concern is with someone tampering with it.

What I'm wondering is if there is a way to disable/enable the USB ports through the OS so that no one can plug a device into the USB port, but if I need access for whatever reason, I could temporarily enable the USB port through the OS?

Thank you

---

### Post by SeijiSensei on 2017-04-04
You can "blacklist" the usb-storage module from being loaded at boot by adding the line
```
blacklist usb-storage
```
to /etc/modprobe.d/blacklist.conf (edit it with sudo).

Then if you need to restore the port, comment out that line with a hash mark ("#") and reboot.

The better solution is to fill the ports with epoxy, but that's pretty irreversible!

---

### Post by alexwaltz on 2017-04-04
> **SeijiSensei said:**
> You can "blacklist" the usb-storage module from being loaded at boot by adding the line
```
blacklist usb-storage
```
to /etc/modprobe.d/blacklist.conf (edit it with sudo).

Then if you need to restore the port, comment out that line with a hash mark ("#") and reboot.

The better solution is to fill the ports with epoxy, but that's pretty irreversible!

Thank you, this looks pretty straightforward. 

I just want to confirm something, I'd still be able to boot off USB if I need to reinstall the OS for whatever reason?

---

### Post by deadflowr on 2017-04-04
> I just want to confirm something, I'd still be able to boot off USB if I need to reinstall the OS for whatever reason?
yes
If you want to disable it on the machine, disable it in the BIOS.
If you want to disable it on the OS level, disable it in the OS, as posted above.

Disabling it in the OS will not affect how it functions from the BIOS settings, such as booting from a usb stick.
Disabling it in the BIOS will, however, disable it in both the OS and the machine as a whole, including booting from a usb stick.

hope that makes sense.

---

### Post by alexwaltz on 2017-04-04
> **deadflowr said:**
> yes
If you want to disable it on the machine, disable it in the BIOS.
If you want to disable it on the OS level, disable it in the OS, as posted above.

Disabling it in the OS will not affect how it functions from the BIOS settings, such as booting from a usb stick.
Disabling it in the BIOS will, however, disable it in both the OS and the machine as a whole, including booting from a usb stick.

hope that makes sense.

Thank you for clarifying the difference, this makes sense.

---

### Post by HermanAB on 2017-04-05
Another thing you can try is to enable a Guest account and automatically start up into that.  That will effectively turn the machine into a Kiosk and it will be 'fresh' after each reboot.

---

