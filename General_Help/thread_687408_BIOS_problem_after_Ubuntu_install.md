---
title: "BIOS problem after Ubuntu install"
date: 2008-02-04
forum: General Help
---

### Post by tpv616 on 2008-02-04
Hello,
I have a Dell Dimension 8300 with two hard drives - one 250GB SATA (which contains the Ubuntu partitions ~15GB and one NTFS partition with the rest) and a 160GB IDE (containing everything related to Windows XP - obviously one NTFS partition). After installing Ubuntu, I kept getting the error message "Error loading operating system" when booting normally, but if I go into the BIOS boot menu and select "Primary IDE", it takes me to the grub menu (which it should be doing normally). Question is, how do I make it so that the BIOS always boots from the IDE drive? My guess is that it keeps trying to boot from SATA, generating that error.

---

### Post by cdenley on 2008-02-04
You set the boot order in your bios configuration.

---

### Post by OffAxis on 2008-02-04
(you are talking about the BIOS setup utility and not some wacky Dell boot menu, right?)

Within the BIOS, sometimes the boot order only has 'hard disk' as an option, and there's a sub menu for setting the priority of the hard drive.

BUT, if you're setting that and saving the changes to the CMOS, it reboots, and then starts up how you want it to, then the setting isn't being saved in the CMOS.
Look for a BIOS update on Dell's site. If there's one just follow the instructions for flashing it.

Otherwise, you probably have a battery problem; bad battery, the battery contacts may be corroded, etc.
So crack open the case, pop the battery out (the silver disc about the size of a nickel) and take a look at the contacts. If they look good try replacing the battery.

---

