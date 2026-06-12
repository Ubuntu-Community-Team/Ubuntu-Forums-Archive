---
title: "Vista won't boot!"
date: 2007-12-02
forum: General Help
---

### Post by Patman27 on 2007-12-02
Hi, i am running a dual-booted computer (Vista home premium + ubuntu 7.10) and i just got a problem with Vista.

Last night, I logged out of windows and logged into ubuntu to work on Wine running world of warcraft. I didn't make any crucial system changes. The only thing was that i ran "regedit" from terminal and added the "almost mandatory performance tweak" as listed by so many linux forums. during that time i had access to my vista partition and so nothing seemed out of the ordinary. However, today when i tried to boot into vista from GRUB, it showed the boot screen as it normally would, but when the screen went blank (which normally happens before the login screen).......the screen stayed blank. 
After a few seconds the HDD activity light started shining as it normally would during usual windows operartion, but still no login! it just stays like that until i do a manual shutdown.

Safe mode didn't work either. After it loads most system drivers, it gets stuck on csdisk.sys (or something like that) and just freezes. Again, the HDD light shows same behavior.

I also tried "Run last good known configuration" but again, i got the same results as from the first instance.

I'm running off my ubuntu partition for the moment, but for some reason i don't have access to my vista partition. I can see the one labeled "RECOVERY" from windows, but i can't go to the vista partition.
For the greater part, all of my data is fully backed up. the only missing things are a few things that might have changed over the past few days (light schoolwork, etc.) Please help me fix this, I'd rather not re-install vista YET. 

thanks!!!


(p.s. If i re-install vista on the broken vista partition, will it mess up the MBR and/or grub? will i be able to boot into the new vista install and/or linux?)

---

### Post by lenux2005 on 2007-12-02
Try booting to a bootable cd (bart pe) and run check disk. If that does not work you may have to reload windows. If so the following link will help you recover your Ubuntu:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I think the check disk will solve your problem.

---

### Post by froy02 on 2007-12-02
When you access your vista partition from ubuntu it showed a change in the file system index. If the hard drive light was going it go on for a long time because vista is checking every file in your vista installation. It would take a very long time so let it do its thing and try to watch a football game in the meantime.

---

