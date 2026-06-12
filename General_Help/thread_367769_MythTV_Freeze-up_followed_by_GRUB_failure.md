---
title: "MythTV Freeze-up followed by GRUB failure"
date: 2007-02-22
forum: General Help
---

### Post by Yoooder on 2007-02-22
I had an interesting crash last night, while watching a recorded show in MythTV on Edgy, MythTV froze (leaving it's final frame on my TV).  I was able to kill just MythTV and keep running Ubuntu, but couldn't get MythTV to regain control of my TV set.

I tried unloading the ivtv_fb module that's needed to output video to my TV through my PVR-350 tuner card, but received errors even when trying to force the module to unload.

I finally rebooted, and my machine hung at GRUB.  It says something to the effect of "loading stage 1.5", shows one more message--something about it loading (no errors)--and then hangs.

So I booted to the 6.10 LiveCD and ran ext3 checks on my boot partition (seemed ok), as well as xfs checks on the rest of my main partitions, without seeing any errors.  I then re-ran the GRUB installer without receiving any errors.

I've done all my repairs remotely from work, so haven't been able to test if I'm back up and running--but my main question is, **does anybody know what may have gone wrong?**  I was fearful it was a drive failure however everything seems in tact.  It seems bizarre that an application crash and a stuck module would affect my bootloader.

:confused:

---

### Post by majoridiot on 2007-02-22
did you *reboot* or power-cycle?

if you just did a simple reboot, it is possible that the machine was left in a very unstable state when
mythtv hung and you manually killed it- which somehow in the reboot/restart process *could* have
corrupted your GRUB somehow.  i have had unstable states survive a reboot, only to hang the machine
somewhere in the reboot process- never had corrupted files, tho.

i would be very surprised if mythtv had anything to do with it, as it wouldn't have permissions to
write to grub.

i'd start with a thorough review of all your logs in /var/log to see what went awry.

---

### Post by Yoooder on 2007-02-22
**FIGURED IT OUT**

Just in case anyone else sees anything like this...  the source of my boot failure was a flashdrive that I had left plugged in.  Once I removed it everything booted fine :)

---

