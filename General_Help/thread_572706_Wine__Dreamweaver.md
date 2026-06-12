---
title: "Wine | Dreamweaver"
date: 2007-10-10
forum: General Help
---

### Post by BroshizzleDizzle on 2007-10-10
My brother was working on my computer and his flash drive wouldn't show up, so he managed the filesystems and accidently destroyed my boot table.  I've been dual-booting Ubuntu and Windows XP for some time now, but I'm going to hopefully get rid of Windows.
All my files on the hard-drive are fine.  I've successfully mounted the drive with ntfs-config.
I've installed wine successfully.

When I attempt to run Dreamweaver 8, it begins loading but it closes saying that I need to reinstall.  This is because it cannot find the registry settings.  I cannot boot Windows to export the registry settings, and my XP install disks are at home, not with me here at college.  I cannot get them for at least two weeks.

What should I do?  Can someone export their registry for me?  I can edit registry files to change paths and such if needed.  I am a web development major, and my school requires Dreamweaver to be used.  I need this to work as soon as possible.

---

### Post by DJ_Peng on 2007-10-12
I recently had to reinstall my comp and before I re-installed Dreamweaver 8 I took the upgrade to Gutsy (then beta). The new integration of Wine into Gutsy made installing DW easier than ever. There's even a menu of programs installed with Wine so you don't have to remember the proper command line info to use to launch it.

Since Gutsy is now a Release Candidate and "suitable for testing by any user" you may want to [grab the upgrade]("https://help.ubuntu.com/community/GutsyUpgrades") and try installing DW with that.

---

### Post by tech9 on 2007-10-12
> **DJ_Peng said:**
> I recently had to reinstall my comp and before I re-installed Dreamweaver 8 I took the upgrade to Gutsy (then beta). The new integration of Wine into Gutsy made installing DW easier than ever. There's even a menu of programs installed with Wine so you don't have to remember the proper command line info to use to launch it.

Since Gutsy is now a Release Candidate and "suitable for testing by any user" you may want to [grab the upgrade]("https://help.ubuntu.com/community/GutsyUpgrades") and try installing DW with that.

I agree... choose the default settings when creating the partition. It will resize and create a new one... thus leaving your data in tact and accessible.

---

### Post by DJ_Peng on 2007-10-12
> **tech9 said:**
> I agree... choose the default settings when creating the partition. It will resize and create a new one... thus leaving your data in tact and accessible.
I think you're confusing Wine with VMware. Wine doesn't ask, or care, about partitions.

---

### Post by BroshizzleDizzle on 2007-10-16
Hmmm... I'm not sure what I did, but it now finds it...
And I got the entire Macromedia suite to work, not just flash and dreamweaver.

---

### Post by tech9 on 2007-10-18
> **DJ_Peng said:**
> I think you're confusing Wine with VMware. Wine doesn't ask, or care, about partitions.

no confusion here... it was a general statement about resizing partitions.

---

