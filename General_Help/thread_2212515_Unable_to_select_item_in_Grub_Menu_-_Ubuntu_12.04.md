---
title: "Unable to select item in Grub Menu - Ubuntu 12.04"
date: 2014-03-21
forum: General Help
---

### Post by Danial on 2014-03-21
Hi,
Thanks in advance for your time and help.

I recently installed 12.04 on a dual boot machine along with Win7. Except for unsuccessful Java update, everything else work fine. Both OS booted properly. However, last night, I had to reset the BIOS on PC and now when I boot, I can get to Grub boot menu but unable to select any item; first line is highlighted (Ubuntu 12.04) and after 'default wait time' system boots into Ubuntu 12.04. Before I was always able to use Up/Down arrow keys to select the OS and <Enter>. Just an FYI, my key board is working fine - (before and after booting into OS). I have tried to use Up/Down arrow keys on num pad (yes - by turning off num lock button) and any other possible combination to no luck. I also checked (and toggled) num lock option in BIOS.  I have NOT tried "Boot Rescue" or "Boot-Repair" yet. Your advise and input needed before I use that. If nothing possible, I can always re-install the OS (since I don't have much installed on it (not yet).  

Any help is very appreciated.

Danial

---

### Post by grahammechanical on 2014-03-21
I do not think that boot repair can fix this. I do not think that this is anything to do with Grub. Please explain what you mean by "my keyboard is working fine - (before and after booting into OS)." I thought the problem was with the keyboard up/down arrow keys not moving between the options in the Grub boot menu. If that is correct then your keyboard most definitely is not working fine before booting the OS.

The clue to what is wrong is in these words:

> [COLOR=#000000] I had to reset the BIOS on PC and now when I boot, [/COLOR]

Something changed in the BIOS settings. If I was having this problem there would be a couple of BIOS setings I would look at.

> USB Configuration>Legacy USB Support: Allows you to enable or disable support for legacy USB devices. Setting to [Auto] allows the system to detect the presence of USB devices at startup. If detected, the USB controller legacy mode is enabled. If no USB device is detected, the legacy USB support is disabled. 

Now it seems to me that if the keyboard is USB and I want it working before the OS is loaded then I would want this setting enabled. I think that a USB keyboard is a legacy USB device.

I would also look at the settings for Plug And Play OS support.

Regards.

---

### Post by Danial on 2014-03-21
Thanks for your time and response.

When I stated that keyboard is working before and after, what I meant that if I go to BIOS I am able to use it there as well after when system is booted. Yes, you are right, keyboard is USB too. I thought about swapping the kbd with one of old clunker just to test but got distracted and forgot. However, as you explained settings for legacy usb device in BIOS; now I will check the BIOS settings again for that matter before I do anything else. It will be couple of hours before I get to my putter. I will post back with results. I am very sure this is the case what you just explained. 

I very appreciate your time and guidance for this matter.

Thanks,
Danial

---

### Post by Danial on 2014-03-21
Sir,
Thank you very much for your help. I am able to resolve the issue by following your guidance. It was BIOS setting. Once again, your help is very appreciated.

Danial:D

---

