---
title: "Recovering Lost Partition"
date: 2008-06-07
forum: General Help
---

### Post by Bunni on 2008-06-07
While moving a partition on one of my drives (using gpart) my power had gone out during the process, now the drive does not display on my computer. When i try to access the drive in windows, im asked if i would like to format it... The drive still shows as the correct size, what can i do to get it back!?


Any and all help will be greatly appreciated!

---

### Post by housam on 2008-06-07
Try this way using [[COLOR="Red"]_fdisk partitioner_[/COLOR]]("http://tldp.org/HOWTO/Partition/recovering.html")

---

### Post by jimbob on 2008-06-07
Are you using the stand alone live CD for Gparted?  What does it show now ?  Can it see the drive?

---

### Post by Bunni on 2008-06-07
> **jimbob said:**
> Are you using the stand alone live CD for Gparted?  What does it show now ?  Can it see the drive?

At the time i was using 7.10 64bit live cd, the drive (180gb) was at the time partitioned roughly:
|unpart size:?|~125gb ntfs | 12gb ubuntu | 1.3gb swap | 8mb mb | 4.5gb unpart |

You can see why i was moving things around, i had gpart moving the ntfs, ubuntu, swap, and 8mb to the front of the drive so i could group the unpart space together. The last time i checked the progress of gpart, it was roughly 30gb into the first step of moving the ntfs partition (the power went out roughly 5-10 minutes later).
Windows currently shows it as:
|~118gb ntfs | 12gb ? | 12gb ? | 1.39 swap | 8mb | 4.5 unpart |

Currently im booted into XP (which is on a different drive) using a program recommended by a colleague (Active Partition Recovery). As soon as this finishes i shall reboot into the 7.10 live cd i have and post what gpart can see.
> **housam said:**
> Try this way using [[COLOR="Red"]_fdisk partitioner_[/COLOR]]("http://tldp.org/HOWTO/Partition/recovering.html")
Thanks for the recommendation, i shall try this out as soon as this Active Partition Recovery finishes trying.

---

### Post by Bunni on 2008-06-08
resolved, was able to recover all the files using Active File recovery and create a new partition with the same drive letter as the last one. Everything seems to be working great now...

Thank you everyone for your help

---

