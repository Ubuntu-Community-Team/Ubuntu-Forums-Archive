---
title: "Soundmodem Transmitting"
date: 2013-09-17
forum: General Help
---

### Post by fCTXLmP on 2013-09-17
I've been working with soundmodem for amateur radio satellite tracking. I've been able to recieve and demodulate using soundmodem, but I'm still having issues modulating and transmitting.

I've been able to activate PTT by hand under the Diagnostics tab. I've assumed that all I have to do is write to [FONT=courier new]/dev/soundmodem0[/FONT] while soundmodem is running and it would take care of the rest, but that doesn't appear to be the case. I've used minicom and CuteCom to write to [FONT=courier new]/dev/soundmodem0[/FONT], and it looks like it wrote successfully, but soundmodem seems to just have sat there and the radio (Yaesu FT-897) didn't transmit at all. Is there a special character sequence I need? Am I doing something wrong (clearly I am, but what)?

Any help is appreciated. Thanks.

**Soundmodem Settings**
Configuration[INDENT]Mode: alsa
ALSA Driver: plughw0,0
PTT Driver: /dev/ttyUSB0
[/INDENT]
Channel[INDENT]Modulator/Demodulator: afsk
Bits/s: 1200
Frequency 0: 1200
Frequency 1: 2200
Differential Encoding: Checked

[/INDENT]
[INDENT]Packet IO Mode: KISS
File: /dev/soundmodem0
Uplink File: Checked
[/INDENT]

---

### Post by fCTXLmP on 2013-09-18
[B]Additional Troubleshooting
[/B]I substituted the DATA cable that ran between the soundcard of the computer and the radio with speakers, then tried to write to the soundmodem device again. I didn't get any sound out of my speakers which tells me that I'm not communicating correctly with soundmodem. I tried both the standard device location (/dev/soundmodem0) and a custom one (~/soundmodem). Nether got me any solutions. I plugged a recording of APRS into my Line In and got soundmodem to demodulate, so that's still working.

[B]Additional Questions
[/B]Am I writing to the device correctly (using CuteCom)?
Is there a better way of writing to devices / checking written devices?

EDIT:
**Further Testing**:
I also just ran [FONT=courier new]soundmodem[/FONT] (rather than [FONT=courier new]soundmodemconfig[/FONT] with diagnostics open) and listened in using CuteCom to the dev port while I played a recording of APRS. Soundmodem demodulated and wrote there and I was able to read it with CuteCom, so somethings going on on the writing side for sure. It's either the writing itself or the modulation, but somehow what I input is not interpreted and processed by soundmodem. Once again, any help is appreciated.

---

### Post by fCTXLmP on 2013-10-24
Solved it!

I can get soundmodem working by using CuteCom, and opening soundmodem's Packet I/O location at 9600bps (I don't think this matters, actually. Any speed should do). Packets need to be written in Hex to the Packet I/O location and need to have a C0 at either end. The second hex number in the series is TNC port, which for me is 00. So I can send:

C0 00 [packet here] C0

and soundmodem will modulate it. Packets have to be short enough (I think it's somewhere around 256 characters). I'll try to update this if I find anything else.

Here's all the hex I know right now for Soundmodem.

00-06: Commands
07-1F: I don't know
20-2F: Symbols
30-39: Decimal Numbers (0-9)
3A-40: More Symbols
41-5A: Uppercase Letters (A-Z)
5B-60: More Symbols
61-7A: Lowercase Letters (a-z)
7B-7E: More Symbols
C0: FEND
DB: FESC
DC: TFEND
DD: TFESC
FF: Return

Good sources:

[http://en.wikipedia.org/wiki/KISS_(TNC)](http://en.wikipedia.org/wiki/KISS_(TNC))
[http://www.ka9q.net/papers/kiss.html](http://www.ka9q.net/papers/kiss.html)

---

