---
title: "Hardy Heron unmitigated video disaster"
date: 2008-06-03
forum: General Help
---

### Post by dracovich on 2008-06-03
Sadly i'm posting this question from my windows dualboot because the hardy install had simply become unmanageable.

Basically what is happening, that it crashes VERY often when playing videos. % wise it's not insanely high, probably low single digits, but i watch enough videos every day for it to mean at least 3-4 restarts a day. It's most common to happen when playing AVI files in VLC, but i've also had the same problem with mplayer, a few times when a flash video is playing (on a website) and recently it's been happening when playing embedded windows files.

What happens is that the screen and keyboard completely freeze up (except for the mouse, which can be moved but does nothing), but the sound keeps playing. Only thing to do is to cut power and reboot. The embedded windows video files one is slightly different in that the screen doesn't just freeze, it changes to some weird black/pink/green pixel combo (not sure how to explain it better then that).

I really hate being back on windows and wish i could do Heron, but unless someone has suggestions as to what to do, i really see no other choice, i'd be really annoyed if i had to do a fresh install as i was under the impression that this was the whole point of linux, that reinstalls and reformats were not suppose to be necessary.

P.S. i don't think pulseaudio is the problem, i did at first but this problem seems to happen even if i've already killed the process.

---

### Post by mikewhatever on 2008-06-03
The pattern you describe may suggest a faulty graphics driver. Can you provide more info about your hardware (CPU, RAM, graphics card).
Sometimes, it's easier to fix the problem by reinstalling, and Linux is no different in that respect.

---

### Post by dracovich on 2008-06-04
Thanks for your response. It's a 2 year old Alienware Sentia m3450, i'll just post the specs from my old order form:

Processor: Intel® Core™ 2 Duo Processor T7200 2.0GHz 4MB Cache 667MHz FSB
Operating System (Office software not included): Genuine Windows® XP Professional with Service Pack 2
Display: Alienware® Sentia m3450 with 14" WideXGA 1280 x 768 LCD with Webcam - Xeno Grey
Motherboard: Alienware® Intel® 945GM + ICH7 Chipset
Memory: 512MB Dual Channel DDR2 SO-DIMM at 667MHz - 2 x 256MB
Hard Drive: 100GB Serial ATA 1.5Gb/s 7,200 RPM w/ NCQ & 8MB Cache
Primary CD ROM/DVD ROM: 24x10x24 CD-RW / 8X DVD Combo w/Software MPEG2 Decoder
Video/Graphics Card: Intel® GMA 950 Extreme Graphics
Sound Card: Intel® 7.1 High-Definition Audio
Wireless Network Card: Internal Intel® PRO Wireless 3945 a/b/g Mini-Card
Communications: Integrated 10/1000Mb Gigabit Ethernet & 56K V.92 Modem 

A friend of mine suggested turning of Compiz, don't know if that'll help, i'm back on it now and so far no crashes (although it's still way too early to tell if it fixed anything).

---

### Post by dracovich on 2008-06-04
Found this thread 

[http://forum.compiz-fusion.org/showthread.php?t=4065](http://forum.compiz-fusion.org/showthread.php?t=4065)

on the lead that it might be my video drivers fault, i'll try those suggestions, sounds like a similar problem with the same hardware (although i'm surprised i had no problems at all with Gutsy, used it from release until Hardy came out without a single (video related) crash.

---

