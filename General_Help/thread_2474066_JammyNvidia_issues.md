---
title: "Jammy/Nvidia issues?"
date: 2022-04-21
forum: General Help
---

### Post by csete on 2022-04-21
I tried updating to Jammy a couple of days ago and ran into issues with suspending my laptop and logging in after I opened it again.  I ended up reverting back to 21.10.  This morning I found this issue:  [https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1968929](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1968929) .  My question is whether there is a "safe" configuration of Jammy that works with Wayland right now?  I usually am configured in hybrid mode with the Intel drivers as primary.  I can wait to upgrade if there is no safe way to do this, but thought I'd ask here to see what my options might be.

Thanks!
Craig

---

### Post by grahammechanical on 2022-04-21
This matter was discussed in the development section of the forum.

[https://ubuntuforums.org/showthread.php?t=2473861](https://ubuntuforums.org/showthread.php?t=2473861)

I have been running 22.04 (development version) for some weeks and Wayland was the default. Then after an update/update X.Org became the fault with no option to load using Wayland. Personally, I do not think that users should be forced to use a work around. Not on a LTS release.

Regards

Edit: I have just logged into the 22.04 install and the Wayland option is back and is now the default once again. I only have Intel graphics.

---

### Post by csete on 2022-04-21
If I force Intel graphics, I should be OK with Jammy and Wayland then?  I honestly, don't do enough that it is likely the Nvidia card actually kicks in.

---

### Post by este.el.paz on 2022-04-24
> **csete said:**
> If I force Intel graphics, I should be OK with Jammy and Wayland then?  I honestly, don't do enough that it is likely the Nvidia card actually kicks in.

@csete:

I'm running a '12 cMacPro that has an Nvidia card with multi-boot set up, in which I have a Lubuntu Jammy installed . . . .  I just checked "lsmod" and I see "nouveau" showing in the "video" category.  Over the years of running linux I have found issues with using "proprietary" nvidia drivers, and during install I either select "default" or "nouveau" to run the graphics . . . and doing that I don't or haven't had issues with "suspend" or reviving from suspend on that machine.

I also have a System76 laptop running Pop!_OS and they use the nvidia proprietary software . . . based on Impish right now.  Recently I had an issue where the machine wouldn't suspend, it would flash black and then back into the log in screen . . . then it wouldn't revive from suspend . . . .  I was running "integrated" graphics at the time, I changed that around, no dice.

The techs there suggested "purging" the nvidia driver and then re-installing it . . . and that fixed the problem.  Likely to return again at some point in the future??  Nvidia doesn't seem to keep pace with linux upgrades . . . in their proprietary software.  I don't know what Wayland is, but in my Jammy edition it looks like "nouveau" keeps things current, etc.

---

### Post by SeijiSensei on 2022-04-24
My understanding is that the nouveau driver doesn't support hardware acceleration on the graphics card or audio via HDMI. That was true some years ago, but I don't know if it's still true. Most processors these days are fast enough so that hardware acceleration isn't all that important, but audio over HDMI is a requirement for me on at least one computer that is connected to my TV. (All my computers have NVIDIA hardware.)

---

### Post by este.el.paz on 2022-04-24
> **SeijiSensei said:**
> My understanding is that the nouveau driver doesn't support hardware acceleration on the graphics card or audio via HDMI. That was true some years ago, but I don't know if it's still true. Most processors these days are fast enough so that hardware acceleration isn't all that important, but audio over HDMI is a requirement for me on at least one computer that is connected to my TV. (All my computers have NVIDIA hardware.)

@SeijiSensei:

I have seen comments on the SUSE forums that suggested, "nouveau is old" . . . my requirements are pretty simple.  I come from the PPC linux days and back then the only driver we had was "nv" and we had to do a lot of messing to get that installed to the Xorg.conf file, at that time "nouveau" was the "unobtanium" driver that we wished we could get, etc.

This install that is now Jammy goes back a few years and I also have Nvidia hardware in all three machines that I use regularly . . . at that time I was still finding "nouveau" was better than "proprietary" in linux.  A couple of years later the SUSE forum told me about "default" . . . which I mostly use now.  My '12 cMP I think is using "vga" rather than HDMI??

The System76 laptop has HDMI port, . . . I have a Gecko and a Debian Bookworm along with the ubuntu-based Pop! that has options for different graphics . . . .  It would be tomorrow before I'm back to that machine to see what drivers are in use.

I don't really know if "nouveau has come a long way" . . . or, "it's been passed over and left behind."  Generally I find the proprietary options to be problematic, across a wide range of systems that I have installed and used over the years.  I like the hardware, but the software side seems to lagged behind the linux upgrade cycle.

---

### Post by csete on 2022-04-25
Thanks for all of the input.  I've put a pause on the update for a while to see if some of this settles down a bit.  Right now I need a semi-stable machine and can't afford to be down for a long time to get all of this straightened out.

---

### Post by este.el.paz on 2022-04-25
> **csete said:**
> Thanks for all of the input.  I've put a pause on the update for a while to see if some of this settles down a bit.  Right now I need a semi-stable machine and can't afford to be down for a long time to get all of this straightened out.

@csete:

Thanks for posting back on it, best wishes on it.  It's hard to know if rolling back to Impish will provide better nvidia drivers than what you could have in Jammy . . . ??  Jammy is "LTS" and is now officially "released" . . . ready for prime time, etc.

---

### Post by csete on 2022-04-25
> **este.el.paz said:**
> @csete:

Thanks for posting back on it, best wishes on it.  It's hard to know if rolling back to Impish will provide better nvidia drivers than what you could have in Jammy . . . ??  Jammy is "LTS" and is now officially "released" . . . ready for prime time, etc.

Thanks.  In my case, I had cloned my Ubuntu partition before the upgrade, so I was able to revert pretty easily.  I'm currently running on Impish with the 470 version of the Nvidia drivers and things are working OK for the moment.  While I tend to like being on the bleeding edge, I will give Jammy a couple more weeks to settle down.

Thanks again,
Craig

---

