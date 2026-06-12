---
title: "ubuntu 20.04 no sound"
date: 2020-05-30
forum: General Help
---

### Post by admiralhikarusulu on 2020-05-30
took an old toshiba laptop and put ubuntu 20.04 on it, works great so far except I have no sound.

here is what I have from terminal on sound card:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba Corporation 82801I (ICH9 Family) HD Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at f2800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

have tried reinstalling alsa and pulse audio, but no change.
alsamixer shows Realtek ALC272 selected.

suggestions?

---

### Post by admiralhikarusulu on 2020-05-31
[COLOR=#2E8B57][FONT=monospace]here also is result from pacmd list-sinks

[/FONT][/COLOR]1 sink(s) available.
  * index: 6
	name: <auto_null>
	driver: <module-null-sink.c>
	flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
	state: RUNNING
	suspend cause: (none)
	priority: 1000
	volume: front-left: 57672 /  88% / -3.33 dB,   front-right: 57672 /  88% / -3.33 dB
	        balance 0.00
	base volume: 65536 / 100% / 0.00 dB
	volume steps: 65537
	muted: no
	current latency: 5.17 ms
	max request: 4 KiB
	max rewind: 4 KiB
	monitor source: 6
	sample spec: s16le 2ch 44100Hz
	channel map: front-left,front-right
	             Stereo
	used by: 1
	linked by: 1
	configured latency: 23.22 ms; range is 0.50 .. 2000.00 ms
	module: 26
	properties:
		device.description = "Dummy Output"
		device.class = "abstract"
		device.icon_name = "audio-card"

have tried adding:
options snd-hda-intel dmic_detect=0

with no change

---

