---
title: "Where is the Default Grub Config Found?"
date: 2007-11-09
forum: General Help
---

### Post by Azzuron on 2007-11-09
I have an odd System board in my computer, i think it was simply that i had the RAID controller (fake raid ofcourse) turned on when i did the install. At the time i didn't realize it was on. It confused me for sure, At the time i had a work around to install Ubuntu, that was to modify the boot line in the Live CD Grub. i had to add break=top to the end and boot that. I did so and now every time there is a kernel update the grub configuration routine adds break=top to the end of every boot option in the menu.lst. I have to manually edit out the command after a new kernel is installed. I would like it to stop doing this as i don't really need it since i disabled the controller in the bios. Where does it read this info from that i cannot seem to find it? If anyone has any thoughts please let me know. its rather annoying :( My KVM doesn't work when the system boots and i have to hook up a keyboard directly to the box. Thnx!

  --Dave

---

### Post by logos34 on 2007-11-09
[This]("http://users.bigpond.net.au/hermanzone/p15.htm#kopt") might be the culprit.

---

