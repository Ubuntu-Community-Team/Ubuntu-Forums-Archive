---
title: "Latest kernel update 5.3.0-26, 19.10"
date: 2020-01-06
forum: General Help
---

### Post by jerry47 on 2020-01-06
Three machines running Ubuntu 19.10 had kernel updates from 5.3.0-24 to 5.3.0-26. Works fine but noticed something unusual. Two of the machines are Intel Nucs. During the boot process the Intel Splash screen comes up normally. Then the Ubuntu Grub Menu. Next the Intel Splash screen again but without the setup selection menu bottom right. Then normal after. These two machines boot UEFI. The third boots legacy. It does not exhibit this behavior. 

Please write back if you have seen this behavior with the newer kernel. I booted with the previous kernel and this does not happen. I would think this could not even happen. I have had Linux get stuck in a boot loop before and at first that's what I thought was happening. But its not. The two Intel splash screens are not the same. The second is missing the F key selections for setup and bios update etc. Guess I want to know if this was done on purpose or its some sort of bug. 

Thanks,
Gerald

---

### Post by CatKiller on 2020-01-06
19.10's too new for me, but Intel have been working on "flicker-free boot" where the screen mode doesn't change at all until the login screen, and the boot splash is overlaid on the bios splash. It could be because of that.

---

### Post by jerry47 on 2020-01-06
I&#8217;ve never had any issues with flicker during startup and boot. It&#8217;s actually slowed down the boot. Usually about 7 seconds to desktop without logon. Now, it&#8217;s like 10. It&#8217;s an extra screen. There&#8217;s only one intel splash screen and somehow now there&#8217;s two different ones. Not sure that&#8217;s done with the kernel update. I&#8217;m extremely curious.

---

### Post by jerry47 on 2020-01-07
I decided to roll back the latest Ubuntu kernel update to 5.3.0-24 from 5.3.0-26. Upon researching various ways to accomplish this, altering grub seemed like the best solution. I think displaying the Intel splash screen twice is an unintended consequence of changes made to the update. I'm still interested in comments related to this problem. I altered grub with the following lines:

#GRUB_DEFAULT=0
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true

Then selected the previous kernel via the grub boot screen. This resolves the issue of displaying Intel splash screen twice and increasing boot time. This way when there are other kernel updates I'm set up to test them before restoring grub to its original settings. 

Regards to CatKiller for his comments. 

Gerald

---

