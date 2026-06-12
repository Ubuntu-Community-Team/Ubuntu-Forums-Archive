---
title: "AMD Catalyst in Ubuntu 16.04"
date: 2016-06-07
forum: General Help
---

### Post by uRock on 2016-06-07
Hi all,

I recently installed 16.04 on my system and I like almost everything about it, except the lack of graphics drivers.

AMD's Catalyst Controls allowed me to adjust the screen size to work with my plasma TV via HDMI.

The driver also made the HDMI audio show as an option in the Sound applet.

That said, is there a workaround to get the Catalyst driver for my system or should I take the easy route and reinstall 14.04, then pray that Canonical brings back the drivers for 18.04?

```
ronnie@5FDP:~$ lspci
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series]

```

I really enjoyed the hot swappable experience with the drivers that came with Ubuntu 14.04 and would love to get that back.

Cheers & Beers,
uRock

---

### Post by QIII on 2016-06-07
A rocky road lies ahead.

The fact that fglrx is not included with 16.04 (and there is no work around) is due in equal parts to Canonical and AMD:  the fglrx driver would not work with the updated X Server that Canonical intended to include in 16.04 and AMD didn't want to take the time to update fglrx so that it would.

That may seem like madness, but it was triage on the part of both parties.  AMD and Canonical have been working very closely and very hard on two open source drivers:  the old Radeon driver (to improve it) and AMDGPU -- a new driver entirely that is the open source basis for the AMDGPU-Pro hybrid open-source/proprietary driver that eventually replaces fglrx.

I short, what we are seeing is AMD working very hard to deliver what we have been asking for:  a truly useful and feature rich open source driver.  But getting there will be painful.

At the moment, when you install 16.04 the installer decides if you hardware supports AMDGPU and installs it.  If not, the Radeon driver is installed.  For the moment, AMDGPU only works with GCN 1.2 hardware -- the Fiji and Tonga chipsets.  Work is being done to get it to work with GCN 1.1 (already an experimental driver) and possibly GCN 1.0.  But older cards (yet again) will not be covered.

As to whether there will ever be a future fglrx, I see some speculation from those "in the know" and some teasers from AMD.

I bought an R9 380X (a Tonga chipset) just to be able to test all of this and the AMDGPU driver works exceptionally well (in some cases better than fglrx) but there isn't a Catalyst-style GUI.  I'm fiddling around with the AMDGPU-Pro beta on my Yakkety install, but I'm not prepared to say much at the moment.

---

### Post by uRock on 2016-06-07
Thanks for the input. I'll probably go back to 14.04 until 18.04 comes out. Hopefully by then they'll have the driver easily configurable.

---

### Post by QIII on 2016-06-07
Keep an eye out.  The scuttlebutt indicates an fglrx returning at the first point release.  Possibly.  Maybe.

---

### Post by uRock on 2016-06-07
> **QIII said:**
> Keep an eye out.  The scuttlebutt indicates an fglrx returning at the first point release.  Possibly.  Maybe.

Will do, thanks!

---

