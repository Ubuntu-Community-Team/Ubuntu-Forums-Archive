---
title: "can't boot, grub error 18"
date: 2007-05-27
forum: General Help
---

### Post by isaacf on 2007-05-27
I was just using firefox to browse the web and ubuntu froze up and I had to do a hard reset, but then when I tried to reboot, I got GRUB error 18. That apparently means the selected cylinder exeeds what is supported by my BIOS, which is odd because this install has booted properly many times before. I can only surmise that when I manually turned it off my filesystem got corrupted and it thinks that's what happened. I'm not sure what to do now. Any help would be greatly appreciated.

---

### Post by OzOle on 2007-05-28
I'm no expert on this but have also on occasion experienced a similar (identical???) problem.

One thing I then try first is to reset the BIOS settings to whatever the manufacturer considers the standard setting. Different manufacturers may use different names for this but one I remember is "Optimal" settings. In some situations that has cleared the problem suggesting to me at least that in some unfortunate situations where you have to do a hard reset (or power off and then on again) something can get corrupted in the BIOS settings.

I have no idea whether this will solve your problem, but resetting your BIOS to the manufacturer's standard setting should be harmless. When you get the system going again, you may want to revisit the BIOS settings if you have preferred settings.

Hope it helps.

---

### Post by Crafty Kisses on 2007-05-28
This sounds pretty bad, can you get into the login screen at all without the LiveCD?

---

### Post by confused57 on 2007-05-28
Here's some possible solutions for error 18:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)
since it was working before, the bios suggestion sounds like a good idea

---

### Post by sdil on 2007-05-28
a month ago, i have same problem. I know how to repair it. Your must open your computer case and push the wire at hardisk ( all wire at hardisk . you do note worried your  computer will damaage. Just tighten the wire.

I hope you undestand what i saying because I am a Malaysian ;)

---

### Post by trippinnik on 2007-05-28
I think he's right it could be a loose cable.  Have you had any other trouble with the hard drive recently? any fsck's? crashes? is the drive full?

---

### Post by isaacf on 2007-05-28
This happened a couple days ago, but then the problem sort of fixed itself so I backed up all my data. I tried a reinstall, but the install wouldn't load, giving me a "Buffer I/O error on sda1" at certain blocks. My hard drive is Toshiba 30G IDE, if that matters.

The BIOS thing sounds like a good idea. I will try that and report back. 

I am reluctant to open the case and check for loose cables because this is a laptop. Also, I haven't actually moved this laptop in a very long time, so I doubt it's a loose cable, but if the resetting BIOS fails, I might have to check.

---

### Post by isaacf on 2007-05-28
I went into the BIOS, did an HDD self-test and that came out alright, so I then restored the BIOS defaults and when I rebooted I got an error that says it can't find the disk. Drag. So I guess all that's left now is unscrew the laptop case and check the cables, which I want to avoid if all possible. I'm in a bit over my head with that so I think I may take it to a local tech support place. Thanks everybody.

---

### Post by isaacf on 2007-06-03
Well, the harddrive turned out to be completely dead, but I replaced it with one that had 4x the storage so it all worked out.

---

