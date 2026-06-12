---
title: "Static kills my sound, but only in Ubuntu (This is one hell of a problem)"
date: 2008-01-13
forum: General Help
---

### Post by KARaidl on 2008-01-13
The other day I reached over and touched the knob on my speakers to turn up the sound. I got a bad static shock and I heard a pop come from my speakers. Ever since then they don't get very loud in Linux, to the point where I can barely even hear some YouTube videos without putting my ear against the speakers.

I thought for sure I had blown them out until I booted into Windows XP, and the sound is working perfectly.

What in the hell happened to Ubuntu? Did the static send some sort of a signal to the operating system?

---

### Post by mccorkle on 2008-01-14
There isn't much in the OS that static can affect that wouldn't be fixed after a reboot.  What kind of speakers do you have?  Are they Logitech or any of the other USB only speakers?

---

### Post by articpenguin on 2008-01-14
is your PCM set to high? I got static sound from my speakers until i found PCM was up the highest. I turned it down and no static:)

---

### Post by KARaidl on 2008-01-14
Articpenguin, you misunderstand. I'm not getting static sound from my speakers at all - The issue is that the volume is by far not as loud as it was. In Windows XP, it's perfect.

Mccorkle, my speakers are JBL, and no, they're not USB. As for rebooting, I never leave my PC on for more than a few hours.

Like I said, the sound used to be perfect until I reached over to the knob on my speakers and got a static shock. Now the sound is very low only in Ubuntu, not Windows XP.

---

### Post by ljd65536 on 2008-01-14
I had a similar problem with an ensonic sound card. It turned out to be a switch setting that was in the wrong position. Did you check all the switch settings?

---

### Post by KARaidl on 2008-01-15
My sound was PERFECT until that little static shock. From **right there** my problems started. I have not touched any switches and everything has been turned all the way up.

I'm asking for someone to please point me to a sound configuration file or something like that. What else could be done?

---

### Post by hardyn on 2008-01-15
well if the sound is working in windows, i think that elimates the speakers; and as the shock was though the speakers not the motherboard, i would say it would have eliminated any possiblity of a hardware fault.

I think you should be looking at the mixer settings, perhaps something coincidental has occured?  there are two sound tabs, one for ALSI and another for the legacy driver (acronym escapes me) make sure that volume is up for both, this has caused me trouble in the past.

*thought*

what about the cables or connectors, try bending the wires around, perhaps you move something around on your desk when you use linux and it improving a faulty connection?

---

### Post by KARaidl on 2008-01-15
Aha! Found it after it occurred to me to right click the volume control on the taskbar. I cranked up the settings and my sound is now back up to where it was.

But I swear I've never seen that control panel before. Never opened it, never messed with it. Weirdness.

---

