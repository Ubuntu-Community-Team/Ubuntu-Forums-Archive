---
title: "How does Ubuntu's boot directory work?"
date: 2007-08-14
forum: General Help
---

### Post by zorkerz on 2007-08-14
Im currently running Gutsy Gibbon and I wanted to try and install Gentoo as a learning experience for me. Gentoo wanted me to create a separate small (32MB) partition for its boot directory.
Ive been trying to figure out the best way to set this up. How do boot partitions or directories work? Does each os need its own or can i just add gentoo into the grub already installed from Ubuntu?

I was thinking it would be nice to have one small boot partition for both OSs as gentoo was requesting but then I realized I did not know if they each needed their own or how any of that would work.

So if it makes sense I would like to move the ubuntu boot directory to a separate partition and use that partition as boot for any os I install.

Im not sure where to look to start answering these questions so I came here.

---

### Post by distroman on 2007-08-15
You could just add gentoo to your current grub and it would be fine. 
I always create my boot partition with the first install, but I am pretty sure it should be fine doing one afterwards. 

If you plan on keeping old kernel's or even install more OSs I think you want to give it a bit more space then 32MB.

I would create a boot partition, remove grub, then reinstall grub on the boot partition according to this howto.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Then I would go ahead with gentoo, when you come to installing grub in the handbook or whatever you are using, skip it, and just put gentoo into your already installed grub on your boot partition.

---

### Post by zorkerz on 2007-08-16
Thanks your advise is just what I needed. Ill give it a whirl and let ya know what happens.
cheers

---

### Post by zorkerz on 2007-08-17
wow 
alot of playing around and i finally got it all down. Gentoo is booting (well the bootloader works at least) and I now have ubuntu using my new boot partition.
Thank you much

---

### Post by louieb on 2007-08-17
The main problem with sharing /boot between a Debian based distro such a Ubuntu comes at kernel update time. I used to have Fedora and Ubuntu sharing a /boot partition. Every time there was a kernel update the /boot/grub/menu.lst configuration file would wind up all messed up. Just be sure to keep a backup of that file. 
You might want to look at Dual Boot link in signature and find the section on chainloading or the configfile option. IMHO both work without any problems.

---

