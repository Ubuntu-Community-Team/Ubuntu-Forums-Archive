---
title: "Mic is staticky on Ubuntu 14.04 but not on Windows"
date: 2016-08-06
forum: General Help
---

### Post by daily01 on 2016-08-06
Hi there.

```

Linux ghost 4.2.0-42-generic #49~14.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

With any application that captures my mic, (i.e. Mumble, Discord, or any application that allows recording) the mic is bad sounding. It is quite staticky and isn't pleasant to listen to.
I tested it up against a laptop that has Windows 7 on it, and it sounded fine there. I tested both mic inputs on my main PC, of which the motherboard is a Gigabyte GA-970A-UD3P.
I've also tested along with other mics, and it has the same issue.

My [MXL 770]("https://www.amazon.com/gp/product/B0007NQH98/ref=oh_aui_detailpage_o02_s00?ie=UTF8&psc=1") plugs into a [Phantom power supply]("https://www.amazon.com/gp/product/B00KAPGLQC/ref=oh_aui_detailpage_o02_s00?ie=UTF8&psc=1") and then into my PC.

Any help would be appreciated!

---

### Post by daily01 on 2016-08-06
bump -- I'll at least make it a useful one.

/etc/pulse/default.pa
[http://pastebin.com/viDUuV1g](http://pastebin.com/viDUuV1g)

/etc/pulse/daemon.conf
[http://pastebin.com/q4Avuv6Y](http://pastebin.com/q4Avuv6Y)

I changed the rate from 44100 to 48000 like arecord suggests when I attempt to record with it, but after restarting PulseAudio there was no effect.
Recording with arecord produces no static, which confirms this is a pulseaudio problem.

---

