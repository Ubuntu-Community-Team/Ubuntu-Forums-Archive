---
title: "Question about grub"
date: 2007-08-01
forum: General Help
---

### Post by lbyrd33 on 2007-08-01
I have ubuntu feisty and vista installed on the same hard drive on my laptop. I would like to install other linux os's on my external usb hard drive and boot them still from the ubuntu grub written on my MBR. I have been able to succesfully install fedora 7 on my external hard drive and I chose for it to not overwrite my ubuntu grub. I edited the ubuntu grub and pointed it to where fedora is installed;however, upon boot it gives an error message that it is not able to mount the fedora root partition.

Anyway, I guess my question is if their is a way to edit the grub to mount the selected partitions or some other way I can get around. Any help on this matter will be greatly appreciated.

---

### Post by confused57 on 2007-08-01
I would recommend trying a configfile entry to boot Fedora:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

