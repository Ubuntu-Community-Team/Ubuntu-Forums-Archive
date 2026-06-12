---
title: "Need help figuring out crash"
date: 2019-01-14
forum: General Help
---

### Post by jorgeblasio on 2019-01-14
I've been having complete system freezes for over 6 months and finally now I got logs written to disk.
Symptoms: Random lockups using any app, from just moving the mouse over the desktop to No Man's Sky game. Just crashed while writing this.

I'm attaching the logs.

Thank you!

---

### Post by dragonfly41 on 2019-01-15
I would try [petit]("https://www.tecmint.com/petiti-log-analysis-tool-for-linux-sysadmins/") to figure out patterns in your log files yourself.

---

### Post by HermanAB on 2019-01-15
FWIIW, in my experience, random crashes were caused by pad power supplies.

---

### Post by jorgeblasio on 2019-04-21
Thank you for the response, apparently I'm not being notified by the forums of new responses. Sorry.
The thing is, I have a pretty good power supply (Seasonic Focus Gold Plus 750w). I know having a brand product does not preclude you from having a failure, but this never happened to me on Windows when I used to dual boot.

---

### Post by rbmorse on 2019-04-21
In addition to the PSU itself (and I have the same unit...it's a good one) there are the voltage regulators on the motherboard for the CPU.  The components in the Voltage regulation (VR) circuits on desktop motherboards tend to run hot and will degrade over time.  On laptops, they may have been woefully underspec'd to begin with. When they start to degrade, there may not be much margin for error. 

Open the case, blow out the dust (do this outdoors if it has been awhile) then get a bright light and hand magnifier.  Examine the capacitors on the motherboard in the general vicinity of the CPU.  They look like little beer cans with plastic jackets.  The tops should be flat to slightly concave, and there should be no signs of leakage (white "feathers" or brown goo) and the sides should be straight.  If the part looks "bowed out" as if there is too much internal pressure it means there is too much internal pressure and the device has failed. 

Also, examine the MOSFET devices around the CPU. These may be box shaped or just IC's on a heatsink.  Look for signs of overheating (discoloration or even burned substrate).  Give that area a good sniff...the odor of burned electronic component is unmistakable. 

While you're in there, pop out and reseat each memory module.  It might help.

---

### Post by NM5TF on 2019-04-22
> **rbmorse said:**
> In addition to the PSU itself (and I have the same unit...it's a good one) there are the voltage regulators on the motherboard for the CPU.  The components in the Voltage regulation (VR) circuits on desktop motherboards tend to run hot and will degrade over time.  On laptops, they may have been woefully underspec'd to begin with. When they start to degrade, there may not be much margin for error. 

[COLOR="#FF0000"]Open the case, blow out the dust (do this outdoors if it has been awhile)[/COLOR] then get a bright light and hand magnifier.  Examine the capacitors on the motherboard in the general vicinity of the CPU.  They look like little beer cans with plastic jackets.  The tops should be flat to slightly concave, and there should be no signs of leakage (white "feathers" or brown goo) and the sides should be straight.  If the part looks "bowed out" as if there is too much internal pressure it means there is too much internal pressure and the device has failed. 

Also, examine the MOSFET devices around the CPU. These may be box shaped or just IC's on a heatsink.  Look for signs of overheating (discoloration or even burned substrate).  Give that area a good sniff...[COLOR="#FF0000"]the odor of burned electronic component is unmistakable[/COLOR]. 

[COLOR="#FF0000"]While you're in there, pop out and reseat each memory module.[/COLOR]  It might help.

all good advice from a hardware point of view...for [COLOR="#FF0000"]an experienced person[/COLOR] that understands possible electrostatic discharge damage & how to prevent it....there is also the possibility of damage to memory chip pins doing reseat procedure...caution is advised for the unexperienced...

the OP might want to look at his graphics card as possible source of system freezes...in my experience this has caused me lots of grief over the years...

tommy

---

