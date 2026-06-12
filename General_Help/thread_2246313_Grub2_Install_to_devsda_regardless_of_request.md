---
title: "Grub2 Install to /dev/sda regardless of request?"
date: 2014-09-29
forum: General Help
---

### Post by adriancohea on 2014-09-29
I have two hard drives. One spinning rust waffle cake on /dev/sda, and one shinny SSD from the future on /dev/sdb.

I select /dev/sdb as the installation destination. Ubuntu's grub is written to /dev/sda anyway...

I can see an argument for installing the bootloader to a different device than the OS, but the installer should have at least warned me this was going to happen or provided me an option to install the bootloader to /dev/sdb.

---

### Post by yancek on 2014-09-29
Are you selecting the "Something Else" option under installation type and then selecting "Device for bootloader installation" as /dev/sdb?  The default unless you select something different will be /dev/sda which is shown on that page.  If you are using one of the auto or semi-auto installs I don't think you get a choice but am not really sure as I never use another option.  If you posted more information someone might be able to give you some advice.  You could google "bootinfoscript" and go to their site and download and run it and post the output here, a results.txt file.  You haven't mentioned any other operating system so we expect that you have only one OS and that it is Ubuntu?

---

### Post by adriancohea on 2014-09-29
Under "Disk Setup" I was using "Guided - use entire disk and set up encrypted LVM" and selected "SCSI3 (0,0,0) (sdb) - 240.1 GB ATA Corsair Neutron."

I guess I sort of had the expectation that the bootloader would also be installed to /dev/sdb since I'm "using the entire disk." Again, I can see the argument for installing to /dev/sda by default, but I feel like the grub-install location should match everything else unless an option is provided. It just doesn't feel very "guided" to me that I'm installing the operating system on /dev/sdb but the bootloader is bring written to /dev/sda.

I can see that choosing "Manual" would have given me an option to select the device for the bootloader.

Anyway, these are my partitions (hence why I didn't want /dev/sda messed with)

/dev/sda1 104M (Windows wasting space)
/dev/sda2 122G (Windows)
/dev/sda3 64M (Arch Linux /boot)
/dev/sda4 790G (Arch Linux LUKS container)

---

