---
title: "Envelopes Print Backwards in OpenOffice.org"
date: 2008-07-02
forum: General Help
---

### Post by chrisolof on 2008-07-02
Does anyone know how to tell OpenOffice.org to print an envelope return-address first (basically print left to right)?  Right now, no matter what settings I change (and I haven't found anything that seems to address this specifically), my return address is getting cut off of my envelopes due to the OpenOffice.org printing addressee first.  It's annoying and only happens with envelopes.

Maybe to illustrate this better, imagine if you printed your document and the printer started printing the bottom of the page first, finishing with the top.  This is essentially what's happening when I print envelopes.  If I was only able to print them out the opposite side first (return-address first), nothing would get cut off because the top margin limitation of my printer is way smaller than the bottom margin-limitation (.25in top opposed to .75in bottom).

Back in the day when I used OpenOffice.org in Windows XP, the printing situation was correct - envelopes printed left to right (return-address, then addressee).

Yes I realize that I could move the return-address text over to the right so it doesn't get cut off, but it just looses all chance of looking professional at that point, which is why I'm asking for help.

Also strange is the appearance of a fine line at the bottom of the envelope when I print at "Normal" quality - further adding to the unprofessional look.  In "Draft" mode there's no line, but things are a tad too faint.  This line problem was not there in Ubuntu 7.04.

Any help is greatly appreciated.

---

### Post by jsmumma on 2009-03-30
> **chrisolof said:**
> Also strange is the appearance of a fine line at the bottom of the envelope when I print at "Normal" quality - further adding to the unprofessional look.  In "Draft" mode there's no line, but things are a tad too faint.  This line problem was not there in Ubuntu 7.04.

I noticed the same problem, but have not been able to find anything online about it. I think it first manifested itself when I upgraded to 8.04, but I'm not sure. It is still there in the i386 8.10 with OpenOffice.org 2.4.1.

It appears that each pixel of the line is "on" (ink) if all pixels on the (envelope) page above it are "off" (no ink). That is, it is a NOR function of all pixels in the same vertical line. Any ink printed in this vertical line causes the corresponding pixel not to be printed in the line at the bottom of the envelope. Consequently, it appears as a solid (unbroken) line between the return and main addresses and as rare dots below the addresses, depending upon how the ink and spaces of the address lines line up vertically.

---

### Post by chrisolof on 2009-03-30
Odd - my line is consistent the whole length of the envelope - ink above it or not.  Anyway I've learned to live with it and still just load the envelope in backwards when I need to print one.  I almost wonder if it's the envelope template I started with - jsmumma did you build an envelope document from scratch or start with a template from an online resource (as I did)?

---

