---
title: "Computer not turning on!"
date: 2007-07-31
forum: General Help
---

### Post by era86 on 2007-07-31
This is sort of a general question...

I just got done building a PC that used to work just fine before.  I upgraded the memory and installed a case fan.  Now when I try to power it up, the switch doesn't turn it on!  The motherboard LED still turns on when the power supply is switched on.  What could the problem be?  Any help would be appreciated.  Thanks!

---

### Post by dwasifar on 2007-07-31
> **era86 said:**
> This is sort of a general question...

I just got done building a PC that used to work just fine before.  I upgraded the memory and installed a case fan.  Now when I try to power it up, the switch doesn't turn it on!  The motherboard LED still turns on when the power supply is switched on.  What could the problem be?  Any help would be appreciated.  Thanks!

It sounds like your power switch is no longer connected to the correct pins on the motherboard.  

Usually the switch and LED cluster on the front of the case has a bunch of twisted-pair wires coming from it and leading down to little black connectors that slide onto pins on the lower right corner of the motherboard.  Most of the time these connectors are labeled - POWER SW, HD LED, RESET SW, and so forth.  Check to see that the connector labeled POWER SW is connected to the right pair of pins.  Usually the pin assignments are silk-screened right on the motherboard in teeny-tiny white print.

---

### Post by era86 on 2007-07-31
I tried that out, maybe I have the + and - mixed up.  Is white usually + or is it -?  Thanks so much.

---

### Post by dwasifar on 2007-07-31
> **era86 said:**
> I tried that out, maybe I have the + and - mixed up.  Is white usually + or is it -?  Thanks so much.
For the switches, polarity doesn't matter.  Only the LEDs care about polarity.

---

### Post by era86 on 2007-07-31
Is it possible that this motherboard is fried?  I'm so sad.

---

### Post by dwasifar on 2007-07-31
> **era86 said:**
> I tried that out, maybe I have the + and - mixed up.  Is white usually + or is it -?  Thanks so much.

If you're sure you have the right pair of pins, try unplugging the connector and shorting those two pins briefly with the tip of a screwdriver.  If the computer starts, the switch or its wires are the problem.  If not, then you either have a motherboard fault, or (more likely) the wrong pair of pins.  Sometimes the silk-screened pin assignments can mislead you into thinking the pair you want is on the opposite side of the row.

If the problem actually turns out to be the switch, you can connect the reset switch to the power switch pins and use the reset switch as a power switch from then on.  You'll lose the reset switch's functionality, but you can always cycle the power supply for that if you absolutely need to do a BOS boot.

---

### Post by era86 on 2007-07-31
Thanks for your help, but i think the motherboard is shot.  Could there be any other problems with it?  Perhaps the CPU or any other component.  RAM?  Will the small LED ont he board light up even though it is broken?

---

### Post by dwasifar on 2007-08-01
> **era86 said:**
> Thanks for your help, but i think the motherboard is shot.  Could there be any other problems with it?  Perhaps the CPU or any other component.  RAM?  Will the small LED ont he board light up even though it is broken?
I've seen that LED light up on a nonfunctional motherboard, yes.

Ordinarily bad RAM or a CPU fault will not prevent the motherboard from TRYING to boot, though they will prevent it from succeeding.  

The good news is that motherboards are not that expensive.

---

### Post by fredj on 2007-08-01
Pull all the cards out of the machine and disconnect all the power leads and connections to disk
drives including floppy disk drives. Make sure that all the memory chips are installed properly in
the correct slots.
Then make sure that all the power leads to the motherboard are connected properly. Does the
video card require an extra power connection.
Check carefully the connections of jumper lead for the power switch and the reset switch, pull
all the others including the led and speaker connections.
Then try powering on and see if the bios posts.
Before you do any of these things, relax for a few hours so that you can concentrate on what 
you are doing.

---

### Post by era86 on 2007-08-01
I pulled all peripherals out of the case, disconnected the wires, and went to remove the board.  When I got the board about half way out of the case, I found that there was a loose screw hiding behind it.  I took the screw out and connected everything back up.  Bingo!  Works now.  Thanks for all the help though guys.  Now I know what to check when something like this occurs again.  (Maybe next time it won't be a loose screw!)

---

