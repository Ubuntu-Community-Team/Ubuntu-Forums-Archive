---
title: "Move /home to new partition"
date: 2008-07-04
forum: General Help
---

### Post by dmitrijledkov on 2008-07-04
I have made a new partition. And I want to move my /home there.

How should I copy current /home to the the location?

How to reference new /home in /etc/fstab?

How do I know I'm running on new home?

How will I delete "old" home? Cause /home will already be new one =D

---

### Post by Philonimbus on 2008-07-04
I would advise you to burn a bootable GParted LiveCD.

This way you will have full access to your system partitions.

Download and burn this cd image : 

[GParted Stable Live CD]("http://downloads.sourceforge.net/gparted/gparted-live-0.3.7-7.iso?modtime=1215010676&big_mirror=0")

Then you boot the CD and do whatever you want with your partitions.

For extensive documentation on GParted go here :

[GParted documentation]("http://gparted.sourceforge.net/documentation.php")

To create a new /home, just delete the /home folder (backup anything important beforehand) and when you're working on your partitions with GParted, select the partition, right-click on it, and mount it in "/home".

And no need to bother with fstab, GParted does it all.

---

### Post by louieb on 2008-07-04
The classic how to: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

