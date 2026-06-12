---
title: "Ubuntu Verbatum Drive Read-Only GPT --HowTo Wipe/Nuke?"
date: 2014-04-25
forum: General Help
---

### Post by slacker1965 on 2014-04-25
I'm not a master of Linux, but I've been using it for years, so I'm not exactly a noob either.

I have a Verbatum Tuf-N-Tiny 16 GB USB Flash Drive.  I set it up with Tails and a 14GB encrypted partition.  I cannot remember the password I used, but there is nothing I need form the encrypted partition, so I just want to get rid of it.  I have spent hours searching and learning, but still no working answer.  I cannot do anything with it because it claims to have a protected MBR with GPT (GUID disk), thus it will only mount read-only.  I cannot seem to force it to read-write. Where is an appropriate place to seek more help on this?  

Thank you for reading this!

---

### Post by jamesisin on 2014-04-25
Install gparted (*sudo apt-get install gparted*) and use gparted to reformat the unmounted drive.

---

### Post by slacker1965 on 2014-04-25
jamesisin, thank you for the fast response.  I've already tried that and learned that gparted does not work, reporting: "Linux Unified Key Setup encryption is not yet supported.  Unable to open /dev/sdc read-write (Read-only file system).  /dev/sdc has been opened read-only."

Also, the USB drive reports having a Protected MBR, whatever that means.  It was created by a Tails installation, then the encrypted partition was added by Truecrypt.  I haven't thought to search for a solution from Tails until now, so that's a new idea...

Somewhere I read that gparted cannot handle GPT, but to use gdisk instead.  I've tried fdisk and cfdisk, but they are unable to work with GPT.  I installed gdisk, but it would do nothing but mount things Read-Only.  I also tried various schemes with the "dd" command, attempting to nuke the MBR, partition table etc, all to no effect.

Oh yeah, it may be important that the first partition was created by TAILS and the other was created with Truecrypt, but Truecrypt doesn't give any options to do away with the partition...

---

