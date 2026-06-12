---
title: "How to start from SCRATCH?"
date: 2015-06-05
forum: General Help
---

### Post by riverguy99 on 2015-06-05
Got 12.04 running sweetly on 5 machines.  One just got a full load of veggie juice into the keyboard it apparently it did some major damage.  It's a Dell D630 laptop, docked to external display and keyboard, and after the accident, tapping any key would just make indescribable weirdness happen on the display.  I tried another keyboard, plus the one on the laptop. So then I did a fresh install of 12.04, and the same glitches are happening with that!  So I'm assuming that the bowels of the computer got damaged beyond what a fresh OS can fix.  Is there a way I can repair the BIOS on this thing?  Is there hope?

Thank you!

---

### Post by VMC on 2015-06-05
Here's a [youtube]("https://www.youtube.com/watch?v=zTPebVcfKRs") on how to disassemble Dell D630. Look for removing the keyboard section, and maybe just wiping/cleaning the keyboard off would suffice. You could go ahead to the motherboard to see if anything else is wet.

---

### Post by tgalati4 on 2015-06-05
It's not clear from your post, did you spill veggie juice into the laptop or into the external keyboard?

---

### Post by riverguy99 on 2015-06-05
The juice got spilled into the external keyboard.  New issue, though, now when  have the laptop running undocked, it works fine.  As soon as I plug it back into the dock, which has always worked great, it goes weird and the keyboards, external or laptop, no longer work. It's the correct Dell port replicator that I use on all of these machines.  Never had a bad one before.


UPDATE:  I removed the port replicator Had to use a different display cable and different display settings) and just hooked everything back up without it and it all seems to work now. I guess Dell Docks do sometimes fail, but it's still hard to imagine why a keyboard soaking could do that.  Maybe it was the ginger in the veggie juice?

Thanks, Ubuntu friends, and I'll mark this one solved.

---

### Post by tgalati4 on 2015-06-06
The replicator exposes the computer bus to the outside, so any short to the connections can cause issues.  It's possible that you blew an internal fuse on the replicator port.  It may be repairable, but you would have to dismantle it to see there is any obvious damage to the circuit board.  The keyboard typically runs at 5 VDC, so it's hard to imagine damage caused by a 5VDC short, but veggie juice is known for its energetic properties.

---

