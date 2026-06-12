---
title: "Difficulties Removing Grub"
date: 2006-11-20
forum: General Help
---

### Post by braub1018 on 2006-11-20
So I installed Ubuntu 6.06 and thoroughly enjoyed but now it is time to move on and just keep Win XP on my system. (currently a dual-boot)  I have read that I should use a Win XP boot disc to enter the recovery console and create a new MBR and fully understand how to do that. However, when I attempt to enter the recovery console, there is no hard drive detected.  I am completely stumped now and have pretty much exhausted my resources.  Does anyone have any ideas that might solve my problem?  Any advice would be great.  Thanks.

- braub

---

### Post by dcstar on 2006-11-20
> **braub1018 said:**
> So I installed Ubuntu 6.06 and thoroughly enjoyed but now it is time to move on and just keep Win XP on my system. (currently a dual-boot)  I have read that I should use a Win XP boot disc to enter the recovery console and create a new MBR and fully understand how to do that. However, when I attempt to enter the recovery console, there is no hard drive detected.  I am completely stumped now and have pretty much exhausted my resources.  Does anyone have any ideas that might solve my problem?  Any advice would be great.  Thanks.

- braub

If you can boot to a Dos command prompt then "fixmbr" or "fdisk /mbr" should work.

---

### Post by braub1018 on 2006-11-21
That did the trick. Thanks alot.

---

