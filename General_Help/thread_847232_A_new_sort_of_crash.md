---
title: "A new sort of crash?"
date: 2008-07-02
forum: General Help
---

### Post by martinquested on 2008-07-02
OK, this probably isn't so new that it's never been seen before, but I can't find any current threads describing the same problem I have.

I upgraded from gutsy to hardy back in April.  I have not experienced a system crash like this until today, and today I have experienced it six times.  Basically, the screen suddenly scrambles with a repeated pattern, and the entire computer becomes completely unresponsive to anything except a hard reboot.

I am not aware of anything specific triggering this problem.  A couple of times it had crashed before the system was even fully booted up (no apps were running).  But the first time it happened today, the system had been running for about three hours.  At the moment when it crashed, I was running Firefox (reading a long email and not pressing any keys or moving the mouse much!) and not much else.

I had not run the Adept Updater today, but it does run regularly and so the system was pretty much up-to-date.  Last week I had problems getting the nVidia graphics driver to work on the latest kernel, but eventually managed to download that driver from nVidia and get it working fine.

What I am saying is that nothing significant has changed on this system to make this happen today.

I am writing this on someone else's computer (running a surprisingly stable Vista) because I can't face having my machine freeze again within a few minutes of booting up.

I also tried booting up an older version of the kernel, but can't get that to work with my current nVidia drivers - and the first time I tried it, booting halted with a kernel panic, complaining about some problem with rogue interrupts or somesuch.

Model: Compaq Presario V6030US (V6000 series)
Graphics card: nVidia 6150
MCP51 is the audio or network chip (or both, I can't remember)
Running: Kubuntu Hardy Heron 32-bit (generic kernel)

I've had a look in /var/log/syslog and /var/log/messages and there's no indication of any problem.

Where else should I look and what else can I try?

Thanks very much!

---

### Post by jwcgator on 2008-07-02
(This won't fix your problem) Have you tried doing the sysrq commands to reboot the system instead of holding the powerbutton/flipping the switch?

Press and hold (yes you must hold it the whole time) (LEFT)Alt + SysRQ (usually the same as printscreen) and press (in order, leaving a bit of time between each keypress) R S E I U B.  This usually goes through even if the computer is completely locked up. 

A good way to remember the letters is Raising Skinny Elephants Is Utterly Boring.

Sorry if you already knew this :)

---

### Post by martinquested on 2008-07-02
I was aware of it, had forgotten it, but had also come across it while searching the forums looking for the solution to this problem.  But thanks for the reminder.

The good news is that, after half an hour of being switched off (in case it was over-heating), and then running on the wired network for a while, but now back to the wireless, and with the powerlead connected to a new socket in another room, so far there have been no more crashes.  Maybe it was something as stupid as power supply glitches?

---

### Post by wootah on 2008-07-02
> **jwcgator said:**
> (This won't fix your problem) Have you tried doing the sysrq commands to reboot the system instead of holding the powerbutton/flipping the switch?

Press and hold (yes you must hold it the whole time) (LEFT)Alt + SysRQ (usually the same as printscreen) and press (in order, leaving a bit of time between each keypress) R S E I U B.  This usually goes through even if the computer is completely locked up. 

A good way to remember the letters is Raising Skinny Elephants Is Utterly Boring.

Sorry if you already knew this :)

The funny thing is that I know that that exists, but every time I need to use it I forget the order and characters :(

---

