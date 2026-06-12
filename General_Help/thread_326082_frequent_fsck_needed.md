---
title: "frequent fsck needed"
date: 2006-12-27
forum: General Help
---

### Post by thomastaranowski on 2006-12-27
About every 2 hours during normal operation, my filesystem gets mounted read-only, and I end up having to reboot, run a manual fsck, then reboot again.  After this everything runs normally again, until the next round.   

The hard drive is a Western Digital, and I've run their diagnostic program on the hard drive, and it reports the hard drive is good.  I'm wondering at this point if it's other hardware(e.g. PCI controller) or some problem with my software configuration, or a buggy driver.  Any tips or suggestions on how to proceed with my debugging?  Can a kernel-mode linux driver corrupt the filesystem?  I want to say yes, but not sure.

The following excerpt taken from syslog looks pertinent:
Dec 26 21:00:46 heath kernel: [17179576.036000] Attempting manual resume
Dec 26 21:00:46 heath kernel: [17179576.064000] kjournald starting.  Commit interval 5 seconds
Dec 26 21:00:46 heath kernel: [17179576.064000] EXT3-fs warning (device hda1): ext3_clear_journal_err: Filesystem error
recorded from previous mount: IO failure
Dec 26 21:00:46 heath kernel: [17179576.064000] EXT3-fs warning (device hda1): ext3_clear_journal_err: Marking fs in nee
d of filesystem check.
Dec 26 21:00:46 heath kernel: [17179576.080000] EXT3-fs: mounted filesystem with ordered data mode.



I'm running Edgy, kernel 2.6.16-10-generic. 

Fdisk -l:
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7833    62918541   83  Linux
/dev/hda2            7834        9138    10482412+  83  Linux
/dev/hda3            9139        9729     4747207+  82  Linux swap / Solaris

---

### Post by pay on 2006-12-27
I used to have to run fsck regularly untill I decided to use reiserfs (reiser3.6 more sane than reiser4).

---

### Post by wgscott on 2006-12-27
I've been having a similar problem and it is specific to the kernels that came with Edgy.  If I go back to the earlier kernels, the problem goes away.  I have one master and two slave drives, and one or both would become read-only.  After wasting more time than I care to admit, I gave up.  I am using one of the drives for storage, mounting it read-only, and rearranged my file system.  The other alternative, booting in the older kernel, had its own set of problems.

I convinced myself that it is a kernel bug.  I had someone who knows how to do this sort of thing build the latest kernel in diagnostic mode.  The problem persists, but the diagnostics weren't informative.

](*,)

---

### Post by thomastaranowski on 2006-12-27
It 'seems' to have corresponded with when I clicked the handy 'update' icon in the top right corner (on Kubuntu), and did a mass number of upgrades.  There were also some major power outages at the same time, which makes me suspect the hardware got buggered.  So now I have no idea if it's hardware or software.  It would be nice to know what I should replace.  IF I had an extra hard drive laying around, I could install and run on that.  Then if I got the same problem, I could say it's motherboard related( up until recently, it had been running fine for a couple of months).

---

### Post by rykel on 2006-12-27
> **pay said:**
> I used to have to run fsck regularly untill I decided to use reiserfs (reiser3.6 more sane than reiser4).

That was what I was going to say... ext3 seems to crash some hard drives... I installed Edgy on ext3 because I wanted to see if it has improved, but alas, after only a few months of use (Edgy was released in October, right?) I am already getting instances whereby my whole laptop would hang, and only a HARD SWITCH TURN-OFF will reset the system.

From what I remember of my personal experience in the past with Fedora and ext3, 5-6 more of such incidents, and ext3 will ultimately destroy my hard disk, and there goes everything...

I hope NOT!

---

### Post by thomastaranowski on 2006-12-27
After some study, I suspect that the drive's write-caching scheme could be dinking up the file system.  Some notes I read indicated that some drives had non-standards compliant write-caching that can corrupt file systems.  I disable the write-cache via hdparm, so I'll see if that has any positive effect.

---

### Post by thomastaranowski on 2006-12-27
Why do I even bother.  The hdparm tweaks solved nothing.  Time to get out the gas and matches.

---

### Post by Phatfiddler on 2006-12-28
Rykel - 
That seems to be the exact problem that I have.  I haven't been able to explain it until now, but yes, that is what happenhs to me as well.  Thye thing is, I never had hangups in Dapper, only since i moved to Edgy.  Fsck reports only 1.5% non-contiguous space in my 60Gb, yet the drive just goes crazy once in a while.  When it does, CPU is arouind only 20%, system load is low, and hard drive read/write activity is low, yet it acts as if it's reading the entire drive, and everything locks up.  Hmmmm

---

### Post by thomastaranowski on 2006-12-29
I saw similar reports while investigating my problem.  One solution that was proposed is to use hdparm to change the time between ext3 journal commits from 5 minutes to 30 seconds.  Apparently, under some scenarios, the commit can cause some real thrashing.  I suppose doing it every 30 seconds spreads the thrash around.

---

