---
title: "Output through my VGA monitor only on boot"
date: 2008-06-19
forum: General Help
---

### Post by burton247 on 2008-06-19
sorry if this is the wrong forum to post in.

I understand this is a common topic and i have researched it, but i can quite seem to set it up properly. I can get a virtual desktop thats big enough for both my screens but only the laptop screen is displayed.

Default monitor is my laptop 
VGA is out to another monitor

My VGA comes on for boot sequence with laptop monitor off. When x is starting it switches to laptop screen. i cannot get them working at the same time (not even clone)

Unplugging the VGA displays no signal on screen, when its in an orange light is on which shows its inactive. When its actually got an image going to it the light is green.

Ive followed a few different guides but i cant get it right, can someone give me a hand??

---

### Post by chewearn on 2008-06-20
Please tell us your graphics chip, nvidia, ati, intel or other?

---

### Post by burton247 on 2008-06-20
Sorry forgot to add
part of the output of lspci is

> 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
	Memory at ec000000 (32-bit, prefetchable) [size=64M]
	I/O ports at 9000 [size=256]
	Memory at e4300000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at e4320000 [disabled] [size=128K]
	Capabilities: <access denied>

Even if someone could just help me so that they clone, that would be a step in the right direction

thanks

---

### Post by chewearn on 2008-06-20
I was afraid it's going to be ATI, which I have no knowledge, unfortunately.  Anyone else?

---

### Post by burton247 on 2008-06-20
ill continue looking for guides for the moment then

---

