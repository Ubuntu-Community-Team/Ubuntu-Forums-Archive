---
title: "scanner = error"
date: 2007-09-03
forum: General Help
---

### Post by scragar on 2007-09-03
I just got given a scanner by a relative, and after throwing the windows driver disk into the bin I plugged it in and it was instantly picked up. my problem is that whenever I try Xsane I get the message:

Error
Failed to open devide 'gt68xx:libusb:003:003':
Invalid argument.

anyone got any ideas?

---

### Post by scragar on 2007-09-03
*bump*

I know the scanner is supported bye sane, I checked that already, but I have no idea about the error, could someone please point me in the right direction?

---

### Post by geraldm on 2007-09-04
Show the permissions for the device: bus=003 device=003
ls -l /proc/bus/usb/003/003

What were ALL of the arguments passed?
Be sure the user has R/W permission on the device, as that is one way to fail.

Gerald

---

### Post by scragar on 2007-09-04
I have spotted the problem, although I have no idea how to fix it...

I decided to run it from the terminal instead of the launcher and got his message printed out:
> [gt68xx] Couldn't open firmware file (`/usr/share/sane/gt68xx/PS1fw.usb'): No such file or directory

after checking it /usr/share/sane/gt86xx is empty...

any ideas as to what I should do from here?

As per request:
$ ls -l /proc/bus/usb/003/003
-rw-r--r-- 1 root root 43 2007-09-04 00:17 /proc/bus/usb/003/003

---

### Post by geraldm on 2007-09-04
Sooner or later you will have a permissions problem.
On my system, the group is scanner, which I make read/write.
The owner of the device could be changed to the users name to test it.

The firmware file does not come with the sane package.  I have no idea where to get it.
There are other locations for firmware, such as /lib/udev/devices/
Try google for the filename ?

Gerald

---

