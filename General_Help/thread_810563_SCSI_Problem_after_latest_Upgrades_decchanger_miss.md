---
title: "SCSI Problem after latest Upgrades /dec/changer missing"
date: 2008-05-28
forum: General Help
---

### Post by bleeding-edge on 2008-05-28
After the latest batch of upgrades I can't find the Tandberg Autochanger and HP Drive in it any more. It was previously listed under /dev/changer. The Tandberg was accessible under /dev/nst0 and the tape drive itself was represented by the device /dev/sg1.
After rebooting with the new Kernel 2.6.24-17-generic it was missing. Changing GRUB to 2.6.24-16-generic wont let them come up any more either.
scsiinfo -l doesn't see any of the devices.
/dev/changer is missing too.
adding st and sg modules to /etc/modules doesnt change anything.

Do any of u have any idea? I'm stuck here.
Please tell me if you need any other logfiles than the attached output of dmesg. The only relevant line I can see in there is:

[   62.433292] scsi3 : ioc1: LSI53C1030 C0, FwRev=01032700h, Ports=1, MaxQ=255, IRQ=23

This could be one of the tape library components.

Any help would be appreciated

Thx

---

