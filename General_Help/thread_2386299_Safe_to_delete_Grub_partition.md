---
title: "Safe to delete Grub partition?"
date: 2018-03-03
forum: General Help
---

### Post by harry5552 on 2018-03-03
using a dual boot win 10 & ubuntu 16.04 system configured as attached

I've freed up 200gb from the win partition (sda3) to hopefully use in Ubuntu (sda5, sda7), but the grub partition (sda4) is sat in the middle and the option to Move it option is grayed out.

not sure what to do, can I delete the Grub partition it and re-create immediately after sda3? - if so, how do re-create that partition?

thanks for help and sorry for probably asking thicko questions but I'm so worried about messing it up and not yet that confident with the linux file system

---

### Post by oldfred on 2018-03-03
It looks like you should not even have the bios_grub partition.

If Windows is UEFI boot, generally better to have Ubuntu as UEFI boot.
Then both systems share the one ESP - efi system partition, your sda1.

The bios_grub is required by Ubuntu/grub for BIOS boot on gpt partitioned drives.
You can delete it if you install grub-efi-amd64 for UEFI boot. Often a bit easier with Boot-Repair and its advanced mode when booted in UEFI mode.

 Or you can delete it and create a new bios_grub anywhere within 2TiB on a drive. It must be unformatted and have bios_grub flag if using gparted or code ef02 if using gdisk to create partition.

What brand/mode system? Some do make it  a bit more difficult to use UEFI boot. But many work arounds, depending on configuration.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

How you boot install media, it then how it installs, UEFI or BIOS.
And this shows both boot mode's first screen.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by harry5552 on 2018-03-06
thanks for that mate, will get rid of it (after a backup of course :D )

---

