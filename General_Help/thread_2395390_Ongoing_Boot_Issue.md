---
title: "Ongoing Boot Issue"
date: 2018-07-01
forum: General Help
---

### Post by johnnybro66 on 2018-07-01
Alright. So first I completely wiped my windows 10 hardrive via the clean all command in the windows disk installer. Then I tried Linux Mint. Did not work. Now Ubuntu is giving me the same issue. Here is the issue:
I boot from a usb that contains the ubuntu iso file, which was done with rufus. It boots fine, and I have the option to install ubuntu, to try without installing, and a couple other options. I install the OS and delete everything else on the harddrive. I then go to reboot it without the usb. I recieve my Acer logo for about 1 second, then a "Checking Media: [Failed]" message. Rinse and repeat forever. 

I would appreciate help greatly. I have been on this for 3 days now. I have tried various fixes of which none work. I am willing to try anything. Thank you.

---

### Post by johnnybro66 on 2018-07-01
Booting to [COLOR=#000000]/EFI/ubuntu/shim64.efi fixed the issue.[/COLOR]

---

### Post by oldfred on 2018-07-01
If an Acer, you normally need to update UEFI to latest version from Acer.
Then enable "trust" on the Ubuntu/grub .efi boot files from inside UEFI.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

