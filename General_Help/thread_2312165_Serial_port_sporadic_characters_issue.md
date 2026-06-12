---
title: "Serial port sporadic characters issue"
date: 2016-02-02
forum: General Help
---

### Post by roland-logikalsolutions on 2016-02-02
Weird problem. I've done serial port communication since the days of the original XT computer. Not seen this issue.

Ubuntu 14.04 32-bit all updates applied.
Qt 5.4.2

Application on Ubunut computer (actual computer, not VM and the HP motherboard has an actual serial port built in) communicating with external device via serial port.  57600 8-N-1 noFlowControl.  External device sending packets every few seconds. Packets bounded by STX and ETX per historical standards. Device cannot be changed to include additional control characters. This means the device does not transmit adding LF or CR after the packet.

Periodically, but rather consistently the Ubuntu computer will send either 0D (LF) or 0E (SO - Shift Out). It looks like the serial port driver assumes it is a terminal with some kind of line length and forces these characters out to achieve some kind of "line wrap".

Has anybody seen this with 14.04?
Does anyone know how to configure the serial port so it doesn't "think" a terminal is connected? (i.e. so it is just a raw data port not trying to do me any "favors")

Thanks,

---

### Post by coldraven on 2016-02-03
What happens if you just disconnect the TX pin on the computer end of the serial cable? Does the port lose incoming data when it transmits those LF and SO? 
What program is controlling the port? Is it something that can be modified? Sorry for all the questions, I bet you would have preferred answers :)

---

