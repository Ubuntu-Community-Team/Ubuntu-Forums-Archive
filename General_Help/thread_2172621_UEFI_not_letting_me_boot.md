---
title: "UEFI not letting me boot?"
date: 2013-09-05
forum: General Help
---

### Post by Taylor_Martin on 2013-09-05
[COLOR=#000000]So im having this issue getting ubuntu 13.04 to dual boot with windows 8 on this laptop. Its an Asus G75 VX, it has UEFI and i didnt know anything about this new kind of bios untill i started having problems. First off, in order to get the live cd of ubuntu 13.04 to even boot so i can install, i have to enable secure boot, which i did. After getting it to install as a dual boot, it didnt load grub, so i did the boot-repair fix and it kinda worked, now grub comes up, but when i select ubuntu, it just goes to a black screen, my HD spins up like its going to do something, then goes inactive. Boot repair seemed to work, but now my install of ubuntu doesnt...any suggestions?[/COLOR]

---

### Post by oldfred on 2013-09-05
It sounds like you are booting, but have video issues.
What video card/chip do you have? Or is it a dual video system?

Most will at least boot to default video with nomodeset boot parameter.
From grub menu press e, scroll to linux line and replace quiet splash with nomodeset. 

 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some new systems need additional or other boot parameters also.

Some other Asus which may be similar:

 HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
      
 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

---

