---
title: "Sound Card Help"
date: 2008-05-09
forum: General Help
---

### Post by lakelovers on 2008-05-09
I apologize for this long post but I put myself in a box. I have no sound on 8.04, up from 7.10, on my Dell Dimension 2300. It has an integrated sound card: **ADI 1885**. It doesn't show up when I use code **aplay -l**. I get:

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and when I use  **lspci -v** I get:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: Dell Unknown device 013d
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at e000 [size=256]
	I/O ports at e400 [size=64]
	Memory at ec181000 (32-bit, non-prefetchable) [size=512]
	Memory at ec182000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

...among other devices.

For a few days I assumed that "I82801DBICH4 [Intel 82801DB-ICH4]" was my card. Using that card i.d. I tried the many suggestions for recovering sound. Then I wised up, got out my Dell invoice and see on it that the integrated card is actually "ADI 1885," (assuming that the invoice description is correct). Now, I find that ADI 1885, apparently, is not supported by Alsa. The thing is I had sound on 7.10, but not on 8.04. So, I guess version 7.10 detected the sound card. Where do I go to get sound on 8.04?

---

### Post by lakelovers on 2008-05-11
For anybody who's interested. . . I solved the sound problem. As an afterthought I went to Kbuntu which I have installed but don't use, it had sound, so I went to the alsa setup on it, noted the detected sound card or chip set which by the way was 82801DBC-ICH4. I went back to gnome and put that info in the sound setup and that did it.

---

