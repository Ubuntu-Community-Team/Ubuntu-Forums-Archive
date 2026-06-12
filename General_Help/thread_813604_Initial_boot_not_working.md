---
title: "Initial boot not working"
date: 2008-05-31
forum: General Help
---

### Post by Josh Teeters on 2008-05-31
Hey all,

I've just installed Ubuntu 8.04 via Wubi, and while the installation in Windows went by without incident, I can't get Ubuntu to actually boot up. The first few times I tried to boot into it, I just selected the normal boot option; the loading bar stopped after 3 orange bars, and never moved beyond that, even after I left my PC sitting for a few hours.

I then realized I could hit ESC and boot up in verbose mode, which would be a little more helpful than "hey, my orange bars aren't moving!" So, here's what I've got. On the initial attempt at booting up on a fresh Wubi install, everything loads fine until it reaches the "loading hardware drivers" section. A good bit of that loads fine, but it hangs at this:

[75.300500] intel8x0: clocking to 47395

At this point, nothing worked on my PC; I tried a soft reboot trying all of the key combinations listed in the Wubi Guide, but none of them, even the final one, worked. So, I reset my PC and tried Ubuntu again, using verbose mode. This time the boot-up stalled here (as well as a subsequent attempt):

Kernel panic - not syncing, fatal exception in interrupt

If it's any help, I've had Ubuntu running on this machine before. Previously, though, I installed it normally, i.e. made a partition for the OS and the swap file, booted from an install CD, etc. I never had any boot-up problems when I had it installed then.

Thanks for any help!

---

### Post by ago on 2008-05-31
Try the acpi option. You might need some special boot parameters to boot your machine. If you search the forum for your make and model you might find some hints.

If you manage to boot with special parameters, please consider submitting a bug in launchpad, since the special parameters are normally workarounds but a proper fixed is the best long term solution.

---

### Post by Josh Teeters on 2008-05-31
Hi ago,

I already tried the ACPI boot option; it didn't work either. I don't recall if it stopped at the same point, though. I'll try it again and note that down.

Also, would the ACPI issue be a problem if Ubuntu worked without issue previously with a normal install?

---

### Post by Josh Teeters on 2008-05-31
Update: the ACPI option gives the same problem, i.e. kernel panic. I'm not really sure how to go about searching for my make and model; I built my PC, so it doesn't really follow any specs set out by a company. What hardware would I need to focus on? Motherboard, CPU? All of it?

---

### Post by ago on 2008-06-01
> **Josh Teeters said:**
> 
Also, would the ACPI issue be a problem if Ubuntu worked without issue previously with a normal install?
You can try booting from live CD

---

### Post by Josh Teeters on 2008-06-01
Hey ago,

Burnt the image, tried booting from it, but the boot process stopped at the same spot. 

I realized that I have changed one thing about my PC: I swapped an old nVidia Quadro4 750XGL out for a new(er) Radeon X1650. Would that have the potential to cause a kernel panic?

---

### Post by Josh Teeters on 2008-06-01
I found an old Ubuntu 6.06 CD that I'd used previously, and tried the Live CD on it; Ubuntu booted without problem.

I take it that means my hardware is OK (i.e., not failing) and the problem does indeed lie with the latest version of Ubuntu?

---

### Post by ago on 2008-06-02
> **Josh Teeters said:**
> I found an old Ubuntu 6.06 CD that I'd used previously, and tried the Live CD on it; Ubuntu booted without problem.

I take it that means my hardware is OK (i.e., not failing) and the problem does indeed lie with the latest version of Ubuntu?
It can be, but obviously it is not Wubi specific. In most cases you can boot with special boot parameters, but I cannot help you understand which one to use. You will have to try them all, also in combination.

---

### Post by Josh Teeters on 2008-06-02
Hey,

Yeah, I know; I wasn't saying that it's Wubi specific, but 8.04 specific. ;) I'll check out the boot parameters and give those ago. Thanks for your help.

---

