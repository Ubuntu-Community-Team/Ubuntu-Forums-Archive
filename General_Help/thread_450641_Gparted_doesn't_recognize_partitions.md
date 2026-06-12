---
title: "Gparted doesn't recognize partitions?"
date: 2007-05-21
forum: General Help
---

### Post by 67GTA on 2007-05-21
I was playing with a PCLinuxOS live cd and was using the partitioner. I selected the clear button because I wanted to stop and use Gparted to set up the partition before installing PCLinuxOS. I rebooted into Ubuntu and when I open Gparted, it shows the whole hard drive is empty. I selected the refresh devices option with no luck. Can I force it to show them? What could the PCLinuxOS cd have done to cause this? I have two 40GB partitions XP/Ubuntu and one swap.

---

### Post by 67GTA on 2007-05-21
I looked at the hard disk info with Gparted and it shows that the disk label type is unrecognized. It says to set a label will erase the hard drive. I didn't make any changes with the PCLinuxOS cd and "sudo fdisk -l" shows the partitions. Is there a file that stores this info for Gparted or does it generate this when it runs?

---

### Post by 67GTA on 2007-05-21
The PCLinuxOS installer still sees the partitions. That is weird.

---

