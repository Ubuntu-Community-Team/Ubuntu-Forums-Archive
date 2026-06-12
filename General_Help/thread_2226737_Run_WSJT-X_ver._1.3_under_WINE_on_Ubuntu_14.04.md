---
title: "Run WSJT-X ver. 1.3 under WINE on Ubuntu 14.04"
date: 2014-05-28
forum: General Help
---

### Post by tm-hart on 2014-05-28
I have been running WSJT-X weak signal software version 1.1 on Ubuntu ver. 14.04 without problems.  However, WSJT-X ver. 1.3 is the latest version of the s/w and has some interesting improvements.  I installed the Windows program on the Ubuntu system using the WINE utility.  I can load the program and copy incoming signals.  However, the CAT function does not work.  Wonder if anyone has found a way to establish CAT control?  The Configure Menu options on WSJT-X do not work - the USB and COMn options do not function.  Symbolic links for USB and COMn configure options to not work either.  

Would be interested in hearing if a solution to the CAT problem is available and what it involves.  Thanks.

*_Setup parameters for the Linux and Windows versions of WSJT-X and WINECFG are:_*

Hardware / Software
Kenwood TS-590S
USB cable from computer to transceiver
Ubuntu 14.04 operating system
WINE version 1.6.2 (Stable Version)
WSJT-X ver. 1.1 for Linux
WSJT-X ver. 1.3 for Windows

Linux version 1.1 WSJT-X settings:
PTT METHOD: CAT
PTT PORT: NONE
ENABLE CAT: 231 KENWOOD TS-590S
CAT PORT: /dev/ttyUSB0
DATA BITS: 8
STOP BITS: 1
SERIAL RATE: 57600
DATA BITS: 8
STOP BITS: 1
POLLING BITS: 1
AUDIO	DEV.	CH.	AP.	NAME
AUDIO IN:	10	32	ALSA	 DEFAULT
AUDIO OUT:  2	  2	ALSA	 USB AUDIO CODEC

WINDOWS version 1.3 WSJT-X settings:
PTT METHOD: CAT
PTT PORT: NONE
ENABLE CAT: 231 KENWOOD TS-590S
CAT PORT: /USB (Symbolic Link in WINE dosdevices folder)
DATA BITS: 8
STOP BITS: 1
SERIAL RATE: 57600
DATA BITS: 8
STOP BITS: 1
POLLING BITS: 1
AUDIO	
AUDIO IN:	 IN USB ADUIO CODEC / RIGHT
AUDIO OUT:  OUT USB AUDIO CODEC / RIGHT

WINECFG AUDIO SETTINGS:
AUDIO IN:     USB AUDIO CODEC / RIGHT
AUDIO OUT: USB AUDIO CODEC / RIGHT

---

### Post by tm-hart on 2014-06-01
I found an answer to my problem.  A symbolic link of /dev/ttyUSB0 to com2 is needed for the WSJT-X software to run under WINE on Ubuntu.  The program runs on a desktop and portable with no problems after changing the CAT port to "com2".  Hope the info helps someone else interested in weak signal software.

Ubuntu, Wine and WSJT-X

WSJT-X ver. 1.3 for Windows runs on Ubuntu Linux under WINE compatibility layer software.  During testing, contacts were made using the JT65 and JT9 modes.  The key hardware and software settings utilized are:

 Software:
- Ubuntu Linux version 14.04.
- Wine version 1.6.2.
- WSJT-X version 1.3 for Windows.

Hardware:
- Kenwood TS-590S.
- (1) HP desktop and (2) HP portable running Ubuntu 14.04.
- USB cable connecting computer to transceiver.

Wine Setup:
- Open a terminal and create the symbolic link “com2” in the “.wine/dosdevices” folder:
	# ln -s /dev/ttyUSB0 com2

WSJT-X Configure Panel settings:
- PTT Method: CAT
- PTT Port: None
- Enable Cat: Kenwood TS590S
- CAT Port: com2
- Data Bits: 8
- Stop Bits: 1
- Serial Rate: 57600
- Polling Interval: 1
- Select: DTR, RTS and DATA
- Handshake = none.
- Audio In: USB Audio CODEC / Right
- Audio Out: USB Audio CODEC / Right

Configuration Panel Tests Performed:
- “Test CAT Control Button” = successful
- “Test PTT Button” = successful

---

