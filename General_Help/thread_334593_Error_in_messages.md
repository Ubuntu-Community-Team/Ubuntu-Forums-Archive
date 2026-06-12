---
title: "Error in /messages"
date: 2007-01-09
forum: General Help
---

### Post by SamBessey on 2007-01-09
Hi

Should I be concerned about this error I keep seeing in /var/log/messages?

Jan  7 16:57:32 sam kernel: [17180509.264000] spurious APIC interrupt on CPU#0, 
should never happen.

I am running the following hardware config with no immediately obvious problems...

Athlon XP 1900+ 
Abit KR7A (No VIA chipset drivers or anything installed (If they exist?!))
512MB Crucial DDR
ATI Radeon 9700 PRO (With drivers installed and XGL & Beryl working)
Intel 10/100 NIC (Works fine)
Netgear Wireless NIC (No drivers installed, will remove next time I open system)
Hercules Game Theater XP Sound Card (No drivers installed, replacing with M-Audio card)
Hauppage WinTV Analogue card (Will remove next boot, no drivers installed)

The error doesn't seem to cause any problems but I would like to get rid of it if I can... Any ideas as to what's causing it? :-k 

Thanks

---

### Post by hal10000 on 2007-01-09
APIC is buggy on many mainboards, so you might disable it on the bootprompt with the [COLOR="Red"]pci=noapic [/COLOR]option.
Maybe the correct option is just [COLOR="Red"]noapic [/COLOR] instead of pci=noapic
If it works on the boot prompt, you can add it to your /boot/grub menu.lst

---

