---
title: "How to remove Grub without Windows"
date: 2015-08-03
forum: General Help
---

### Post by jas-gagne on 2015-08-03
Hi, I just fully installed Ubuntu Mate on my ssd which had Windows 10 on it, and for some reason Grub has installed. I do have other hard drives which didn't have windows installed in them, however it's reading one that seems to have windows 8.1 which doesn't lol. Is there a way to remove grub so my computer can automatically load Ubuntu without interruptions? 

Thank You.

---

### Post by pqwoerituytrueiwoq on 2015-08-03
i believe that could be worked better, but i think you are saying you had win10 install present during a kernel update or new install that is no longer present in the system
in which case you just need to run [FONT=courier new]sudo update-grub[/FONT]
if you remove grub you can not boot, if you only have 1 OS grub2 will boot that one without asking you any question unless you hold shift

if that does not work post the output of [FONT=courier new]sudo parted -l[/FONT]

---

### Post by grahammechanical on 2015-08-03
There is another way of looking at this and that is to say that the machine has a UEFI boot system and the reference to windows 8.1 is in the UEFI and not in Grub. We do not have sufficient information.

Regards.

---

### Post by oldfred on 2015-08-03
With multiple drives and multiple installs best to see details.
And is system UEFI or BIOS? Be sure to boot Boot-Repair in same mode as installs.
If BIOS which drive do you boot from?

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

