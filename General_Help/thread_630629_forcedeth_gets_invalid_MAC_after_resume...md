---
title: "forcedeth gets invalid MAC after resume..?"
date: 2007-12-03
forum: General Help
---

### Post by Trebaruna on 2007-12-03
Recently I've been able to mostly get suspend to work on my desktop, and things seem fairly alright when I resume, except that foredeth cannot properly get my NIC back up.

If I check dmesg it mentions that forcedeth received an invalid MAC address, and therefore is assigning it a random one. This MAC it receives is invalid because it is the correct address backwards. A subsequent suspend/resume cycle is no problem: forcedeth gets the correct address, and all is well.

Curiously, when I use network-manager-gnome it gives me something like eth10 (with the random MAC), while without it (using /etc/network/interfaces with or without a defined MAC) it cannot get the interface up at all.
The board is nForce4 AMD based.

Is there maybe another driver for this chipset, or a way to automatically tell it to use the correct MAC every time? More detailed info can be provided if required. Many thanks!

EDIT: after some more Googling with different keywords it would appear some board makers have reversed the order in which the MAC is stored (nForce stores it in reverse, boardmakers try to put it back to normal). This breaks the driver. Okay, fine. So now I'll be looking at a way to automatically set MAC straight after wake-up.
Sorry for not "STFW"-ing enough...

---

### Post by Richie_ on 2007-12-10
I've the same issue, noticed a couple of days ago when I thought someone else had ssh'd to my server.

According to LKML someone had this issue a year ago when netbooting. The fix was to store the mac in the right order. I suspect the order is read opposite to what is stored, and that is why it works every other time, and the other times the driver simply generates a random mac, since it is invalid.

I submitted a bugreport to launchpad, but I don't know if they can do anything about it, since it's a kernel thing.

Actually I don't know where to go with this.

---

