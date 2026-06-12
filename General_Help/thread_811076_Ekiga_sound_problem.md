---
title: "Ekiga sound problem"
date: 2008-05-28
forum: General Help
---

### Post by achelis on 2008-05-28
Hi

I've just installed Ekiga and when connecting to echo to test my setup I get the following error message:

```

Could not open audio channel for audio transmission

An error occured while trying to record from the soundcard for the audio transmission. Please check that your soundcard is not busy and that your driver supports full-duplex.
The audio transmission has been disabled.

```

I do get sound from the echo-server however, but no echo from myself.

aplay -l gives me:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v gives me (among other things)
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Giga-byte Technology Unknown device a002
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fa200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

Any ideas?

---

### Post by sharat87 on 2008-09-20
I get the same error... did you find any solution:(?

---

### Post by spiderbatdad on 2008-09-20
Are you using alsa or the pulseaudio sound server under system>preferences>sound?

---

### Post by achelis on 2008-09-22
@sharat: I'm afraid I didn't.

---

### Post by heykenen on 2008-10-04
Hi

I solved the problem with 

$killall pulseaudio

but I don't know why.

---

### Post by Trevorius on 2008-10-22
I'm currently in need of a solution for this as well, but killing pulseaudio didn't work since it wasn't installed on my system in the first place.

---

### Post by crjackson on 2009-02-22
Did anyone find a workable solution? I have this problem too...

---

