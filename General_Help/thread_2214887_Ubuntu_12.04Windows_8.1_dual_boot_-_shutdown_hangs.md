---
title: "Ubuntu 12.04/Windows 8.1 dual boot - shutdown hangs on both systems"
date: 2014-04-03
forum: General Help
---

### Post by LifeEnemy on 2014-04-03
Hi all,

I have an Acer V5-572G with Ubuntu 12.04 and windows 8.1 set to dual boot off an SSD. There's a HDD I use for storage as well. I'm having problems with shutdown/restarts on both systems, and I suspect they may be related. Neither of these issues happen every time I shut down or restart, but they are frequent.

On Ubuntu, the system will hang on the purple shutdown screen with the Ubuntu logo. Pressing escape, I see a black screen with some code. It seems like some process fails to shut down, though I'm not very knowledgeable. "USB device" is mentioned as well, though there's none connected. I've attached a picture of the screen.

On Windows, I often get a BSOD when shutting down. I've seen "Unexpected_kernel_mode_trap" and "System_service_exception" error messages. This is rather frustrating is it restarts instead of shutting down, so I need to boot into Ubuntu to actually shut off my computer after a night of gaming. It may or may not be relevant, but when logging in I often see an error message about the last USB device I connected "wasn't recognized" or something similar.

Could there be an issue with one of my USB ports causing all this???

This is very frustrating, as the SSD means my boot time is great! I'd like it if shutting down didn't take 10 times as long though.

Thanks for the help!!

---

### Post by LifeEnemy on 2014-04-10
Bump.

Did my image not post?? Let's try again.
[IMG]http://i183.photobucket.com/albums/x312/LifeEnemy/2014-04-03104327.jpg[/IMG]

---

### Post by oldfred on 2014-04-10
That says something about ClamAV, are you running a virus program and it is the issue?
I do not have that so do not have any suggestions.

---

### Post by LifeEnemy on 2014-04-11
I have ClamAV installed in case I need to scan something. I don't think it's running though, it's not listed in the processes.

It seems as though the line after that, terminating all processes, is the one that fails. The bottom linese say USB and make me think something is awry there, but I don't know what they mean.

On windows I do get a message about "the last usb device you connected was not recognized" when I start without connecting anything. Could one of the USB ports be bad and that's what causing this??

edit- just realized I already asked about the USB :p

---

### Post by oldfred on 2014-05-12
The last entries are USB related. What is plugged into USB?

lsusb
With lots of details
lsusb -vvv

---

### Post by LifeEnemy on 2014-05-14
That's just it, nothing is plugged in =/

Here's the output from lsusb. The '-vvv' had so much output I couldn't even see it all after scrolling up in the terminal. Let me know if it would be useful and I'll post what I can.

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b3d6 Chicony Electronics Co., Ltd

---

### Post by oldfred on 2014-05-15
Is the hub shown just the internal to motherboard or do you have an external hub connected?
What is Chicony, your mouse or keyboard?
Have you enabled USB support in UEFI/BIOS? some systems require you to turn that on, my old BIOS system has specific entries for both keyboard & mouse as USB. New systems may just have one USB entry.

---

### Post by LifeEnemy on 2014-05-20
> **oldfred said:**
> Is the hub shown just the internal to motherboard or do you have an external hub connected?
What is Chicony, your mouse or keyboard?
Have you enabled USB support in UEFI/BIOS? some systems require you to turn that on, my old BIOS system has specific entries for both keyboard & mouse as USB. New systems may just have one USB entry.

I don't have anything connected-- no USB hubs or mouse/keyboard.

I don't know what Chicony is. A quick net search suggests it might be the webcam. I don't see Chicony on the screenshot though, perhaps I'm just dense?

I didn't see any USB option in my BIOS.

---

### Post by oldfred on 2014-05-20
I think this was only Gigabyte motherboards. But settings in BIOS for USB may not say USB.
  BIOS - enable the IMMOU so USB2 ports work
User had settings for USB to only work in certain boot modes:

 BIOS settings need USB mouse & keyboard, USB detection turned to "UEFI Only"

Not sure what else to suggest as it varies so much by system.

---

### Post by LifeEnemy on 2014-05-26
I've upgraded to 14.04 (which is having some of it's own issues, hopefully to be fixed in 14.04.1. Guess I should've waited a bit longer). If the problem persists I'll post back, as I haven't noticed it quite yet.

---

