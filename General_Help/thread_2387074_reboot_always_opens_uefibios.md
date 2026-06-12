---
title: "reboot always opens uefi/bios"
date: 2018-03-14
forum: General Help
---

### Post by TechnoJunky on 2018-03-14
I just installed Ubuntu on my Windows gaming computer (now dual boot).  The machine has 2 hard drives, one for C and one for D.  i resized my C drive and created extended partitions for Linux.  I'm able to boot to both OSs no problem, except that every reboot automatically loads the bios and I have to exit before I can get the Grub menu to load.  I'm assuming this is a grub issue.  This didn't occur when it was just Windows.  When I installed Ubuntu it stated that if I continued with UEFI mode that other OSs might not boot afterwards, so I clicked go back instead of continue.  This is a home grown PC, not a proprietary one, I didn't have safe boot on.  I had to install Ubuntu twice because the first time I told it to modify the boot record on the default sda but when rebooting it went straight to Windows.  Second install I told it to boot to sdb.  Don't recall if the first boot loaded the bios or not, but now every boot does.  Any help in getting this resolved would be appreciated.

I went into the bios and reset it to defaults and changed the things I needed back to what they should be, but still enters bios screen every time.

---

### Post by rbmorse on 2018-03-14
This usually happens when the system EFI (what used to be the BIOS) can't find a valid boot configuration at the location specified in the UEFI setup.  

Check your setup.  There is probably a section for configuring boot items and one of the settings in that section will probably allow you to specify which of the detected boot configurations to load at startup.  There may the option to list a several in a hierarchy, but on my particular ASUS motherboard if the configuration in the first slot is not valid the machine stops and opens the EFI setup menu as you described.

---

### Post by TechnoJunky on 2018-03-14
I know what you're talking about, I have an Asus motherboard as well.  I don't recall making any changes there but will check it out after work.

---

### Post by TechnoJunky on 2018-03-14
The fix was as goofy as the break.  As I said, I only have the 2 hard drives.  Not sure why, but the boot loader for Windows was on the second (D drive).  When installing Linux, I had to use the same one (SDB).  I went into the bios and swapped it so that the smaller drive (SDA) would boot, and it failed with a grub rescue prompt.  I rebooted went back into the bios and swapped it back so SDB was booted to and now it no longer goes into the bios every boot.

---

