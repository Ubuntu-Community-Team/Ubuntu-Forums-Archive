---
title: "Raid0 Post-Install"
date: 2007-03-02
forum: General Help
---

### Post by dillanlaughlin on 2007-03-02
Having a hard time finding an easy method for setting up RAID-0 after I have installed Ubuntu. I am not sharing it with any Windows OS

My machine has 3 hard drives:
hda - primary/boot partition (os, software, etc.)

Raid Stripe
[INDENT]sda 400gb[/INDENT]
[INDENT]sdb 400gb[/INDENT]

I will be storing files recorded from Myth on this raid stripe.

I have read the information on FakeRaidHowTo and FakeRaidEdgy but both of those seemed to apply primarily to installing Ubuntu directly on those drives.

My motherboard seems to support FakeRaid as when I am using the Raid BIOS utility it allows me to configure the stripe and reports the desired size correctly. Of course when I boot into Ubuntu they are 2 separate disks.

BTW: Both SATA drives are setup using xfs. Also when I attempt to run fdisk on the SATA drives, fdisk reports "Cannot open /dev/sda"

Please Help!

---

