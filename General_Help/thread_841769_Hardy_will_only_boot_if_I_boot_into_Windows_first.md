---
title: "Hardy will only boot if I boot into Windows first???"
date: 2008-06-26
forum: General Help
---

### Post by gwilki5691 on 2008-06-26
Hi,
Has anyone experienced the following problem with Hardy?
I have a dual boot system with Windows XP. I did a freash install of Hardy and it worked fine. I then enabled the restricted nvidia drivers and the compiz effects. Now when I try and boot, the system hangs just before X should load up. You maybe thinking its just a driver or Xorg issue, but get this........
I accidentally discovered that if I boot into Windows first then reboot and select Ubuntu from the grub menu my system boots up perfectly. I get full nvidia support with spinning cubes and wobbly windows in their full glory. Once booted into Hardy I can reboot back into Hardy as many times as I like and it works perfectly. The only time the problem occurs is durung that 1st boot from cold.
As you can imagine relying on Bill to boot Hardy is a little humiliating.:-?
Any ideas?

---

### Post by gwilki5691 on 2008-06-26
To add to my post above;

1. I don't think it is a hardware problem as my PC works perfectly under Windows, and I have swapped graphics card, swapped RAM, changed to 500W Thermaltake PSU and removed any hardware I don't need to boot up.

2. I cannot see exatly where it fails as the screen goes black before it freezes even with 'nosplash' added to the grub line.

3. It does this in all versions of the kernel.

4. I can also get it to boot by booting into safe mode, disabling the compiz effects / nvidia driver and then enabling again once booted.

5. Once booted it has never failed, never locked up and never fails to boot upon reboot.

6. It always boots after Windows reboot.

Very very confusing!:confused:

---

