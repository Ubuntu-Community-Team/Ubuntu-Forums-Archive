---
title: "Recover disk space when NOTHING works"
date: 2019-11-03
forum: General Help
---

### Post by rick-cessco on 2019-11-03
Dealing with Ubuntu 16.04LTS.  Apologies for the long post but I have tried most every solution out there so far without success and only wish to avoid answers leading me down already ventured paths.  I mounted a 3TB failed NTFS drive that had become RAW on my machine to recover the files with Testdisk.  That worked but, I screwed up not realizing my system HDD didn't have enough room to accept all the recovered files copied from Testdisk post recovery.  My system HDD is 1.5TB but the external drive I was recovering from should have only had about 1TB on it.  Either way; my Ubuntu system disk filled beyond capacity.  I transferred the recovered files I wanted to an external drive and set about cleaning up my poor abused HDD deleting vast amounts of data that I didn't need to retain post recovery.

My system will still boot up just fine but is horribly sluggish, unable to update and won't play nice with internet connections (ssslllllloooooooowwwwwwwwwwwww).

What I'm left with is a disc that should have tons of space but shows full.  /var/cache/apt/archives is all but empty yet this errors when I try any form of update or upgrade.  Ergo installing any package or 3rd party utility to help clean is currently impossible.  All variation of sudo apt-get clean, apt-get clean, sudo apt-get --purge, autoremove etc... don't help as the /var/cache/apt/archives is all but empty.  I have gone through folders manually verifying volumes and even used root permissions to delete to the bone.  Nothing.  The disk analyzer utility and any terminal data all show a 1.5TB disc that is 100% used and 0 bytes remaining.

I have no restore utility installed so that option is out.  A fresh install would not be the end of the world, just inconvenient so: any ideas out there?

---

### Post by webaake on 2019-11-04
Did you try a forced disk check at boot? There's obviuosly something wrong with the filestructure.

The command is: touch /forcefsck

"This empty file will temporarily override any other settings and force fsck to check the filesystem on the next system reboot. Once the filesystem is checked the forcefsck file will be removed thus next time you reboot your filesystem will NOT be checked again."

From here: [https://linuxconfig.org/how-to-force-fsck-to-check-filesystem-after-system-reboot-on-linux](https://linuxconfig.org/how-to-force-fsck-to-check-filesystem-after-system-reboot-on-linux)

---

### Post by HermanAB on 2019-11-04
How did you delete the files?  If with a GUI, empty the trash.  Maybe delete the .trash (or whatever) directories manually from the command line. A fsck is probably required at this point.

---

### Post by TheFu on 2019-11-04
You can always boot from a Desktop Install USB flash drive, mount the storage and remove things.  Inside that "Try Ubuntu" environment, you can install whatever tools you need and look for files.

Testdisk kinda sucks, right?  It "finds" whatever was there, even if is was the 8th version of some file from 3 yrs ago. Backups are 1000x easier. You get the version of the files you need, no need to hope.

---

