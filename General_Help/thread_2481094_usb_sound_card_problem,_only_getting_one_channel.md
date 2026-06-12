---
title: "usb sound card problem, only getting one channel"
date: 2022-11-18
forum: General Help
---

### Post by porphyry52 on 2022-11-18
Lubuntu 20.04 on Gateway notebook

The internal sound card has no linux driver, so I am using a Sabrent usb device which lsusb lists as 
```
Bus 001 Device 004: ID 0d8c:0014 C-Media Electronics, Inc. Audio Adapter (Unitek Y-247A)
```

I get sound, but apparently only one channel. Dialog is ok, but for music usually the vocal channel is very faint and far away sounding.
 I have used this device before on Lubuntu, quite satisfactorily.

alsamixer output for this device is shown in q.jpg attached. I assume that the "Item" line, showing 2 decibel gain values, indicates 2 sound channels are detected.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291261&stc=1[/IMG]
So I have 2 questions. How can I make this card the "default" card? As it is, every time I reboot, I have to run alsamixer, press F6 and select it manually.
How can I get both sound channels?

---

