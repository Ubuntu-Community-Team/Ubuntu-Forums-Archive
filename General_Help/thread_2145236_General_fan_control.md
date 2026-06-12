---
title: "General fan control"
date: 2013-05-14
forum: General Help
---

### Post by mayagrafix on 2013-05-14
Been trying to get control over my PC fans as per instructions on older threads, but believe they are outdated (messages say file not found, unable to read configuration file, command not found, etc). [COLOR="#FF0000"]lm-sensors, pwmconfig, sensors -s, fancontrol,[/COLOR] are some of the commands which seem not to run.  

Are there updated versions of fan control software for 13.04?

I'm keen on getting the computer case fan (that is what the schematic diagram calls the fan port location) to work as additional cooling for my GPU. The fan port was unused on the mobo (I guess Dell thinks case fan not necessary anymore) so I thought it be a good idea to add an extra fan to the GPU for this purpose :>]

Thanks for ur advice.

---

### Post by mayagrafix on 2013-05-16
OK, here is where I'm at:

When I shutdown the PC completely, upon restart the chassis fan starts up and runs continuously, A-OK.

If I put the the PC in suspend mode, on power-up the chassis fan will only turn once and stay off until the next time I shutdown the PC completely and turn on again. Same with reboot, it will stay off even if it was working normally initially.

Anyone know what doc I should edit to get the chassis fan to keep working when I use suspend mode or reboot? 

Thanks.

---

### Post by mayagrafix on 2013-05-18
So I'm starting to think that this is a hardware related problem rather than software caused. Any suggestions as to where I might look for an answer? the bios in this PC has no options for sensors or fans, who would know about altering the bios?

---

### Post by squenson on 2013-05-18
I agree with you, I think something changed in 13.04, although I have a kind of opposite behavior. Since I have upgraded from 12.10 to 13.04, I have observed:
 - If I boot the PC, the fan works fine, it goes to high speed when the processors are busy but goes back to a lower speed when there is less to process;
 - If I suspend and resume, the fan starts at high speed and stays at this high speed forever, even if the processors are used at less than 5%.
I have an HP6830s laptop.

---

