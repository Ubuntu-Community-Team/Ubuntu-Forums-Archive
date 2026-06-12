---
title: "Laptop crashing after restoring from suspend, after kernel updates"
date: 2024-07-29
forum: General Help
---

### Post by raif on 2024-07-29
My laptop freezes then crashes a minute or so after restoring from suspend and, this is the really odd bit, then goes into the BIOS utility. The only way to exit the utility is to power off. I've never had a crash like this in 15 years of Ubuntu. I have tried to look at logs but they just stop at the crash.

I've searched for similar bugs and this is the nearest I found, as I'm also using an AMD Ryzen with Radeon Graphics, except that this bug happens for me from the first (and only) attempt at suspend and only seems to be due to more recent kernel updates. [https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-5.19/+bug/2008774]("https://bugs.launchpad.net/ubuntu/+source/linux-signed-hwe-5.19/+bug/2008774")

I'm using Ubuntu 24.04 and this first started happening with the 6.8.0-35 kernel (which also caused power consumption regressions, now fixed) but at least I could boot with an earlier kernel to avoid the problem. Then 6.8.0-38 seemed to fix it but it's happening again with 6.8.0-39 and also -38 if I try to boot with that now. I do not have a clue what is going on or how to diagnose the problem. I'm no longer confident in my assumption this was a kernel regression that would be fixed. 

Any help much appreciated as having a laptop without suspend working is really annoying.

---

### Post by hessajee on 2024-08-16
My issue is not exactly the same as yours, however I thought I'd share my situation and what I've found so far.

I'm running Lubuntu 24.04 LTS. When I suspend either via the terminal or GUI, it looks like it is suspending but instead it seems to be shutting down or restarting upon pressing any key. I say this because I see the boot screen when I "resume" the laptop. I have onboard graphics so our situation or the ones in the link shared don't necessarily match. 

I've found the following [post]("https://forum.linuxconfig.org/t/suspend-bug-for-ubuntu-24-04lts/7853/8") which seems to say for Ubuntu 24.04 LTS users, there is a newer kernel 6.10.3-061003-generic which one can update to that may help resolve the situation. I think this is a mainline kernel rather than a LTS kernel. I believe the latest LTS kernel is 6.8.0-40-generic but I'm not sure where to go to confirm it is the case.

As I'm still new and transitioning to Ubuntu, I don't wish to carry out the kernel update just yet as it seems that I have to manually undertake kernel updates if I choose to take this path. I followed the [instructions here]("https://ubuntu.com/kernel") to check which kernel I'm running: Ubuntu 6.8.0-40.40-generic 6.8.12

If you're interested in updating your kernel to see if it resolves your issue, I found [this blog]("https://www.ramoonus.nl/2024/08/07/ubuntu-linux-kernel-6-10-3-installation-guide/") that outlines what one needs to do to update the kernel to 6.10.3-generic.

---

