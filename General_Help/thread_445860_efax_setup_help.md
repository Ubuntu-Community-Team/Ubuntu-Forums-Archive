---
title: "efax setup help"
date: 2007-05-16
forum: General Help
---

### Post by ubiwankanubi on 2007-05-16
I had bought a faxmodem that works with linux (original system it was on was fedora, and it worked fine)

but now installing efax and efax-gtk I get this error:
tcgetattr on fd=4 failed: Input/output error

what is causing this?

---

### Post by ubiwankanubi on 2007-05-16
i tried setting the ttyS1 to ttyS0 and i get this message:

efax-0.9a: 11:41:32 opened /dev/ttyS0
efax-0.9a: 11:41:39 sync: dropping DTR
efax-0.9a: 11:41:43 sync: sending escapes
efax-0.9a: 11:41:49 Error: sync: modem not responding
efax-0.9a: 11:41:49 finished - no response from modem

here is the result of lspci -vv

01:08.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (re
v 01) (prog-if 02 [16550])
        Subsystem: 3Com Corp, Modem Division Unknown device 00d3
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 5
        Region 0: I/O ports at a800 [size=8]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0+,D1-,D2+,D3hot
+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-

---

