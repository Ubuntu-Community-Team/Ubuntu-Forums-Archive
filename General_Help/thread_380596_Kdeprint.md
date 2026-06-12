---
title: "Kdeprint"
date: 2007-03-09
forum: General Help
---

### Post by cyracks on 2007-03-09
Since this afternoon I can't print anymore. Didn't do any upgrade or as far as I know nothing relevant to make printer stop working.

If I try to print **IPP** report says:
Printer not connected; will retry in 30 seconds...

**lsusb** shows me that printer is connected
...
Bus 001 Device 006: ID 04b8:0802 Seiko Epson Corp. Stylus CX3200
...

but if I try to readd it with kdeprint it is not on the list of local ports selection.
The list looks like:

Local System
-paralel
     - lpt #1
-serial
-usb
-others
        -hp no_device found
        -paralel port #1
...

I also tried the command:
**sudo foomatic-cleanupdrivers **but it didn't help.

[B] What to do, or how to debug the problem ?
[/B]

---

