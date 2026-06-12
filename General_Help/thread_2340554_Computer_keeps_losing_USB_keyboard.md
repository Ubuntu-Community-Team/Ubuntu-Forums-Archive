---
title: "Computer keeps losing USB keyboard"
date: 2016-10-19
forum: General Help
---

### Post by hhall on 2016-10-19
Hi all. 

I have a sudden and huge problem and urgently need help. I still work on the 14 LTS, simply not having had the time to upgrade to 16.

I use an external USB keyboard (not wireless) for my laptop, as the internal one failed a year or more ago. It suddenly misbehaves most disturbingly. At times, the computer does not appear to receive any keyboard input, at others, it takes a minute or more per keystroke. Unplugging and replugging the keyboard does help only occasionally and for a few seconds only. 

The issue only affects the keyboard, not the wireless mouse I also use. If I switch them between USB ports, it still only affects the keyboard. The keyboard itself also does not appear to be the issue: I experience the exact same problems when using a different external keyboard. 

The problem is so bad that I can usually not authenticate updates, put commands in terminal, nor do any work (I use an onscreen keyboard as an emergency solution; installing it was difficult). 

On starting, I sometimes (not always) see the following on screen:

[ATTACH=CONFIG]271684[/ATTACH]

Transcript:

> hub 2-1:1.0: port 2 disabled by hub (EMI?), re-enabling...
usb 2-1.2: device not accepting address 14, error -32
hub 2-1:1.0: port 2 disabled by hub (EMI?), re-enabling...
usb 2-1.2: device not accepting address 16, error -32
usb 2-1.2: device not accepting address 17, error -32
hub 2-1:1.0: port 2 disabled by hub (EMI?), re-enabling...
usb 2-1.2: device descriptor read/64, error -32

Does anyone know what the issue might be and how to solve it?

---

### Post by ajgreeny on 2016-10-19
Is there a setting to enable/disable legacy USB in your BIOS or UEFI settings?

Might be worth trying the other setting to the way it is at the moment, whichever that is.

Is it a standard USB2 port or are you trying to use a USB3 port?

---

### Post by hhall on 2016-10-19
Hi. I think it's USB 2. Can you elaborate on how I might change the BIOS or UEFI settings? I'm not really familiar with that. Thank you. HH

---

### Post by ajgreeny on 2016-10-19
When you boot the computer you will.normally see a quick message at the bottom, something like "Use Esc or Del to enter setup".  It could also be an F# key, and if you see no screen message lok in the motherboard manual.

Once in search for any USB settings changes you can make and try them one by one.

---

### Post by hhall on 2016-10-20
Hi again. 

In the boot menu, it also does not react to the keyboard (except getting me there in the first place). I end up seeing the following, but unable to do anything.

---

### Post by hhall on 2016-10-21
Bump. Has anyone else experienced this problem - and perhaps solved it?

---

