---
title: "unbalanced collection at end of report description"
date: 2023-02-06
forum: General Help
---

### Post by klundermann on 2023-02-06
After selecting Ubuntu from the GRUB menu lately, I've been seeing the following error message flash on the screen:

```
3.9516531 hid-generic 0003: 1C4F:0202.0002: unbalanced collection at end of report description
```

Otherwise, my system seems to work just fine.  What's going on?

---

### Post by Holger_Gehrke on 2023-02-06
'hid' means 'Human Interface Device' (keyboards, mice, trackpads, gamepads, joysticks ...) . So a generic input device (probably the third device on it's bus, with vendor id of 1c4f (that would be SiGma Micro, according to /var/lib/usbutils/usb.ids) and a device id of 0202 (that's not in that db ...) and with at least two sub-devices is producing some garbage at the end of it's self-description or at least the driver for generic input devices can't understand it ... 

You could take a look at the output of 'lsusb' to see a list of the devices connected by USB or 'sudo lsusb -v -d 1c4f:0202' for a detailed look at that specific device to get an idea what that device is.

Holger

---

### Post by klundermann on 2023-02-06
Thank you very much, Holger_Gehrke!   sudo lsusb ...  shows that it's the keyboard.

I'm guess that the message means that a configuration file somewhere might be missing a closing quotation mark, parenthesis, or some other delimiter.  Would anybody have any idea how I could find the file?

---

### Post by Holger_Gehrke on 2023-02-06
> **klundermann said:**
> sudo lsusb ...  shows that it's the keyboard.

I'm guess that the message means that a configuration file somewhere might be missing a closing quotation mark, parenthesis, or some other delimiter.  Would anybody have any idea how I could find the file?

No, there's some garbage in the data it's sending when asked by the driver to identify itself - probably a small bug in the devices firmware, sending a few bytes more than it should. Not much you can do about it unless you want to reverse engineer the software of the microcontroller inside your keyboard ...

Holger

---

