---
title: "Hard drive issues"
date: 2006-12-27
forum: General Help
---

### Post by 2eeks on 2006-12-27
I'm trying to reinstall windows on my hardrive because ubuntu got pretty messed up... but when I start the installation CD it says that I dont have a hard drive...?

Anyone ever encounter this issue?

---

### Post by meng on 2006-12-27
Have you got any unallocated space on that drive? What is the partition setup? The Windows installation disk software is pretty lousy at recognizing other partitions, and I think won't even allow Windows to be installed on an extended/logical partition.

---

### Post by 2eeks on 2006-12-27
No unallocated space on the drive from what I can tell... When I installed linux the first time I used the entire drive. How do I go about scaling down the linux partition so Windows has a place to start?

---

### Post by meng on 2006-12-27
This is probably the explanation. Therefore I would suggest you download the latest version of GParted LiveCD, resize your Linux partition, leave at least 5GB unallocated for Windows (but your discretion). Hopefully the Windows installer will recognize the unallocated space and offer to format it for you.

Beware that GParted has worked very well for me, but one should seriously consider backing up all vital data before undertaking something serious like a resize.

---

### Post by dcstar on 2006-12-27
And be aware that installing Windows will (probably) wipe out Grub.

Do a search for the procedure for re-installing Grub after a Windows install so you have the info at hand when you need it.

---

### Post by meng on 2006-12-27
> **dcstar said:**
> And be aware that installing Windows will (probably) wipe out Grub.
Will definitely wipe out grub. There's an article in the wiki entitled RecoveringUbuntuAfterWindows or some such.

---

### Post by enopepsoo on 2006-12-27
I've had a partition resize in gparted crap out.  It was an older system (that is what I get for wanting to install winblows).

I second the recommendation to backup first, preferably to a different drive/cd.

---

### Post by 2eeks on 2006-12-28
I repartioned the harddrive using the ubuntu installation disk, cause I already had it burned. I attempted the windows installer again, and despite my reallocation of free space it still did not recognize the harddrive.

Im going to check to make sure the hard drive is connected to the appropriate spot on the mobo...

---

### Post by ~LoKe on 2006-12-28
I bet it's a SATA, right?  I've heard of some problems with SATA drives.  Not sure how to fix it though, sorry.

Have you tried flashing your BIOS to the latest revision?

---

