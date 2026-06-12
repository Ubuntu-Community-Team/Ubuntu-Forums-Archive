---
title: "No login screen"
date: 2014-12-13
forum: General Help
---

### Post by punchdrunkgrunt2 on 2014-12-13
Gather round and hear my frustrating tale.
A couple of weeks ago, out of curiosity, I installed a copy of Bodhi linux on a spare partition alongside Kubuntu 12.04 (my main OS). Everything was fine until this morning when I was linuxing on Kubuntu when a bunch of updates popped up - kernel updates etc. I installed them => rebooted => GRUB menu => KDE splash screen => nothing. Blank. Uh oh. Bodhi linux still works and has become my lifeboat. Tried updating initramfs and GRUB - no joy. Blkid, fstab and mtab are all in agreement. X server problem?
I've been booting into recovery mode, root shell. Startx from root goes straight to the blank screen but if I login as me I get the dreaded "no directory, logging in with HOME=/" message. To be clear, my home directory is the same one I've had since installation two and a half years ago, I haven't moved it or added any other users. Bodhi linux is...nice, but I'd like my KDE back.
FYI
KDE 12.04 because it's a 5 year old laptop with an ATI card and I like my fglrx
Bodhi using open source drivers
/home (KDE) on its own partition
I can mount my KDE partitions in Bodhi (read only) - it's all still there

Any help would be much appreciated

---

