---
title: "Computer Does Not Start"
date: 2013-08-31
forum: General Help
---

### Post by King Dude on 2013-08-31
My computer turns on, the HP splash page pops up like normal, but it hangs for an indefinite amount of time. I try pressing Esc to load the boot menu, it will say "Loading Boot Menu..." and will continue to hang forever. If I try entering BIOS, it will not do so.

Any ideas? I'm so angry it's not even funny. I'm going to have my elderly father on my back for the whole damn day if I don't fix this.

---

### Post by TheFu on 2013-08-31
Could be almost anything.
* lazy bits on the boot sector
* bad HDD
* bad SATA cable
* bad disk controller
* cracked motherboard
* failing power supply
* short in any of the components

There are about 10 steps between power-on and seeing a long screen. Could you put as much of those steps into your problem description?  More details are better - every flicker of a monitor matters.

Also, can you boot off a liveCD or USB flash drive to troubleshoot more?

---

### Post by Thee on 2013-09-01
Try removing the HDD, shouldn't be hard, and see what happens then.

---

### Post by King Dude on 2013-09-03
> **TheFu said:**
> Could be almost anything.
Also, can you boot off a liveCD or USB flash drive to troubleshoot more?
Yes and no. You see, on the splash screen I press Esc to choose which device to boot from, whether it's a flash drive or hard drive. But when I press Esc, it does not let me select any boot options. However, when I unplug my hard drive and leaving my father's hard drive plugged in, my computer seems to work normal again.

---

### Post by scbingham on 2013-09-03
Seems the answer is not to use that hdd on that computer. Have you tried that disk on another computer?

I have exactly the same problem with a 500Gb sata disk, unfortunately I can't try it on another computer yet but I have just resigned myself that I can't use it on that particular computer. Annoyingly though, it has worked on occasion, as I was able to format it & mount it, without any errors. Pity as I wanted to increase my storage capacity. :-(

Sorry that I don't have a solution but you may just have to accept the fact that it won't work & get hold of another disk. If yours is a brand new disk or still under warranty I get it tested & replaced if necessary.

I'd be interested to see if/how you resolve it. Good luck.

---

### Post by Thee on 2013-09-03
Then it's probably one of these 2 things:

- Your SATA cable is bad. Try another one.
- Your HDD is dead or is about to die.

---

### Post by protoss96 on 2013-09-03
If your PC is beign shuted down into middle of BIOS upgrading, you can throw away your motherboard right now.

---

### Post by King Dude on 2013-09-03
I looked at my hard drive, and found that a tiny plastic piece meant to secure the power cable has snapped off, and now the power cable wiggles loose. But I doubt that is the problem, since the only reason it would snap off would be my father messing with it to try and fix it, and he didn't mess with it until after it started not working.

---

### Post by scbingham on 2013-09-04
@protoss96 Who mentioned anything about a BIOS upgrade?

@king dude This item: [http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=350852253457](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=350852253457) might give your connector more support. It combines both the data & power connectors.

Hope that's some sort of help.

---

### Post by King Dude on 2013-09-04
> **scbingham said:**
> 
@king dude This item: [http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=350852253457](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=350852253457) might give your connector more support. It combines both the data & power connectors.

Hope that's some sort of help.
That actually help me a lot. Even if I have to trash my hard drive, that connector allows me to have a DVD drive in my computer (since there aren't enough power connectors for two HDDs and a DVD drive at this time, I've had to give up the DVD drive).

---

### Post by scbingham on 2013-09-04
That does actually still use one of the molex (4 pin) power connectors, you probably want one of these too:

[http://www.ebay.co.uk/itm/2-WAY-INTERNAL-DEVICE-POWER-SPLITTER-4-PIN-FEMALE-TO-2-x-MALE-MOLEX-CONNECTORS-/360730631140?pt=UK_Computing_CablesConnectors_RL&hash=item53fd389be4](http://www.ebay.co.uk/itm/2-WAY-INTERNAL-DEVICE-POWER-SPLITTER-4-PIN-FEMALE-TO-2-x-MALE-MOLEX-CONNECTORS-/360730631140?pt=UK_Computing_CablesConnectors_RL&hash=item53fd389be4)

---

### Post by King Dude on 2013-09-05
> **scbingham said:**
> That does actually still use one of the molex (4 pin) power connectors, you probably want one of these too:

[http://www.ebay.co.uk/itm/2-WAY-INTERNAL-DEVICE-POWER-SPLITTER-4-PIN-FEMALE-TO-2-x-MALE-MOLEX-CONNECTORS-/360730631140?pt=UK_Computing_CablesConnectors_RL&hash=item53fd389be4](http://www.ebay.co.uk/itm/2-WAY-INTERNAL-DEVICE-POWER-SPLITTER-4-PIN-FEMALE-TO-2-x-MALE-MOLEX-CONNECTORS-/360730631140?pt=UK_Computing_CablesConnectors_RL&hash=item53fd389be4)
Yes, I do. Thank you.

---

