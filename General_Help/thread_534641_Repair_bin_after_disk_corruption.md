---
title: "Repair /bin/ after disk corruption"
date: 2007-08-25
forum: General Help
---

### Post by fa2k on 2007-08-25
I was trying to get a TV card working, and the computer froze a lot. It seems too have resulted in some disk corruption on my root partition.

I couldn't boot (got a permission error for /bin/sh), and tried an Ubuntu install CD. There, I ran fsck -f <drive>, and there were some 1000s of errors probably, so I just held down 'y' to accept the fixes. Almost all the errors were in files in the /bin/ directory.

The fsck program seems to have deleted /bin/sh, so, instead of a permission error, i got "file not found" (or similar) when booting. The error occurs when starting init, after the kernel is loaded. 

Even though this seems impossible to fix, I believe that most of the corrupted files were standard binaries, i.e., the ones that are included with Ubuntu.

The first thing that came to mind was to cp all of the files from the LiveCD /bin, to my drive. The liveCD has kernel version 2.6.20-15-generic, while the system with a problem is completely updated (sorry I can't be more specific, but I can't boot it and check). It may be worth a try if nothing better is proposed. This comes, of course, after a backup of all valuable data.

Is there a "repair" option in Ubuntu LiveCD  that reinstalls all the packages, or only the core system, on a separate Ubuntu install?

Thanks, 
Marius

---

