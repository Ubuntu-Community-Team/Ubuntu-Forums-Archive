---
title: "Computer sometimes doesn't go past Bios logo screen."
date: 2019-06-16
forum: General Help
---

### Post by MasterNetra on 2019-06-16
Lately I found that sometimes from cold boot or even a system restart the bios doesn't get past it's logo screen. Usually you turn the computer on the logo screen comes up and after a few moments you get bios options show for a few moments before it loads into the OS. However during these instances it's doesn't even get to showing the bios options and is sitting there unresponsive indefinitely until I hard reset. These occurrences seem to be at random. There is no flashing lights or anything that would indicate that something was wrong just it sitting there seemly doing nothing at all. Thoughts?

---

### Post by TheFu on 2019-06-16
CMOS battery dead?
Might check for a firmware update to the BIOS from the motherboard vendor too.
Some MBs have LEDs that flash error codes. Worth looking for those too. On mine, these LEDs cannot be seen from outside. The case must be opened.

Or it could be a bad cable anywhere inside, power, SATA, GPU ... anything. Reseat all the cables.

---

### Post by Autodave on 2019-06-16
+1 with TheFu: check all cables for proper insertion.  If you have a lot of USB connections, try booting without any unnecessary ones disconnected.

---

### Post by Dennis N on 2019-06-16
You might try a different sata port for your drive. I had one fail with symptoms being the computer failed to post and froze on bios splash display. After checking the existing connections, moved cable to another sata port. System then booted ok.

---

### Post by pqwoerituytrueiwoq on 2019-06-16
If i recall correctly you are using a pretty old system, i think it may be from the time period that KZG and KZJ capacitors were new on the market, those things are lemons
I would suggest you take a look at the capacitors inside the system, there could be some bulging leaking ones

IF that is the issue it can be fixed, but you will need to find replacement caps, i would suggest asking on the badcaps forum for advice there, you will need a heat gun to warm up (not super hot just warm or hot to touch but not burning hot) the board and a soldering iron
probably cost 15-20$ for new quality capacitors shipping from mouser or digikey and then you need to hope that those caps failing has not damaged any other components over time

---

