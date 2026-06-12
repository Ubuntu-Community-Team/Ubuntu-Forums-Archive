---
title: "Need guidance on connecting Samsung i700 cell phone with Dapper"
date: 2007-02-24
forum: General Help
---

### Post by Robertjm on 2007-02-24
Hi all.

I've recently switched my cell phone to a PDA type and would like to hook it up to my computer for syncing with Evolution. 

I found some information online, but can't get past the first step.

Using a Samsung i700 CDMA-based cell phone on the Verizon network. It has a cradle which can be connected via the USB port. 

Here's a link to the instruction sheet I was using.:

 [[COLOR="Red"]Samsung i700 as a CDMA Modem in Linux![/COLOR]]("http://pdaphonehome.com/forums/samsung-i700-faq/41005-samsung-i700-cdma-modem-working-linux.html")

He's using Slackware so perhaps that my problem? I can't get past the "modprobe uhci" part. After doing a sudo su to become ruut I try the modprobe uhci and get the error msg

FATAL: Module uhci not found.

The article mentioned that there are two other USB drivers as well, ohci and ehci-hid. When I did modprobes for each of those I got the same error about the respective module not being loaded. 

Am I going to have to recompile the kernel to get this support, or does anyone have a suggestion on how to get the phone hooked up? As I have DSL I'm not so much interested in using the phone as a cell phone modem, but I do want to be able to sync and access its data card.

Thanks,

Robert

---

