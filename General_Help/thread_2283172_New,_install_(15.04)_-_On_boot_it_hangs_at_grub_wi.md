---
title: "New, install (15.04) - On boot it hangs at grub with USB IR Receiver plugged in"
date: 2015-06-19
forum: General Help
---

### Post by mr_si on 2015-06-19
It doesn't hang so much as offer boot options which I can't see (and don't want)


Because the PC (Dell Optiplex Core2) is displaying through a gfx card to HDMI I never get to see it POST or see grub options - with my previous distro (KUbuntu) it did the same thing and I got to have a look at the boot sequence through the onboard VGA. Press enter to get it boot using the default option works fine.


By trial and error, having disconnected the IR receiver thingy it boots just fine. I did edit grub to tell it to have 0 timeout, didn't make any difference.


The IR Receiver is one of those ubiquitous ebay jobbies, works fine otherwise.

lsusb lists it as Xenta SE3480 PC Remote Control

Thanks...

---

