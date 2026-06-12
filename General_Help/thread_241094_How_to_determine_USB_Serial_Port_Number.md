---
title: "How to determine USB Serial Port Number?"
date: 2006-08-21
forum: General Help
---

### Post by drfox on 2006-08-21
I need to use a Hyperterminal-like program to connect to a lab machine at work. I've installed gtkterm, and I've connected my laptop to the machine via USB cable.

gtkterm is asking what port I'm using, and I've tried ttyS0 through ttyS9; when I execute the command sudo/cat/ttyS0 through 9, I get an input output error.  I've tried sudo ls /dev/ttyUSB* and get no such file.

I have 4 USB ports on this laptop--how can I determine which serial ports they're using, or better yet, how do I configure gtkterm to use the USB ports?

Thanks, Larry

---

### Post by mpvano on 2006-08-22
try watching the log file as you plug in the usb to serial converter device.

tail -f /var/log/messages

My usb converters show up there and there's also a message saying what the device file is.

For the record, my Trendnet TU89 usb/serial adapters work perfectly with linux and the builtin kernel drivers, but not all such devices work without proprietary drivers!

Mine (I've only tried it with one at a time) shows up as ttyUSB0 and I can use it in gtkterm with the command

gtkterm -p /dev/ttyUSB0 -s 19200

to talk to my serial bar code scanner, for example.

Hope this helps....

Mario

---

