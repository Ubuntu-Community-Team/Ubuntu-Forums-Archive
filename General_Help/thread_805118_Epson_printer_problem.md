---
title: "Epson printer problem"
date: 2008-05-23
forum: General Help
---

### Post by ROCValmont on 2008-05-23
I'm running a dual boot system - XP and Ubuntu 7. I've just installed an Epson Stylus DX4450 printer on XP and it worked perfectly. When I booted up Ubuntu it recognised the printer immediately, installed it (clever!) and again, it worked perfectly.  Then I must have done something wrong, because every time I start Ubuntu now, the printer goes dead. How can I uninstall the printer from Ubuntu so I can switch off, start again and get Ubuntu to recognise the printer again?
Thanks..
Robin

---

### Post by shifty_powers on 2008-05-23
type

```
http://localhost:631/
```

into a browser ;)

---

### Post by ROCValmont on 2008-05-25
Thanks for your help - but I'm new to Unix and I don't understand the instructions in the link! Since posting the original query I've discovered how to delete the printer and start again. After deleting the printer (system/admin/printers) I unplugged the usb socket, rebooted Ubuntu then plugged in the USB again. A notice appeared saying Ubuntu had recognised the new printer (Epson DX4400) and loaded drivers for the Epson DX4250. All seemed to be well until I tried to print, when the printer flashed a load of red lights at me and switched off. The printer's still working in XP but I'm trying to switch everything over to Ubuntu if I can, so I'd be grateful for your advice on how to get the printer working. What is mysterious is that it did work when I first installed it - but it's now decided not to! Once again, please bear with me when I say I'm new to Unix so treat me as an idiot!

Robin

---

### Post by Cylence on 2008-05-26
Hello,
I didn't understand if you own a DX4450 or a DX4400. I have the latter, so I'll be talking about that one.
I didn't find a fix to make the Epson DX4400 work flawlessly in Ubuntu. The printer driver one can download from Epson doesn't work (the scanner driver works well with some fiddling, look in the forums for help).
For printing black and white documents the DX4250 driver is fine. It hangs though when trying to print colors or gray scale.
You should use the Epson D68 driver. It works but I think it eats up a lot of ink. The standard quality setting is the only way to go if you don't want some thin horizontal empty lines appearing in your prints.
Another thing you can do if you don't want to dual boot with Windows XP is to create a virtual machine (for example in VirtualBox, but not the Open Source Edition since it doesn't support USB) and install XP on it. It's faster to switch on/off a virtual machine rather than dual booting.
Actually I don't understand why there is no official working driver for Ubuntu yet. I tested the printer on PCLinuxOS and on openSUSE and it works well with the driver you can download from Avasys' website.

---

### Post by ROCValmont on 2008-05-28
Very many thanks for your help. You're right - it does work in black and white, so I think what must have happened is that I booted up Ubuntu, saw that the printer had installed itself, then printed off a quick bit of B&W text just to confirm it was working. It was only when I tried to print some colour stuff later that things went wrong. I've been on to the Epson UK Help(?)Desk and they confirm they don't support Ubuntu with this, or **any** of their printers. Can this be true? Pretty short-sighted if so! I'll now try your alternative driver suggestion and/or try to find another printer/scanner that does work with Ubuntu. Once again, many thanks for your help - very much appreciated.

Robin

Since writing the above I solved the problem by taking the Epson back to PC World, from whence it came, and swapping it for an HP C5180 all-in-one. I installed it on XP, rebooted into Ubuntu Heron, and there it was, working perfectly, without even notifying me that it had recognised the new printer. The moral seems to be, if you want a printer to work faultlessly in Ubuntu, get HP! A pity, because I've used Epsons for years without problems. And a word of thanks to all on these forums - your quick and friendly help is very much appreciated.

Robin

---

