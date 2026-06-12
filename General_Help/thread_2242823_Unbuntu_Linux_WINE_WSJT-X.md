---
title: "Unbuntu Linux WINE WSJT-X"
date: 2014-09-04
forum: General Help
---

### Post by tm-hart on 2014-09-04
**Ubuntu, Linux, Wine, Icom IC R-75 and WSJT-X**

***WSJT-X ver. 1.3 for Windows runs on Ubuntu Linux with the WINE compatibility layer program.  During testing, both JT65 and JT9 signals were decoded.  The key hardware and software settings are:***

** Software:**
- Ubuntu Linux version 14.04.
- Wine version 1.6.2.
- WSJT-X version 1.3 for Windows.

**Hardware:**
- ICOM IC R-75 receiver.
- HP desktop computer running Ubuntu 14.04.
- USB to Serial cable connecting computer to transceiver (CAT control).
- Audio cable from radio to computer microphone connector (audio in).

**Wine Setup:**
- Open a terminal and create the symbolic link “com2” in the “.wine/dosdevices” folder:
	# ln -s /dev/ttyUSB0 com2
- Trial and error shows that “com2” provides CAT control for the R-75.

**WSJT-X Configure Panel settings:**
- PTT Method: CAT
- PTT Port: none
- CW ID Interval: n/a
- CAT enable: “check”
- CAT port: com2
- Enable CAT: ICOM IC-R75
- Serial Rate: 9600 / 8 bits / 2 stop bits
- Polling Interval: 1
- DTR and RTS: “check”
- Handshake = none.
- Input: “mic” (not “data”)
- Audio In: Pulse Audio / Left
- Audio Out: n/a
- Note: on start up, an error message for “VFO B” may appear; ignore and close.

**Configuration Panel Tests Performed:**
- “Test CAT Control Button” = successful
- “Test PTT Button” = n/a.

*[Date: 20140904]*

---

