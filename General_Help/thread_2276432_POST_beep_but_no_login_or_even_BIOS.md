---
title: "POST beep but no login or even BIOS"
date: 2015-05-02
forum: General Help
---

### Post by Mark_in_Hollywood on 2015-05-02
On power up, I can hear one beep during POST. Nothing appears on the monitor (desktop). I cannot DEL to the BIOS or F-11 to choose the boot device. Anyone got a clue?

---

### Post by dino99 on 2015-05-02
i remember having met such a case on a desktop with a few hdds, sata1 & pata, and cdrom
the solution was to test the boot process with each device, and finally found that the cdrom was to be blamed

---

### Post by Mark_in_Hollywood on 2015-05-02
The problem developed as a POST with no video or display or raster but one short beep. That told me that the BIOS was working without a problem. But there was no display (or video, or screen image, or raster). There was no Ubuntu splash screen and no picture or screen showing the BIOS settings and options. The screen was dark or blank.

Netsearching for a solution, someone suggested having no new USB devices. When I removed it, that solved the problem. I have the computer back to normal. 

Before the problem, there was no Hewlett Packard "Link-5" dongle wireless device plugged into the 'puter via a Gear Head USB 7 port hub. The dongle connects the wireless mice and/or keyboard to the BIOS. I later learned that HP Link-5 device dongles (adapters) cannot be plugged into a USB hub. They must be plugged directly into a USB port of the computer. That means that HP is not following the USB standards.

Here is where I found some help:

[CENTER]**[Could be bad RAM. Could also be a USB port. IDK why but sometimes computers get stupid and won't turn on while USB ports are used. Unplug all USB's and turn it on. If still no, then try switching the RAM cards. If still no, try a different hard drive, maybe from a different computer. If still no, it may be a BIOS issue and you will need to flash the BIOS. I can't help you with flashing BIOS b/c I've never done it before, but it's supposedly real simple. Google is your friend. ]("https://au.answers.yahoo.com/question/index?qid=20110922212929AA9o8LU")**[/CENTER]



Thank you for your attention.

---

