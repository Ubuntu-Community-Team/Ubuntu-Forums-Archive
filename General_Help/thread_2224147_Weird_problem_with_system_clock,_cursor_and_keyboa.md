---
title: "Weird problem with system clock, cursor and keyboard!"
date: 2014-05-14
forum: General Help
---

### Post by r0g2 on 2014-05-14
[I]Ubuntu 14.4 (Trusty) desktop 64bit
Intel® Pentium(R) CPU G3420 @ 3.20GHz × 2
8GB RAM
Brand new machine.[/I]

**Every 30 seconds**, for about 3 seconds my keyboard starts repeating characters like crazy. If I'm not typing anything the cursor starts to flash faster and faster until it is a blurred strobe then, after 30 seconds slows down again. If I watch my system clock it starts off counting at 1 second per second then over the course of 30 seconds speeds up until it's counting several seconds every second. It then goes back to normal and repeats the same patter over and over.

Naturally this makes it hard to type and use the machine in general as it's constantly gaining time. Otherwise it seems perfectly stable and has been running for a month without any other problems but... the above problem is a big problem.

I have ahci and apm set to off in grub. It's a totally vanilla system otherwise (just a samba file server) and 14.4 desktop 64, nothing on it apart from conky, mdadm, iotop, and gddrescue. I have even removed several packages I don't need: Ubuntu One, Games, shotwell, Remmina RDP, Thunderbird, Empathy, Gwibber, Ubuntu One music store, Sound Recorder, Movie Player and Rhythmbox. No restriced extras, no binary blobs.

I'm at a loss. Anyone got any ideas?

Best,

Roger

---

### Post by r0g2 on 2014-05-14
OK, seemingly adding clock=tsc to my grub boot options has fixed it. Will leave overnight and check again tomorrow. Googling around show many people with clock problems under linux, for many years. Have never seen this in windows (or linux before to be fair), does anyone know why it happens (I can rule out CMOS battery in this case).

---

