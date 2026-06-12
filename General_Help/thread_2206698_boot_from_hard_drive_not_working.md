---
title: "boot from hard drive not working"
date: 2014-02-20
forum: General Help
---

### Post by vish2 on 2014-02-20
in fixparts when p is selected
it shows
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   2                  599525376    625141759   primary     Y        Y      0x83

a star (*) under the boot is missing ...how can i bring it back?

selecting hard drive in boot menu ...just blinks in black and back to boot menu
or it tries to run pxe rom 

pls help
completely new to fixparts and i screwed it up.....
hard drive is shown as unnallocated

---

### Post by vish2 on 2014-02-20
COME ON .....ISN"T anyone here an expert????!??!?!?!

---

### Post by BlinkinCat on 2014-02-20
> **vish2 said:**
> COME ON .....ISN"T anyone here an expert????!??!?!?!

Hi,

With your attitude you are more likely to turn help away.

It is considered reasonable to bump your thread after 24 hours. (not 30 minutes)

If you are lucky you may obtain assistance sooner,

Cheers -

---

### Post by varunendra on 2014-02-21
Coming here from your other thread on the same issue : [http://ubuntuforums.org/showthread.php?t=2206685](http://ubuntuforums.org/showthread.php?t=2206685)

Please tell us what is your goal here - recovering the partition(s) and data or making Ubuntu bootable.

Recovering partition will involve this guide and you may have to re-create the partitions after backing up your data (if it is recovered).
Getting Ubuntu to boot may require a simple reinstallation, discarding all current data and partitions.

---

### Post by oldfred on 2014-02-21
Grub/Ubuntu does not use boot flag to boot. (unless new UEFI and then boot flag just says which is efi partition)
Windows has to have boot flag and a few BIOS will not let you start to boot without a boot flag on any primary partition, so we still suggest a boot flag. You can add boot flag with gparted.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

