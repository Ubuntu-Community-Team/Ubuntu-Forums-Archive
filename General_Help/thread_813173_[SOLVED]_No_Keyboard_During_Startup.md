---
title: "[SOLVED] No Keyboard During Startup"
date: 2008-05-30
forum: General Help
---

### Post by Cerin on 2008-05-30
I only have a USB keyboard, and I've found it doesn't work at the initial Grub bootloader screen, so I have no way to select the OS I want to boot. I'm coming from Fedora, and I never had this issue before. Is there anyway to get my USB keyboard working with Grub?

---

### Post by Sam Lars on 2008-05-30
This could be related to your BIOS, you could check that for anything about USB support.

---

### Post by Jalh on 2008-06-12
im having the same problem , any solution ? i can only log in into ubuntu , and i still using xp , any help ?

---

### Post by Cerin on 2008-06-12
Yeah, sorry, it was a bios problem. I'm not sure how I never realized that before. All I did was enable "USB Keyboard/Mouse" support in my bios, and now it works fine. Why would any manufacturer disable that by default?

---

### Post by new2gutsy on 2008-06-12
I'm having the same issue,I'm sure I can find that option if I can get into the bios,how can I get into it when my keyboard does not work untill a OS starts to load?

---

### Post by Cerin on 2008-06-12
It depends on your bios. Surprisingly, I was able to reenter my the bios after Linux had loaded basic USB drivers, so I could use by USB keyboard to enable my USB keyboard :) However, if you can't do that, you may need to temporarily use a PS/2 keyboard. I actually have USB->PS/2 adapter for these rare occasions.

---

### Post by new2gutsy on 2008-06-12
Ok Thnx...I have a PS/2 adapter,I will have to try it when I get home from work.
I hope it works,the woman hates Linux so hopefully I can get her back into Windows :lolflag:

---

### Post by Jonomac on 2008-06-16
I have the USB keyboard turned on in the BIOS but i can not get the wireless keyboard to work.  At the initial startup at the start of grub i can hit buttons and it beeps but doesn't actually do what the button should do like arrow or enter. anyway it would be nice if anyone could help me with this.  This is what lsusb gives (so the thing is recognized but not used)
jon@home:~$ lsusb
Bus 004 Device 006: ID 13b1:0014 Linksys 
Bus 004 Device 004: ID 1058:0901 Western Digital Technologies, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 05fe:0011 Chic Technology Corp. Browser Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 03f0:3b11 Hewlett-Packard 
Bus 001 Device 003: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 001: ID 0000:0000  
****

Thanks in advance for any info anyone can provide.

---

### Post by albythom on 2008-06-16
hey thanks for the bios advice i've had this problem for ages and just used ps2 as extra keyboard now i can disconnect it thanks again:):lolflag:

---

