---
title: "Seemingly random, Ubuntu will attempt to suspend"
date: 2014-05-11
forum: General Help
---

### Post by Steven_Justin on 2014-05-11
New to Ubuntu, having an issue that I can't seem to find a solution to.

Seemingly random, Ubuntu will attempt to suspend. I've currently turned off suspend for all occasions in System Settings > Power. I did this because of the [Apple Inc. MacBookPro10,2] suspend/resume failure [non-free: wl nvidia] issue. I'm okay with that. BUT every random suspend will require a hard shutdown. That's the annoying part.

Even though it's off for all normal occasions it still randomly suspends. Sometimes after a couple minutes or sometimes not until after an hour or two. This happens both plugged in and on battery. For a minute I thought it was the after market battery I got from iFixIt but the problem persists using the original Apple battery as well.

I'd like to figure out why my computer is suspending for no reason. Has anyone had this issue before? Are there any logs I can check to determine where the suspend order is coming from? New to debugging Linux so any guidance would be great. Below are my specs.


Running Ubuntu 14.04 on a MacBook Pro 6,2:
Core i5 M540
GeForce GT 330M running proprietary NVIDIA driver version 331.38
4GB 1006MHz DDR3
60GB OCZ Solid 3 SSD supports TRIM, running TRIM every hour and on shutdown/reboot


Thanks!

---

### Post by Steven_Justin on 2014-05-12
Attempted a fresh install of 14.04 and the problem persisted, ruling out a configuration error on my part. Saw the computer lose power a couple of times during the Mac POST/Splash Screen. It's tough to say though because Mac's don't provide you with a verbose POST screen, it could just of likely been while loading GRUB.
 
I'm now treating this for hardware issues, where the computer loses power for a MOMENT and Ubuntu attempts to suspend during power loss. Attempting to routine maintenance, updating Mac EFI, SMC, etc. Will keep everyone posted.

---

### Post by pqwoerituytrueiwoq on 2014-05-12
check the power manager options, action on low/critical battery
does it happen with the battery disconnected?

---

### Post by Steven_Justin on 2014-05-12
In Settings > Power I had it set to shut down on critical battery. I have not attempted to run it without the battery, but I did use a second different battery and the problem persisted. I'll give running it without a battery a try if the problem continues.

---

### Post by Steven_Justin on 2014-05-12
EFI/SMC we're up to date. And the computer ran fine for a long time in OSX 10.9, no problems. Moving to a 250GB HDD and going to dual boot OSX/Ubuntu using the steps outlined here: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Even if it doesn't solve the problem, having a small partition with OSX on it will allow me to more control and insight over the hardware since it doesn't directly let me play with EFI/SMC/BIOS on my own.

---

### Post by BetterAndBetter on 2014-05-12
I have a similar problem.  If I leave my computer for a bit when I come
back I have to enter my password again.  I don't use suspend but if I
did I expect it would act like this.  I have turned everything in the
Settings Manager -> Power Manager to "never" and it still keeps
happening.  However, it doesn't happen randomly in my case.

I am running Xubuntu 14.04 amd64 on a Lenovo x200 laptop computer.

---

### Post by Steven_Justin on 2014-05-12
> **BetterAndBetter said:**
> If I leave my computer for a bit when I come
back I have to enter my password again.  I don't use suspend but if I
did I expect it would act like this. 

I've seen this behavior as well. This was due to the monitor shutting off and require password when it turned back on. Thankfully, this didn't attempt to suspend, this worked just fine since it was just the monitor turning off.

---

### Post by Steven_Justin on 2014-05-13
Ran all last night with no problems. Installed a lot of my usual software and did my new OS maintenance. Will continue running it for the rest of the week and see if the problem arises again. I'm keeping tabs on any change no matter how small. I'll report back either good or bad. Here is the currently list of differences I made or was forced to make:


1) **Moved from a 60GB OCZ Solid 3 SSD to a 250GB Hitachi HDD.** Possible solutions: Bad SSD caused abnormal behavior? Poor hardware or software SSD support? Did not format the SSD properly? (Found out the Mac recovery partition was still on the SSD. Uh oh.)

2) **Dual-booting OSX 10.9 and Ubuntu 14.04 using rEFIt**. Possible solution: Re-installing OSX 10.9 updated the EFI and SMC, resolving hardware issues? rEFIt is magic?

3) **Have not installed any of the 14.04 auto updates.** Possible solution: A update I continuously installed immediately causes the error but I don't give myself enough time to notice the distinction?

4) **The bottom plate is being held on loosely by two screws.** Possible solution: Not ruling this out, ran it all evening with two screws barely holding the bottom plate to the computer. Maybe something is getting smashed in there causing the strange behavior? Working 5 years in computer repair, I've seen weirder things happen.


Thanks!

---

### Post by Steven_Justin on 2014-05-14
Problem persists as of this evening. It happened 3 times. Only difference for all day yesterday and this evening was that it was plugged in while I was using it this evening, while I let it run off battery yesterday evening.

While, if the suspend lock-up issue didn't exist this wouldn't be AS frustrating, I'm going to close the random attempts to suspend as a hardware issue.

---

