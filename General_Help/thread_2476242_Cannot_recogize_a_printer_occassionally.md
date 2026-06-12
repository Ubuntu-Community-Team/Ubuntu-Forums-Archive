---
title: "Cannot recogize a printer occassionally"
date: 2022-06-20
forum: General Help
---

### Post by ODBWilson on 2022-06-20
Hi,

I am using lubuntu 20.04 and try to a thermal printer.
But I have no idea why the system cannot connect to this thermal printer sometimes.
The kernel log shows usblp4 is removed.

Kenel log:
                  [FONT=Calibri]usblp 1-1.2:1.0: usblp4: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x0FE6 pid 0x811E[/FONT]

                         [FONT=Calibri]usbcore: registered new interface driver usblp[/FONT]

      ...............
usblp4: removed

The quickest way to fix this is to turn off and on the thermal printer.
And the system will recognize the printer again.

I also tried using usbreset, but it didn't help
[COLOR=#000000][FONT=Calibri]sudo usbreset 0fe6:811e
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri]Resetting USB Receipt Printer ... ok[/FONT][/COLOR]

Any other ways, like re-scanning the USB port from the command line to recognize the thermal printer again?

Thanks,
Wilson

---

### Post by TheFu on 2022-06-21
Sounds like a bad USB connection, port, or cable.

There isn't much that can be done. USB-A ports relatively suck and wear out.  

You might try lightly making the male side of the USB plug just a little tighter.  More than your fingers can do, but with an extremely light touch on any pliers. Too small means it won't fit into any USB port or the cable will be destroyed. Just want it to be a little tight to prevent vibrations making the connection loose, nothing more.

The connection issue could be on the computer or printer side of the USB cable.

---

