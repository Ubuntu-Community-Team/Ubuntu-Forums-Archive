---
title: "No suspend, neither to ram nor to disk"
date: 2012-10-21
forum: General Help
---

### Post by Farinet on 2012-10-21
On a Samsung 535-u3c (amd64) notebook in lubuntu 12.10 i do not have any suspend or hibernate anymore. On a portable that's not that nice.

When i do sudpend to ram the computer gets not awaken anymore, i see there is a kind of restarting, wireless led goes on, some flickering on hd, but that's it. No way to get to the screensaver login like it would be normal

When i do suspend to disk, the computer gets awaken, but wireless results in: Deactivated by hardware (says the network information). Hardwarewise enabling is not possible (also because the destinated Fn key - Fn+f12 does not work; no fn-key higher than fn+f3 works!).

On a powerbook g4 with lubuntu 12.10ppc, suspend does not work anymore. There before, in 12.04ppc, it did! There the problem is shared by others who tested the ppc version of lubuntu 12.10 (on real machines, not virtual).

So,i googled a bit about this problem and i found lots of links indicating it, always (or mostly) related to kernel > 3.5. Just to have an idea, if this might be the case, i tried out a live cd of Fedora 17 and a kubuntu live-cd (copied to usb). And it was the same! Then i tried a live usb of LinuxMint Debian 13 and: suspend worked.

Now, i'm pretty much helpless, what i could do, i love lubuntu, also for its esthetics. I studied the acpi related pages of ubuntu help, installed some tools they suggested but i didn't get to any obvious solution.

Footnote: there are other serious problems like gparted which always ends in failing trying to format usb sticks (on 12.04 it does not! - i saw there was published a bug: something like an udisk error - i don't have in mind exactly right now), the function key problem, but the suspend on a portable is an ESSENTIAL!

Anyone out there has has a similar problem and/or an idea, how to deal with?

TIA

---

