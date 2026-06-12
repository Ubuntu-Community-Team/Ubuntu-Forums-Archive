---
title: "Feisty shutting down during boot process"
date: 2007-07-24
forum: General Help
---

### Post by TheBlackCat13 on 2007-07-24
I have had kubuntu feisty for a couple of months now.  It has been working fine during that time.  I also have a dual-boot of windows XP.  But starting yesterday, whenever I try to boot into Linux the boot process proceeds for a couple of seconds and then the computer just shuts down completely and instantly.  This happens in both the regular boot and recovery mode.  

During the normal boot the progress bar gets maybe a couple of percent across, while in recovery mode it is loading things but going far too fast for me to tell what it is crashing on.  It seems to be at a fairly consistent point, but I don't know if that is due to time or to a specific module being loaded.  

Windows XP boots just fine, and I can access the linux partitions with ext2fsd for windows and fstab looks alright.  I still have plenty of space on the linux partition, about 10 gb.  I had not used windows in a couple of weeks before it happened so ext2fsd couldn't have done it.  

There was nothing out of the ordinary when I shut down.  I did install a package before it happened, a package for shadow password support and heimdal kerberos support, but I don't see how that could be the problem.  If it is I can't even get into recovery mode to uninstall them, although I could manually delete or at the very least break them from XP if someone could tell me what the files are.

---

