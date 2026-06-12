---
title: "Fixed LiveCD Hang with ACPI=ht"
date: 2007-01-19
forum: General Help
---

### Post by Gobboman123 on 2007-01-19
My computer had been running Ubuntu happily for months when all of a sudden it started hanging at the login screen.  The mouse wouldn't even respond to movement.  I said, meh I'll just install again, so I booted up my Edgy livecd and it froze up soon as it hit the main desktop (keyboard and mouse at least, as the clock was still running in the corner).

I played around with a few things to no avail, eventually downloading a Gentoo LiveCd to see how that worked.  Everything booted fine, except my keyboard wasn't working, so I looked that problem up on the Gentoo forums and somebody mentioned having acpi=ht fixed his problem.  I tried that on Gentoo, and everything worked.  I thought maybe that would fix my Ubuntu error somehow so I gave it a try, and lo and behold it worked.

My question is how can my system have functioned for so long without that option enabled, and then all of a sudden stop working completely.  I haven't changed any hardware in a long time.

I do have a processor with HyperThreading and I believe that it was enabled in my Ubuntu install.

---

### Post by Gobboman123 on 2007-01-21
A little help please?

---

### Post by erothoff on 2007-01-22
Did you recently do a kernel update? My computer was working fine with the noacpi option, and then I when to the newer kernel, and now 2-3 times my computer freezes at boot on ACPI:Assume root bridge [\_SB_.PCI0] bus is 0

I will try the acpi=ht to see if that gets through the problem. From all that I have read, it is a combination problem of issues with changing frequency speeds and dual core processors...

---

### Post by Gobboman123 on 2007-01-22
I believe that I may have gone through a kernel update.  I cannot remember completely.  I know that it did come after one day when I did some updates.  I ended up downloading another liveCD to see if maybe it was a problem with my disc, but it had the same problems too... though I'm not sure if they update the kernel on the liveCD that often?

---

