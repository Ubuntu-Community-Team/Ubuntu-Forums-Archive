---
title: "Installation freezes at splash screen/terminal"
date: 2021-08-02
forum: General Help
---

### Post by zhyph on 2021-08-02
Hi, I'm new to Ubuntu/Linux, first time trying to boot Ubuntu in an old pc, but every time I boot, it just doesn't work.
1. I've created a bootable USB with GPT/FAT32 LST Ubuntu image using Rufus.
2. Disabled Secure Boot on my Bios and boot my USB
3. Go for the Ubuntu/Ubuntu Safe Graphics options, both did not work
4. I've waited a lot for the &#8220;checking files&#8221; part, right now I'm skipping it.
5. When it reaches the splash screen where a reload icon run for a while and then stops.
6. When I open the terminal on splash screen, only one message that shows an error &#8220;failed unmounting /CD-ROM&#8221; and then it runs for a while before stopping on &#8220;Remove Stale Online ext4 Metadata Check Snapshots.&#8221;
GRUB Failed boot detection is all over the place when I open the terminal.

The notebook that I'm trying to install Ubuntu is an Aspire ES 15 &#8212; ES1-533-C27U.

---

### Post by y-fatkullin on 2021-09-24
I have the exact same problem with an Acer Aspire ES1-533-C8M1 laptop.
I installed an earlier version of the system (18.04 seems to be) and updated to the latest. This series of laptops have a UEFI issue. When installing an early system, you need to install GRUB with the --no-nvram option and move and rename the grubx64.efi (with other files) file to EFI/Microsoft/Boot/bootmgfw.efi


This is short, I did it for a long time.


I suspect that the problem with downloading new versions of Ubuntu is in the secureboot-db package, it probably somehow works with nvram, which only works adequately with Windows

---

