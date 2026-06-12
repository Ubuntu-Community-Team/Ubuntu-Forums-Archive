---
title: "Debugging a crash when keyboard is not responsive"
date: 2015-02-21
forum: General Help
---

### Post by lordbalmung on 2015-02-21
Ububtu 14.04, Kernel 3.13 crashes very frequently notably when using Firefox, Eclipse and VLC. The effect of the crash is

[LIST]
[*]all USB devices stop responding
[*]if playing a video, it hangs up and sounds like an old stuckup record (plays a second of the video in an infinite loop)
[*]if I try re-pluging the USB devices they don't receive power
[*]Hence SysRq does not work
[*]no entry in kern.log or syslog
[/LIST]

nothing mentioned in the official debugging solution at [https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash) works for obvious reasons, no input devices active.

**I have tried the following without luck**

[LIST]
[*]updating kernel (tried 3.19)
[*]changing graphic drivers (nouveau, nvidia 331, 304 and 340)
[*]asking the same question at [http://askubuntu.com/questions/586475/debugging-a-crash-when-keyboard-is-not-responsive](http://askubuntu.com/questions/586475/debugging-a-crash-when-keyboard-is-not-responsive)
[/LIST]

**Additional Information:**

[LIST]
[*]System: XPS 8700
[*]Processor: i7-4770
[*]RAM: 16GB
[*]Graphics: NVidia GTX645 (OEM)
[*]Motherboard: [http://www.findlaptopdriver.com/dell-0kwvt8-mainboard-specifications/](http://www.findlaptopdriver.com/dell-0kwvt8-mainboard-specifications/)
[*]OS: Trusty Tahr
[/LIST]

Once, just once, I was fortunate enough that an error was displayed, and here is the image below
[IMG]http://i.stack.imgur.com/eiCYQ.jpg[/IMG]

---

### Post by eezacque on 2015-02-21
So, you have not been able to ssh into your crashed machine?

---

### Post by tgalati4 on 2015-02-21
Pull out your RAM.  Try booting with 2GB.  Pull out other stuff and get to a minimum configuration.  It could be your power supply is sagging.  If it seems stable with a minimum configuration, then get a new or certified-working PSU and replace it and then slowly add stuff back to your system.

The error messages seem to indicate something with the graphics card, but it could be anything.  Take out the nVidia card and see if stability improves.  Check that the graphics card is seated properly and that the GPU heatsink is correctly attached and the fan is spinning freely.

Unfortunately, you (the consumer) are the quality control for Dell machines.

---

### Post by lordbalmung on 2015-02-24
> **eezacque said:**
> So, you have not been able to ssh into your crashed machine?

I could not set up the SSH due to a router issue. My router blocked all SSH requests but I got it fixed and have set it up now and the next time my system crashes, I will know the answer to that question :)

---

### Post by lordbalmung on 2015-02-24
> **tgalati4 said:**
> Pull out your RAM.  Try booting with 2GB.  Pull out other stuff and get to a minimum configuration.  It could be your power supply is sagging.  If it seems stable with a minimum configuration, then get a new or certified-working PSU and replace it and then slowly add stuff back to your system.

The error messages seem to indicate something with the graphics card, but it could be anything.  Take out the nVidia card and see if stability improves.  Check that the graphics card is seated properly and that the GPU heatsink is correctly attached and the fan is spinning freely.

Unfortunately, you (the consumer) are the quality control for Dell machines.

The GPU heatsink is correctly attached and the fan is spinning freely, that I know. Also, I do believe the problem lies with nVidia because in Ubuntu 13.10, when I had the same issue I solved it by installing the proprietary 331.113 driver but even that solution has evaded me this time.

---

### Post by tgalati4 on 2015-02-24
Is your system stable for 1 week running 24/7 without the nVidia card?

---

