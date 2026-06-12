---
title: "Trouble with MP3 player in 8.04"
date: 2008-05-26
forum: General Help
---

### Post by JamesWBrittain on 2008-05-26
Hi!

uname -a:  Linux Ogoglio 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 x86_64 GNU/Linux


Since updating to 8.04, I have been unable to connect my MP3 player.  Dmesg offers the following error messages:

[  648.821035] usb 6-4: new high speed USB device using ehci_hcd and address 4
[  649.824615] ehci_hcd 0000:00:1a.7: port 4 reset error -110
[  649.824620] hub 6-0:1.0: hub_port_status failed (err = -32)


Simply reloading the driver via "modprobe -r ehci_hcd" isn't an option for me because Ubuntu is installed on an external drive, I need that drive to stay on sdc, and reloading the driver doesn't do that.  

Please let me know if you need any further information,
Thanks in advance,
James.

---

