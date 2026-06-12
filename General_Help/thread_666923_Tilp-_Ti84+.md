---
title: "Tilp- Ti84+"
date: 2008-01-13
forum: General Help
---

### Post by talon314 on 2008-01-13
I've seen various other threads relating to tilp, but nothing like what I'm getting.

Basically, I am able to connect my ti84+ over usb to my computer with tilp2, receive all data types, and send applications to my calculator. However, I cannot send appvars, programs, or anything else except apps.

This is the output from the terminal window when I try to send a program:

TiLP2 - Version 1.07, (C) 1999-2006 Romain Lievin
THIS PROGRAM COMES WITH ABSOLUTELY NO WARRANTY
PLEASE READ THE DOCUMENTATION FOR DETAILS
built on Aug 30 2007 17:44:57
tilp-INFO: setlocale: en_US.UTF-8
tilp-INFO: bindtextdomain: /usr/share/locale/
tilp-INFO: textdomain: tilp2
ticables-INFO: ticables library version 1.0.8
ticables-INFO: setlocale: en_US.UTF-8
ticables-INFO: bindtextdomain: /usr/share/locale
ticables-INFO: textdomain: libticables2
ticables-INFO: kernel: 2.6.22-14-generic
tifiles-INFO: tifiles library version 1.0.7
tifiles-INFO: setlocale: en_US.UTF-8
tifiles-INFO: bindtextdomain: /usr/share/locale
tifiles-INFO: textdomain: libtifiles2
ticalcs-INFO: ticalcs library version 1.0.7
ticalcs-INFO: setlocale: en_US.UTF-8
ticalcs-INFO: bindtextdomain: /usr/share/locale
ticalcs-INFO: textdomain: libticalcs2
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
tilp-INFO: Searching for link cables...
ticables-INFO: Link cable probing:
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO:  found TI-84 Plus Silver Edition on #1, version <1.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO:  found TI-84 Plus Silver Edition on #1, version <1.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO:  found TI-84 Plus Silver Edition on #1, version <1.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO:  found TI-84 Plus Silver Edition on #1, version <1.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO:  found TI-84 Plus Silver Edition on #1, version <1.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO:  found TI-84 Plus Silver Edition on #1, version <1.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
tilp-INFO: Searching for hand-helds on DirectLink...
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO:  found TI-84 Plus Silver Edition on #1, version <1.00>
ticalcs-INFO:   PC->TI: Buffer Size Request (1024 bytes)
ticalcs-INFO:   TI->PC: Buffer Size Allocation (250 bytes)
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO:  found TI-84 Plus Silver Edition on #1, version <1.00>
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO:  found TI-84 Plus Silver Edition on #1, version <1.00>
ticalcs-INFO: Checking hand-held status:
ticalcs-INFO:   PC->TI: Buffer Size Request (1024 bytes)
ticalcs-INFO:   TI->PC: Buffer Size Allocation (250 bytes)
ticalcs-INFO:   PC->TI: Ping / Set Mode
ticalcs-INFO:    0003 0001 0000 0000 07d0
ticalcs-INFO:   TI->PC: Acknowledgement of Mode Setting
ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO:  found TI-84 Plus Silver Edition on #1, version <1.00>
ticalcs-INFO: Checking hand-held status:
ticalcs-INFO:   PC->TI: Buffer Size Request (1024 bytes)
ticalcs-INFO:   TI->PC: Buffer Size Allocation (250 bytes)
ticalcs-INFO:   PC->TI: Ping / Set Mode
ticalcs-INFO:    0003 0001 0000 0000 07d0
ticalcs-INFO:   TI->PC: Acknowledgement of Mode Setting
ticalcs-INFO: Requesting folder & vars & apps listing:
ticalcs-INFO:   PC->TI: Request Directory Listing
ticalcs-INFO:    naids=3

<a long list of everything currently on the calc, then>

ticables-INFO: Check for lib-usb support:
ticables-INFO:     usb support: available.
ticables-INFO: Check for lib-usb usability:
ticables-INFO:     usb filesystem (/dev/bus/usb/): mounted
ticables-INFO:  found TI-84 Plus Silver Edition on #1, version <1.00>
ticalcs-INFO: Checking hand-held status:
ticalcs-INFO:   PC->TI: Buffer Size Request (1024 bytes)
ticalcs-INFO:   TI->PC: Buffer Size Allocation (250 bytes)
ticalcs-INFO:   PC->TI: Ping / Set Mode
ticalcs-INFO:    0003 0001 0000 0000 07d0
ticalcs-INFO:   TI->PC: Acknowledgement of Mode Setting
ticalcs-INFO: Sending one or more variables:
ticalcs-INFO:   PC->TI: Request to Send
ticalcs-INFO:    folder=, name=BYTES, size=1335, nattrs=3
ticalcs-INFO:   TI->PC: Delay Acknowledgment
ticalcs-INFO:     delay = 4294967295

at which point it hangs indefinitely. Anyone know of a workaround?

---

### Post by talon314 on 2008-01-14
Nevermind. Seems everything except the apps happened to be corrupted when I made my backup.

---

