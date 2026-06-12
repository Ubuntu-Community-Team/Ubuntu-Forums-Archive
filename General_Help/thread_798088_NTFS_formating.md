---
title: "NTFS formating"
date: 2008-05-17
forum: General Help
---

### Post by stevekrules on 2008-05-17
Okay, so here's my problem.

I bought a new PC recently, unfortunately it came with vista, I tried to upgrade to ultimate, and I couldn't activate it with my key, so I tried using HP system recovery [a partition], which does not work after removing the original OS.

They sent me the discs, and they screw up my pc more then it helps. Nothing installs right, and it partitions my hard drive to 48GB and leaves the other ~270GB unpartitioned. [This is where my Ubuntu question comes in] I install Gparted, and I deleted the partitions, and now have all unpartitioned space [Windows & Ubuntu are on different hard drives, so no worry of ruining my Ubuntu partition], so my question is mainly this, is there any alternative to Gparted that supports NTFS formatting?

I _DO NOT_ need Ubuntu writing access to this drive, as I know Ubuntu cannot write to NTFS, all I need to do is format it.

I've tried installing Norton partition magic [on Vista], using Hirens Boot Disk, and nothing else has worked.

If I don't get it to NTFS, the recovery cd's have to format it since Vista does not use FAT32 [or 16] which Gparted only supports, and hence the problem stays

I would highly appreciate any help or recommendations, as I do not feel like bringing it back to circuit city and have their "technicians" work with my pc.

oh, p.s., as I posted this, I just realized even though my Ubuntu are Vista are on different disks, the MBR has been erased, so if I turn off Ubuntu I will not be able to boot back into Ubuntu.. lol, anyway to rewrite the MBR?

---

### Post by itix on 2008-05-17
Ubuntu can write to NTFS. NTFS3g works perfectly these days.

Well. enough about that. GParted on the ubuntu live CD has the ability to format disks to NTFS. I think there's supposed to be a library in the Synaptic Package manager for writing NTFS.

Apparantly, the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") is supposed to have NTFS support too.

---

