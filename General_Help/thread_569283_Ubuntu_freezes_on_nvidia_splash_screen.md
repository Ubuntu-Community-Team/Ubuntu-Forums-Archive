---
title: "Ubuntu freezes on nvidia splash screen"
date: 2007-10-06
forum: General Help
---

### Post by theShaggy on 2007-10-06
Okay, I'm confused.  I installed the new Nvidia drivers the other day (as of October 1st, whichever driver number that happens to be).  Everything seemed to work fine without a problem.

Since then, I haven't done much outside of remove some orphaned packages and residual files and such.  Still, I wasn't having any problems at all until now.  I was using Cedega and playing City of Heroes, when inexplicably the computer froze.

I rebooted, since that always seems to help, but instead got a blank screen following the Ubuntu status bar.  After a few reboot attempts, it now loads to the nvidia splash screen, but that's it.  It just hangs.  I haven't tried leaving it for 20 minutes (as I'm told sometimes works), but I have tried to turn off acpi in Grub with no luck.

I have also attempted to reinstall the drivers through command-line Envy in the kernel recover mode, with nothing changing.  I'm quite perplexed, since I can't figure out what caused it in the first place.

My specs, to the best of my ability:

AMD64 Athlon 3700+ running Feisty 32-bit.
MSI motherboard model RS482 (and I know that they have had issues with this motherboard in the past)
1 gig RAM
Nviida Geforce 7300 GS PCIexpress

I don't have my xorg.conf right now because I'm on my Windows partition, and am still a relative linux newb, so don't know how to save it on the command line, and trying an older kernel doesn't want to work (gives me a "Soft Lock" error after trying to load Samba drivers).

Any help?  Anything else you want or need to help me out here?

---

### Post by dcstar on 2007-10-07
> **theShaggy said:**
> 
.......
Any help?  Anything else you want or need to help me out here?

CTRL-ALT-F1 or F8 when it stalls, you may be able to see the last item loading.

---

### Post by theShaggy on 2007-10-09
Thank you!  I still don't know what happened, but after a little while the thing started up again, and now works fine.  I'm thinking that perhaps the card overheated a bit and needed to cool down, but that is just me and my random guess.

---

