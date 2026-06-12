---
title: "I need help setting up my new UPS"
date: 2006-11-02
forum: General Help
---

### Post by Hawkowl on 2006-11-02
I just bought a CABAC UPS 100D for my webserver.
It had some installation instructions for linux 2.
I'm running the latest Unbuntu build.
The problem I think is that I connect the UPS to a serial port on my server, but I don't think Ubuntu has recognised the serial ports existance.
Does anyone know how to tell?
After installing and running the software, I get this message

 UPS Adapter No Response!!, type [upsilon stop] to stop this process

Can anyone give me some ideas on what might be going on?

When I try to enter the config it tells me this message

Error opening terminal: xterm.

any help would be appreciated, as I really need this UPS on my webserver before the summer storms start, thanks again all.

---

### Post by Hawkowl on 2006-11-02
Do I even need the software?
I mean shouldn't I just be able to plug the PC into the back of the UPS and it work straight away?
It would give me 10 minutes or so to turn it off anyway wouldn't it?
Does anybody have any experience with these things?

---

### Post by kidders on 2006-11-02
Hi there,

I've been watching your post to see if anyone would answer. I have USB APC UPS (lol :-k ) that works fine without any software.

Having the software is nice though, so you can query the UPS every now and then, or get it to shut off your machines automatically, if the power dies in the middle of the night. The reason I didn't post (until you got so desperate you replied to *yourself*!) is that I'm not so hot with serial ports. If it were me though, I would try connecting something else to it -- something I know how to talk to, like a phone -- so I could see for myself that it's working properly.

First though, check the obvious things, like whether it's enabled in your BIOS, and whether Ubuntu talks about it in your dmesg. The "lshw" tool might also be handy.

Does your UPS software have any configuration files? Perhaps it's not looking in the right place for the port.

---

### Post by Hawkowl on 2006-11-02
Thanks for the input,
yeah I haven't even checked in BIOS yet, but it's that thing with your webserver, you never want to reboot it, cause your don't want someone to be browsing at that very moment you decide to reboot ;) 
But I will.
I/m pretty new to linux and ubuntu, and I don't even know what "dmesg" is, let alone the "lshw" tool, so if you feel like enlightening me a little there, i greatly appreciate it..
but will try that idea with another electrical gadget and see if it stays alive after i turn the power switch off.

---

### Post by kidders on 2006-11-02
Hey again,

[LIST]
[*]dmesg = type "dmesg"
[*]lshw = type "lshw"
[/LIST]
They're ways of finding out what's happening on your system.

> **Hawkowl said:**
> will try that idea with another electrical gadget and see if it stays alive after i turn the power switch off.

If you turn your PC's power off, the serial port will turn off too. The advantage in connecting modem-like devices (eg phones) to your serial port is that they're easy to get working, so you'd know pretty fast if your port is playing nice with Ubuntu, or whether the problem is somewhere else.

---

### Post by bigken on 2006-11-02
One of the reason for the software is so it can broadcast to other pc's on the network when something is wrong ;)

---

