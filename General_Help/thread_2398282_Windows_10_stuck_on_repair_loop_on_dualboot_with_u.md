---
title: "Windows 10 stuck on repair loop on dualboot with ubuntu 18"
date: 2018-08-09
forum: General Help
---

### Post by jeunez on 2018-08-09
Today I booted into Windows 10 (Insider), but unfortunaly it shut down when starting up (battery issues). 

Anyways, afterwards, I couldn't boot into Windows anymore. It would show the error screen (before login screen) and said it will restart the laptop. When rebooted, it tries to do some repair thingy but goes into the same error screen, these 2 things iterate everytime I try to boot Windows. Internet says after 2/3 times you would get into the safe/repair-mode but I don't, which isnt irregular.

Pushing f8 or anything like that never worked on my laptop (or any other key combination) and the only way I ever accessed the safemode/advanced-boot-options was doing something where you had to get into Windows itself first. I would like to get into these advanced boot options to reset Windows.

Now I am still able to enter Ubuntu 18 using grub2 and wondered if I could use this somehow to get into the Windows safemode. If Windows gives you the option to get into these settings on the next startup, there should be some way to trigger this from grub/ubuntu or not? I also installed grub-customizer ([https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)) trying to add some safeboot Windows option in grub2 but I'm not sure how to do it or if it is even possible, but I saw the suggestion on this forum, no instruction were given however ([https://ubuntuforums.org/showthread.php?t=1676518](https://ubuntuforums.org/showthread.php?t=1676518)). It showed me the boot sequence for Windows, maybe I can edit something there? 

```
insmod part_gpt
insmod fat
set root='hd0,gpt1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --
hint-efi=hd0,gpt1 --hint-baremetal=ahci0,gpt1  3EEE-6D97
else
  search --no-floppy --fs-uuid --set=root 3EEE-6D97
fi
chainloader /EFI/Microsoft/Boot/bootmgfw.efi

```

Any help would be appreciated in order to fix this problem. I backed up ubuntu and saved the important files on Windows on an external disk already, but would prefer to not wipe everything. I'm using an ASUS Laptop.

---

### Post by oldfred on 2018-08-09
Grub only boots working Windows.

But you may be able to use Linux NTFS repair tool which really does not do anything but turn on the chkdsk flag. With chkdsk flag set you cannot mount NTFS from Linux, nor if Windows is hibernated/fast start up on. But then Windows may immediately go to safe mode?

       sudo ntfsfix /dev/sdXY #where  X - drive Y - partition

---

