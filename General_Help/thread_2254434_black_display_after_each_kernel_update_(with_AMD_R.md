---
title: "black display after each kernel update (with AMD Radeon HD 6/7000 serie)"
date: 2014-11-27
forum: General Help
---

### Post by rvboutin on 2014-11-27
Hi,
I have got 2 PC, each running Ubuntu 12.04.5 LTS with EnablementStack, current kernel: 3.13.0-40. My current AMD drivers on both machine are: 14.10.1006.1001-140505a-171583E. Even before installing the enablement stack in July and with the last 2 versions of AMD drivers I was getting this  problem of ending up with no display (black screen with a single  cursor). When this happens, I have to reboot in recovery mode, trying failsafe graphic mode does not work and I end up with a black screen again, I have to use root console mode and remount all partition to get read/write access. Sometimes, running the am-uninstall.sh restore the default graphic mode and I am out of trouble, however sometimes that does not work (message saying that the drivers have been modified and uninstall cannot proceed).
I have reached a point where to avoid the problem altogether, when I see a kernel update listed, I uninstall the AMD drivers, reboot, run the update, reboot, reinstall the driver and reboot :shock:, not very straight forward update procedure, isn't it?
I hoped that with time (and because other people have been reporting similar issue) that this will be fixed... but no ](*,)so I have decided to report this now because last time after trying pretty much everything I could find on this forum and others, I had to restore one of my system to the last back-up image I had (from July)!!  To me this recurrent problem is just not acceptable!
I'll try to report this in Launchpad, but this should be fixed at kernel or update procedure level (i.e. resetting the display by default or something).
If other have the same experience, I'd be glad to know how they solved this.
Cheers,
Rv

---

