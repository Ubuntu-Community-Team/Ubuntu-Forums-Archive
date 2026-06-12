---
title: "Map udev rules to specific sata ports"
date: 2017-07-18
forum: General Help
---

### Post by crimsonshot on 2017-07-18
A little background, I'm setting up some homebrew hard drive wiping stations running XUbuntu and the shred utility. I'm set up to wipe 20 drives at once using [URL="https://www.amazon.com/Ableconn-PEX10-SAT-Port-Express-Adapter/dp/B0177GBY0Y"]2 of these cards.
[/URL]
I want to map each sata port on the PCI cards to a udev naming scheme (ex. /dev/sda is the boot drive connected to the motherboard, /dev/sdb is the first sata port on the PCI card going all the way up to /dev/sdu for 20 total drives). The goal is to be able to tell when a drive fails or is bad and pinpoint which sata cable it's connected to.

I'm wiping thousands of drives and it takes about 4hrs to wipe a 7200rpm 500GB drive so if anyone has a better solution I'm all ears. The idea is to have a semi permanent solution.

Thanks.

---

### Post by crimsonshot on 2017-07-19
bump

---

