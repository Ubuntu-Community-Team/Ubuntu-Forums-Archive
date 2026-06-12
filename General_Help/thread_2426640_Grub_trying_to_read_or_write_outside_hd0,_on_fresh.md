---
title: "Grub trying to read or write outside hd0, on fresh install"
date: 2019-09-11
forum: General Help
---

### Post by pr-redstone on 2019-09-11
So recently i decided to switch distros back over to ubuntu, because i dont have drivers for my gpu on anything but ubuntu redhat centos or seus. Cause logic. And all went fine in the install but once i booted it got to grub rescue saying "attempt to read or write outside hd0". 
Thinking it qas a one time issue i tried reinstalling, same thing... Different usb with a fresh installer, yep. Different distro. All is fine tho. 
Idk why but the grub installer is broken for me, any ideas, oh and the boot partition when using ls on grub has an unknown filestructure... So maybe thats a hint as to the root cause...

Gpt for the table type

Now in the mx grub is working but when trying to booy ubuntu says the same error but eith an extra line about meeding the kernal booted first

Edit: for info there are 6 partitions. 
Part1 is for the mx grub install 1 gig
2 and 3 are swap partitions both 64 gigs
4 is for mx,s files64 again
5 is the biosboot for ubuntu
Part 6 is for ubuntu's  files about 8TB rougly give or take a bit


Trying to ls anything other than the top of part6 via grub gives the read write outside hd0 error. So ive got someore info, will post more when i do more testing in a bit,

---

### Post by oldfred on 2019-09-11
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

