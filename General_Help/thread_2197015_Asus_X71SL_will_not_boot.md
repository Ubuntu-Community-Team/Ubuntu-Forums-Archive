---
title: "Asus X71SL will not boot"
date: 2014-01-01
forum: General Help
---

### Post by amelia_tj on 2014-01-01
i  am trying to run ubuntu 12.04 64 bit on an Asus X71SL, i cannot get it to boot after installation. i had to use nomodeset to install after that i get a black screen with flashing cursor. sorry for the lack of detail. does anyone know a workaround to get ubuntu to boot? thank you.

---

### Post by oldfred on 2014-01-01
If you had to use nomodeset to install, you will need it on every boot until you install the nVidia proprietary drivers.

About 1/3 of the way down is the grub screen example on adding nomodeset. I use e on grub menu, scroll to linux line and replace quiet splash with nomodeset.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by amelia_tj on 2014-01-01
alright. tried that, didnt work so i reinstalled used acpi=off this time upon restart after installation i get the purple ubuntu screen. no mouse nothing. thank you for your help.

---

### Post by oldfred on 2014-01-01
Is this system dual video and can you control which video mode it boots in?
Nomodeset works with nVidia, but Intel often needs other settings.

Some other Asus. Not sure if any of their issues are similar.
 ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

---

### Post by amelia_tj on 2014-01-08
i got ubuntu to boot but now i have a plethora of problems... no wifi, no function keys, no sound, freezes after a few mins. have to reinstall ubuntu after i try an nvidia driver. too many problems. this is the first time ive had so much trouble with linux. no idea how to fix any of this time to start new threads i guess. thank you.

---

### Post by oldfred on 2014-01-09
Best to take each major issue as a new thread with issue & chip type in title. Then correct driver may be known by someone else and they will post.
Sometimes BIOS settings or boot options solve several issues at once, but are unique to specific chip and sometimes how vendor enables it.

One BIOS setting.
[http://askubuntu.com/questions/164376/installing-12-04-on-a-asus-x71sl](http://askubuntu.com/questions/164376/installing-12-04-on-a-asus-x71sl)

See posts near end of thread
[http://ubuntuforums.org/archive/index.php/t-1662577.html](http://ubuntuforums.org/archive/index.php/t-1662577.html)

---

