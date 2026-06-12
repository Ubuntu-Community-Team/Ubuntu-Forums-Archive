---
title: "Kensington Orb Hub interferes with HP D7160 printer in any USB port"
date: 2008-05-24
forum: General Help
---

### Post by Fazz Munkle on 2008-05-24
I have two of these hubs and both exhibit the same behavior and this behavior is reproducible. If I plug them in singly or both it seems to interfere with the computer's access to the printer. Plug the hub in one motherboard mounted USB port and the printer in the other then check to see what's connected with lsusb I'll get intermittent connection to the printer (it'll pause before it lists the devices). And it'll list all devices except for the printer. But if I keep entering lsusb after that it brings up the complete list of devices with printer as if the USB bus was woken up. Pause a few moments and hit lsusb again and it does the same. NOTE: This is not doing so while plugging the printer into a hub. I noticed too that if I have things plugged in to the hub (remote control, monitor color calibrator, etc) the lights on the hub light up and go dark at random times. I've tested this with both hubs, powered and unpowered. Plugging in the devices without the hubs connected yields normal operation. lsusb doesn't pause and lists everything (sans the hubs (NEC)). Using hp-setup with the hubs plugged in yields random access to the printer and the program gives me errors saying it can't find the printer. Unplugging the hubs yields normal operation and set up of hp-setup. Plugging the printer into the hubs this time yields the same results. Using the hubs in Windows XP doesn't bring up this problem and the lights on the hubs stay on or when data is accessed.

Thoughts on other causes:

- Power or data short in USB hub? Both?
- Power or data short in USB bus/controller?
- Special USB related software not installed with Ubuntu 8.04?
- Incompatible electronics in hubs? Fundamental flaw?

Troubleshooting tested on Ubuntu 8.04
Hubs are model K33118A
Printer is HP Photosmart D7160

Is this a known bug? Are these hubs known to not work with 8.04? Can you suggest some hubs that work with 8.04?

Please let me know. Thank you for any help or clue with this matter.

---

### Post by Fazz Munkle on 2008-05-26
Nobody have any ideas? Seems like a bug to me if it happens in Ubuntu 8.04 but not in Windows XP or Ubuntu 7.10.

---

