---
title: "Unable to get past Prompt"
date: 2015-10-02
forum: General Help
---

### Post by conor5 on 2015-10-02
I did something incredibly stupid and ran grub boot-repair on my computer, as I couldn't bring up BIOS on my Ubuntu computer. Since then, once starting, the system will say it cannot Mount various windows partitions and then brings up GRUB prompt (below). 

I don't have Windows installed on this system. When I type 'exit' the system just boots back into grub. I have been unable to boot a usb of Ubuntu to re-install due to my initial issue with  not being able to access boot selector/bios. Is there a way I can reverse this? All information I have found so far relates to dual boots, which I am not doing. 

Cheers!


GNU GRUB
MINIMAL BASH-LIKE line editing is supported. FOR THE FIRST WORD, TAB LISTS POSSIBLE
COMMAND COMPLETIONS. ANYWHERE ELSE TAB POSSIBLE DEVICE OR FILE COMPLETIONS.
GRUB>

---

### Post by buzzingrobot on 2015-10-02
GRUB isn't part of the equation until the BIOS transfers control to it when the machine boots.  Be sure you are correctly trying to trigger entry into the BIOS setup screen before you attempt something more drastic. 

Power down the machine completely. Turn it back on and then try again with the appropriate keystroke for your BIOS.

---

### Post by conor5 on 2015-10-07
Hi,  thanks for your reply! I gave it a try again and cannot get BIOS to boot. I'm certain I'm using the correct trigger key, but with no joy. Is there a command I can use on Grub to boot the system into Ubuntu from the menu I'm getting?

---

### Post by lisati on 2015-10-07
Since this is a support request, and not a casual chat topic,
*Thread moved to **General Help**.*

---

