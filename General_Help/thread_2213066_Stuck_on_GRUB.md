---
title: "Stuck on GRUB"
date: 2014-03-24
forum: General Help
---

### Post by adrswimfast on 2014-03-24
Hello. I have tried to boot Ubuntu but only get taken to the grub menu (first image in album). When I select just Ubuntu it shows this blank red screen (second image in album) i have waited with this screen for 30+ mins. and it has not changed. Thanks. [http://imgur.com/a/ufCI8?desktop=1](http://imgur.com/a/ufCI8?desktop=1)

---

### Post by oldfred on 2014-03-24
Probably a video issue.
What video card/chip do you have?

       On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

Most need nomodeset but some need other boot options:
      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

