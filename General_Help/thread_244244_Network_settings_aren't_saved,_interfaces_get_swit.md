---
title: "Network settings aren't saved, interfaces get switched?!?"
date: 2006-08-26
forum: General Help
---

### Post by alanfranz on 2006-08-26
Hardware: Dell Latitude D810 ( Pentium M Centrino, 1GB DDR2 RAM, Broadcom ethernet, Intel BG2200 wireless adapter)

Hello,
I recently installed Ubuntu 6.06 . Clean install, no problem at all. The B2200 and the broadcom ethernet were working out of the box, but it seems impossible to save settings permanently! what happens:

1) eth1 and eth2 (those are the names assigned to my network interfaces) get randomly switched, i.e. sometimes eth1 = ethernet and eth2 = wireless, and viceversa.
2) whenever the switch happens, and even sometimes when it doesn't, the wireless card loses its settings (ssid and wep key).

What baffles me is that this behaviour is random. Sometimes the network cards keep their names and settings, sometimes they don't.

I've seen other posts complaining about switched network cards in ubuntu, but it's not my case: ethernet and wireless devices are always correctly found and shown, it's just they seem to be rescanned again at every boot.

---

### Post by nephish on 2006-08-26
what you may need to do is do an lsmod and see which driver is being used for what card. Then in the /etc/modprobe.d/aliases file, add an alias entry for that specific card. 
for example, lets say your box boots up and eth0 is assigned to an onboard nic. so in lsmod, you find via_rhine loaded. This happens to be what you want, so you add a line to /etc/modprobe.d/aliases that reads

```
alias eth0 via_rhine
```

that way, whenever it boots, it will always assign eth0 to be that same nic.

use [www.google.cin/linux](www.google.cin/linux) to find the module for your kernel and nic, make sure its there in lsmod, then add your line.

let us know if this helps.

---

### Post by alanfranz on 2006-08-27
I tried and it doesn't seems to work. I activated both network interfaces from the ubuntu network manager, and then I did an lsmod. The broadcom gigabit ethernet seems to use the tigon3 (tg3) driver, while the intel bg2200 uses the ipw2200 driver: if I try rmmodding them, the device stops working.

By the way, I added the following lines to the 'aliases' file and rebooted:

> 
alias eth1 tg3
alias wifi1 ipw2200


but without success. The network devices suffer from the same problem, the aliases file just seems to be ignored.

---

### Post by marko on 2006-08-30
Check out /etc/iftab.  That defines which card is which based on MAC address.  Maybe that will do the trick.

---

