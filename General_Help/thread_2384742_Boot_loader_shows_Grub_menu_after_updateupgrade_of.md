---
title: "Boot loader shows Grub menu after update/upgrade of Ubuntu-MAte 16.04.3"
date: 2018-02-11
forum: General Help
---

### Post by smith73 on 2018-02-11
After recent Ubuntu 16.04.3 update and upgrade while restarting the boot loader doesn't get into a usual menu to choose an operating system in dual-boot with Windows 8.
Instead it shows command prompt grub> and a list of commands by Tab key. After typing "exit" in grub> command line it starts Windows. 
What command to use to start Ubuntu from this grub> menu?

Don't the developers understand that if they want to attract more users to using linux and ubuntu, such issues should be avoided? Why a user is supposed after such updates to spend several hours or more on finding out how to use these commands?

---

### Post by Jan_Koichi_Dayanan on 2018-02-28
I already have 2 laptops with encrypted disks that were affected by this. Any news on how to resolve this?

---

### Post by oldfred on 2018-02-28
@Jan_Koichi_Dayanan 
Best to start your own thread as your hardware configuration and install configuration is most likely not exactly the same as the OP. Also post Boot-Repair's summary report.

Smith73 Post this:
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

Also post brand, model system & what video card/chip?

Not sure if Boot-Repair correctly asks to un-encrypt the / partition, if encrypted, but you must do that before running report or repairing.

---

