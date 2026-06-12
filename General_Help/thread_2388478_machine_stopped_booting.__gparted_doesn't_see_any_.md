---
title: "machine stopped booting.  gparted doesn't see any drives (have 2)"
date: 2018-04-03
forum: General Help
---

### Post by JimLS on 2018-04-03
Have Ubuntu, Win 7 and Win 10 partitions.  It stopped booting so I pulled out a CD with gparted but it doesn't see either drive.  Interfaces are different and the second drive is strictly a data drive.  I used a windows program to fix booting when installing Win 10 which may be an issue with dealing with the format but I expected to at least detect the drives.  I tried 'df -h' at a command prompt and don't see either drive.

---

### Post by oldfred on 2018-04-03
UEFI or BIOS?
Does UEFI/BIOS see drives? If not seen, no operating system will see them.

df -h only shows mounted partitions.

Does this show anything?
sudo parted -l

---

### Post by JimLS on 2018-04-03
UEFI
When I turn on the PC I can hear what I think is the hard drive seeking about 6  times 
parted -l gives:
Error: /dev/sr0: unrecognized disk label
Actually only have 1 SATA drive.  It's been a long time since I set this up and I set up an additional partition as another drive so mistakenly was thinking I had two drives.  I opened it up to be sure...
UEFI shows SATA3_0 port as blank - no text.  DVD shows model of drive on another port.  The others show "Not Detected" so it seems to be seeing something but doesn't identify it.

---

### Post by JimLS on 2018-04-03
I am thinking the platters may not be spinning but not sure how to check that.  I have another Ubuntu PC with SATA ports that I could try connecting it to.

---

### Post by JimLS on 2018-04-03
Ran across a method to test spinning easily.  with the drive loose tilt the drive and if it is spinning you should feel the gyroscopic effect - it should resist movement.  Did that and it spins initially but after about 20 seconds (I didn't time it so I may be off quite a bit) it stops spinning.

---

### Post by oldfred on 2018-04-03
If UEFI is not seeing it that is a major problem.
But first thing to check is if connections are tight & then cables. 
If you have other cables try them.

---

