---
title: "Assistance with reboot issue"
date: 2016-09-11
forum: General Help
---

### Post by lsutiger on 2016-09-11
I have a new install of 16.04 on a laptop I want to use as a media server. It seems every time I do a restart, the system will reboot, show the BIOS screen, the hard drive light blinks a couple of times then I get an 'Ubuntu purple-ish' background color with no cursor. It does not boot and freezes there. In order to boot I must power down and power up. I then get the choose the OS. Ubuntu is the only OS on the system and had to create an UEFI partition. I had to add noacpi in the grub menu in order to install and to boot. 
How can I troubleshoot what is happening here?

---

### Post by henrixd on 2016-09-11
You can try to press and hold the shift key during the early boot. It should get you to your grub menu. But no matter how you get there, you can choose 'Advanced options for Ubuntu' which will let you choose recovery mode. This hopefully gives you more information.

If this wont help, you can press 'e' when you have 'your' Ubuntu menu entry highlighted. So you can change your kernel boot options and after editing boot with F10 (if I remember correctly).

It this won't help you have to get some boot disk ready, like Ubuntu installation media and boot your laptop with it and mount your hard drive partitions and debug from there.

---

### Post by ajgreeny on 2016-09-11
If your machine is using UEFI and not legacy BIOS (or CSM as it is sometimes known) you may have to repeatedly press Esc at power-on.

However, if that does not work, see Boot-Repair in my signature below and follow the instructions there to run the Boot-Info-Script. If you can get into your installed OS you can run it from that; no need to boot to a live system.	
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and may show us some reason for the problem.

---

