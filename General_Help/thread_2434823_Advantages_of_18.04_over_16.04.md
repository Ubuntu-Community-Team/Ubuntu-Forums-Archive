---
title: "Advantages of 18.04 over 16.04"
date: 2020-01-11
forum: General Help
---

### Post by lwalper on 2020-01-11
I've been having trouble installing a scanner. When I plug my Epson 3170 into a USB port, nothing happens. When I do the same thing in Win10, just the act of inserting the plug into the port activates the scanner. I'm currently running 18.04 but would consider 16.04 if there may be compatibility issues with the newer OS version. It wouldn't really matter to me which version I use as long as it works. If I could get a couple of other things to work (Accordance in Wine) and some audio editing software I could use this laptop as a native Ubuntu machine instead of doing the dual boot thing. Anyway, my experience in the past has not always shown the most recent "upgrades" to be improvements (not just here . . .), but more change for the sake of change.

Is there a real, justifiable reason to use 18.04LTS over 16.04.6LTS?

---

### Post by CatKiller on 2020-01-11
> **lwalper said:**
> Is there a real, justifiable reason to use 18.04LTS over 16.04.6LTS?
Support for 16.04 ends in April 2021. 18.04 is supported until 2023.

---

### Post by TheFu on 2020-01-11
> **lwalper said:**
>  Is there a real, justifiable reason to use 18.04LTS over 16.04.6LTS?

Depends on your needs.  For me, the only reason to move to 18.04 is for the free, no-hassle, longer support period.  I'll worry about that in about a year.  16.04 here.  I'm still waiting for netplan to have pre/post up and pre/post down capabilities. There are a few other subsystems which need maturing too.

I ended up giving away an Epson printer and scanner primarily because of poor Linux support. Dropped $50 for a Brother all-in-one with a sheet feeder. Brother tends to have much better support. It is only used as a scanner or fax machine.  For printing, I have a $50 Samsung laser.  I've learned over the decade to carefully pick any hardware I buy so that Linux drivers are built into the kernel with all the features I want.  No hunting for drivers from some odd site in Asia or having hardware that just won't work.  

Don't blame Linux for this. Blame Epson. They make the drivers and if it doesn't work, then they didn't make the drivers or didn't make them correctly.  Do you want to give that company any money again?

---

### Post by CatKiller on 2020-01-11
FWIW, support for Apple's AirPrint protocol is being (or has been, I'm not sure) implemented, so any printer that works that way will work regardless of any manufacturer's disdain for Linux support.

After checking, I think AirPrint is there already, AirScan is coming with 20.04.

---

### Post by mörgæs on 2020-01-11
If support for new hardware is the question it's more relevant to install 19.10 than 18.04 or 16.04 (assuming that 20.04 though promising is still too young).

---

### Post by lwalper on 2020-01-11
Thanks all!. I ask because the scanner is a few years old and I just wonder if a "legacy" OS would have better support for the older hardware.

---

### Post by bunny9000 on 2020-01-11
I tend to agree that the newer versions of Linux are more likley to support legacy things. Linux is a difficult one in that regard. You can't go too new because bleeding edge may not have been implemented, but then older stuff tends be folded in over time.

If I were to buy a device to work with linux I'd probably check to make sure it's compatible before purchase.

Windows support in general has gotten a lot better and most of the time if there isn't a drive for some obscure bit of kit by default, someone, somewhere will have made the drivers. 

No1 reason would be security. Safest to keep up with the newest patches, bug fixes, etc.

---

### Post by freebird54 on 2020-01-13
I'm not sure that an answer here would help directly, as your particular machine/setup may differ too much. I would just try a couple of alternatives in 'Live' mode to see how they handle the 'problem'. If you were thinking of installing an alternative anyway, it's not much extra work to try it before committing...

freebird

---

### Post by rsteinmetz70112 on 2020-01-13
With regard to your initial problem, this comment provides some information on a similar problem:
[https://askubuntu.com/questions/1034528/epson-gt-s50-scanner-not-working-after-upgrade-to-18-04-from-16-04](https://askubuntu.com/questions/1034528/epson-gt-s50-scanner-not-working-after-upgrade-to-18-04-from-16-04)

As far as 16.04 being better for older hardware I'd stick with 18.04 and try to fix the problem. If it's a bug as suggested in the above discussion it will get fixed eventually.

---

