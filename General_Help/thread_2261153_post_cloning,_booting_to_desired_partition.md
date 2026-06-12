---
title: "post cloning, booting to desired partition"
date: 2015-01-16
forum: General Help
---

### Post by jpvrlau on 2015-01-16
Cloned most current drive with another of  same size to disk with  dated cloned partitions .  Clonezilla was  used and defaults were accepted.
Everything looked identical.  After working a variety of booting issues  using linux boot-repair and window utilities I got things working  grub-wise.
The partitions sda5 and sdb5, the Unix partitions, always booted up from grub as expected.
UUIDs were changed for all partitions (including the windows partitions) to help with identification.
The main problem that concerns me now is that the Windows 7 partitions  for sda2 and sdb2 always boot to the C: partition, never to F: .
Both Windows partitions get mounted,ie, I can access both from the windows side.  
The desire is to get the grub selection(sdb**2**) for the  Window OS to behave like the Ubuntu choices where when you select a  particular partition for an OS in grub it takes you to that OS on that  partition.
Several Windows utilities (easyBCD, msconfig, disk management) were  employed trying to change this but no matter what I tried it booted to C:  
The ASUS bios allows me to select a specific disk but it never made a difference.  Selecting sdb**2** always boots to C: on the 1st disk(**sda**)**.**
Thanks!!!
Frustrated

I started making progress after using msconfig to change  "Selective  Startup" to "Normal Startup" which gave me 2 boot options instead of  just one for C:.  Marked the F: partition as default.
Grub-wise I ended using the link below to get things proper.  **I just can't trust grub2, grub-customizer, and/or boot-repair, especially  after cloning.**
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

### Post by overdrank on 2015-01-16
Moved to General Help

---

