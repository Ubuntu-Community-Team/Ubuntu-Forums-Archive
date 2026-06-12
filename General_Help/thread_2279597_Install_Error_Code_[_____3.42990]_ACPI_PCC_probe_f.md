---
title: "Install Error Code [     3.42990] ACPI PCC probe failed"
date: 2015-05-24
forum: General Help
---

### Post by josh134 on 2015-05-24
Good Day All,

   I have a custom pc that I am trying to install Ubuntu desktop on its own hard drive. I already have Windows on a separate hard drive. I'm running the follow equipment - 
[COLOR=#000000][FONT=Verdana]
INTEL I5 Processor
[/FONT][/COLOR]ASUS Maximus V Gene Intel Z77

[COLOR=#000000][FONT=Verdana]EVGA GTX670
[/FONT][/COLOR]Crucial 16GB 8X2 DDR3
Thermalta Smart 750W 
TPLINK 3000MBPS WRLS N PCIE ADAPTER

I've created a bootable USB with the 64 bit version Ubuntu 14.4.02.LTS and I've tried version 15. I keep getting the following errors in different order -

4.303598 ldm_parse_tocblock(): cannot find TOCBLOCK, database may be corrupt


ignoring bgrt: invalid status 0 (expected 1)


acpi ppc proble failed

I'm not sure what this means, but I suspect it to be a problem with hardware compatibility/drivers or a setting in my bios. I'd really appreciate any help.

Kind Regards,
Josh

---

### Post by Dennis N on 2015-05-24
On the ACPI message, it just an advisory that a check for PCC failed to find it. Occurs with newer kernels 3.16(?) and 3.19 I think. I see it too on a couple of our computers. You can google the error ("ACPI PCC Probe Failed") and find details, including what PCC stands for. It doesn't mean anything is wrong. Why we are forced to see this message on every boot is a good question.

---

### Post by josh134 on 2015-05-24
Ok thanks for the response. I will do some more research. I can get the installer to load, but I can't get an install up and running. I've tried the demo and get the afore mentioned error. As well, I've tried just a straight install. Any suggestions?

---

### Post by cariboo on 2015-05-24
Have you tried booting with nomodeset enabled? At the menu screen, press F5 and select nomodeset, then press esc to continue booting.

---

### Post by josh134 on 2015-05-24
I tried that. Do I type that in? Keeps telling me kernel not found when I type it in and hit enter.

---

### Post by plucky on 2015-05-25
> **josh134 said:**
> I tried that. Do I type that in? Keeps telling me kernel not found when I type it in and hit enter.

I think cariboo meant F6 and a list of options should appear.

Press down arrow to nomodeset and hit enter.An X should appear next to the option.

Then press Esc to exit menu.

Good Luck

---

### Post by josh134 on 2015-05-25
Thanks for all the help so far guys. I don't have drop down options on the menu you mentioned Plucky. I can see different options to type in, but not to scroll through from what I can tell. 

I've been using the suggested bootable usb builder pendrive linux I believe. I have the option in the bios to boot to eufi for my usb or in regular mode with the usb. If I boot regular I get multiple options i.e. boot parameters, help, advanced, etc. If I boot in eufi I get only a few options install ubuntu, try ubuntu, oem install for manufacturers, and check disc for defects. Is this what I am supposed to be seeing? 

I've also tried using different usb ports on my machine. Not sure if that helps or not.

---

### Post by josh134 on 2015-05-26
Do you all think I should format the drive I plan to install it on first? I am not sure how to attach screen shots I have taken of the problem, but if I could that would probably help give a clearer picture of what is going on.

---

### Post by josh134 on 2015-05-29
"Solved" Good News! I was able to install Ubuntu from a CD. I have no idea why I couldn't get it to boot from the USB, but that's a battle for another day. Thank you all for the assistance.

---

