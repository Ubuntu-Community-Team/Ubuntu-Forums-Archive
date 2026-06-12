---
title: "Cannot Access Recovery Partition"
date: 2013-03-09
forum: General Help
---

### Post by Petro Dawg on 2013-03-09
Some time ago, I replaced my Windows XP OS on my HP pavilion a1330n, with Ubuntu.  I deleted all partitions except the recovery partition and installed Ubuntu 12.04.  Now, due to needing Excel VBA to work on some school assignments, I would like to create a dual boot situation, but it seems I can no longer access the recovery partition during start up (normally by pressing F10 on Boot Up) to reinstall the Windows OS.  I checked with GParted, and the fat32 "HP_Recovery" parition is still on the hard drive.  (I attached a Gparted screen shot in case it might be helpful.)


[ATTACH=CONFIG]239970[/ATTACH]


Do I need a special repair disk, or boot disk to access the  partition now?  If so, any suggestions on where to find such a thing?   Or have I lost access forever?

Thanks

---

### Post by Mark Phelps on 2013-03-09
Sorry, but when you deleted all the other partitions except the recovery partition, it looks like you deleted the code that is used to launch recovery when you press a Function key.

If you contact HP and tell them that your Windows install got infected, so you erased it, and NOW, you can't restore it -- they might be willing to SELL you a set of recovery disks.

---

### Post by Petro Dawg on 2013-03-09
> **Mark Phelps said:**
> Sorry, but when you deleted all the other partitions except the recovery partition, it looks like you deleted the code that is used to launch recovery when you press a Function key.

If you contact HP and tell them that your Windows install got infected, so you erased it, and NOW, you can't restore it -- they might be willing to SELL you a set of recovery disks.

I figured that might be the case. I decided intalling Office2010 using Wine (PlayOnLinux) and did so successfully except for 1 critical thing, I can't seem to use the activeX controls which run my VBA code in Excel.  So now I would gladly take advice on either:

1. getting my recovery partition working (which seems like it might not be possible) or
2. getting activeX controls to work in Ubuntu (which may also be impossible)

I should add, I already selected "Enable all controls without restrictions..." in the trust center activeX settings within Excel.

Thanks for any advice.

---

### Post by Petro Dawg on 2013-03-09
Well I have a relatively decent "work around" at the moment by using "Form Control Buttons" instead of "ActiveX Controls" since either can run VBA subs.  Still interested in any ideas for solutions to the problems I mentioned earlier, but I think I can manage with what I have for now.

Thanks.

---

### Post by Mr. Shannon on 2013-03-09
You might be able to boot the recovery partition from the GRUB boot menu.  However, if the HP recovery tools are anything like Lenovo's then using the recovery tool will completely erase your drive.  So you will lose your linux installation and everything on it.

---

### Post by Petro Dawg on 2013-03-09
> **Mr. Shannon said:**
> You might be able to boot the recovery partition from the GRUB boot menu.  However, if the HP recovery tools are anything like Lenovo's then using the recovery tool will completely erase your drive.  So you will lose your linux installation and everything on it.

You are truly awesome.  Yup, booted to GRUB and I was able to get the Recovery Program to run.  I'm going to hold off restoring and setting up the dual boot just yet to see if Excel runs well enough through Wine, as I am happy with how everything else is working in Ubuntu and I'd prefer not to have to set everything up again for the multiple users on this machine.  However, I'm happy to know I have the option to restore now if needed.

Thanks.

---

