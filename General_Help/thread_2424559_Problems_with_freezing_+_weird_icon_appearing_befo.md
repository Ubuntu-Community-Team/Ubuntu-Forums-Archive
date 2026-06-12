---
title: "Problems with freezing + weird icon appearing before"
date: 2019-08-10
forum: General Help
---

### Post by mathiasbuntu2 on 2019-08-10
[COLOR=#242729][FONT=Arial]Hello Everybody and thank you in advance :)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]It’s been now 2 weeks I am trying to resolve a weird issue (not intensively).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]When I login into ubuntu, everything seems to works and after approximately 2-5 minutes, I have this weird icon appearing. It stay 3 seconds, disappears and then everything freezes. I can’t even use Control+F2 anymore. I have to restart manually.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Here is the icon appearing and disappearing before the crash. It looks like it means that the computer is unplugged, but that’s a Desktop one and everything is working perfectly on windows.

[https://i.stack.imgur.com/rCIXp.jpg](https://i.stack.imgur.com/rCIXp.jpg)

Thank you ...[/FONT][/COLOR]

---

### Post by mathiasbuntu2 on 2019-08-10
Any hints ? :(

---

### Post by dragonfly41 on 2019-08-10
It looks to me that this might be a [power cable icon]("https://www.flaticon.com/free-icons/electric-cable")

---

### Post by mathiasbuntu2 on 2019-08-10
That is also what I think, and right after this icon disappears the computer crashes. As I said I can’t even use tty ...
if that’s a power cable issue that would be really weird as I’m using a desktop computer

---

### Post by Autodave on 2019-08-10
Weak power supply?  Too many peripherals drawing the 5V line low?  Do you hear fans slowing down or even stopping?

---

### Post by mathiasbuntu2 on 2019-08-12
My configuration is:
-processor i7 6700k
-motherboard [FONT=Arial]Gigabyte Z170X-Gaming 7[/FONT]
-[FONT=Arial]DDR4 Kingston HyperX Fury, 2 x 8 Go
- GTX 1060
-Power supply corsair 750W

I have a lot of things plugged in USB as gaming headphone, RGB mouse, razer keyboard RGB also.
Do you think that could be the reason ?

And are you sure about the meaning of the icon? i know that is a silly question cause it does look very much like a PSU issue
Should I try to start it without all this stuff pluggin in ?

Thank you so much for you help[/FONT]

---

### Post by dragonfly41 on 2019-08-12
You need to learn how to diagnose problems by using a process of elimination.
Certainly I would try plugging in devices ("things") one by one.
Try a different USB port on your PC or even add an extension USB hub (I have one which extends 4 ports and it has its own power supply).
Are your devices expecting USB2 or USB3 for example.

---

### Post by mathiasbuntu2 on 2019-08-15
I am coming back today with an interesting thing, I tried to unplugged my USB devices (mouse/keyboard/headphone)
one by one by nothing changes.
Then I decided to make a tail -f for all the logs in /var/log before it crashes.
Globally the second it crashes nothing logs : Except /var/log/syslog and here is the result of that :
[ATTACH=CONFIG]283807[/ATTACH]

I have been very careful with the time and the crashes happened at 20:04:38.I don’t really know how to interpret those logs. But it definitely has something to do with power level, which is weird has windows has been working perfectly for 4 years on this computer before.

I am now in dual boot.
thank you very much for your help

---

### Post by mathiasbuntu2 on 2019-08-15
It is removing my mother board, that does not make sense :eek:

---

### Post by dragonfly41 on 2019-08-15
I'm not sure what you mean by "removing my motherboard" but are you using USB ports near your motherboard which might drain power? Try other port(s). If you have a USB port expander, with its own power supply, try that. Or buy one.

---

### Post by mathiasbuntu2 on 2019-08-15
Ok thanks I&#8217;m ordering one right now and will come back to you after I tried that.
I was saying that it is removing the motherboard because it is written in the logs : 
setting force_power to OFF
State changed: supported/off
GA-Z170-GAMING removed
GA-Z170-GAMING dbus:unexported

---

### Post by dragonfly41 on 2019-08-15
Possibly [some clues here]("https://www.kernel.org/doc/html/v4.14/driver-api/usb/power-management.html") .. but it is guesswork.

---

