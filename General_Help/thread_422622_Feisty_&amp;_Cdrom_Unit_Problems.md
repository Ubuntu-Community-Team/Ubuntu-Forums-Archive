---
title: "Feisty &amp; Cdrom Unit Problems"
date: 2007-04-25
forum: General Help
---

### Post by juantovarm on 2007-04-25
Pretty much like the title says, with Dapper and Edgy I had no problems whatsoever with my hardware. When i installed Feisty my computer would take ages to boot. I decided to edit /boot/grub/menu.lst in order to see what the problem was. 

Ata 2.01 configured for UDMA/66
Ata 2.01 failed to set xfermode (err_mask2)=0x40
Ata 2.00 failed to recover some devices.

I decided to unplug my cdrom: lite-on 52246S. Problem solved. Plugged it with my hd, now the problem was in Ata 1.01. Unplugged my cdrom, problem solved. 

Is the problem in grub? would lilo make any difference? Is it a bug? How can i fix this?

System specs:
Intel D865Gsa MB
Intel PIV 2.66 Processor
1.5 gb ram
Lite-on 52246S cd rom 
Lite-on SOHW-1653S DVD/CD rom
Kubuntu 7.04

---

