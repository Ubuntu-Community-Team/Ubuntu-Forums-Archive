---
title: "How can I boot in Ubuntu or remove Ubuntu from my system"
date: 2013-09-16
forum: General Help
---

### Post by guneshgt2 on 2013-09-16
Hello Experts, 

I am a newbee to Ubuntu and  this might happen to be a repeated question  of a sort but I would like to ask it here as I could not find the answer  for my exact case.

I am trying install Ubuntu 12.04 LTS on my  new DELL INSPIRON 5520 which came with a pre loaded Windows 8 but some  how it was not getting completed. At last after reading different blogs  and forums like this, i could finally install it (i could run thru the  process) and Installed Ubuntu on my machine.
But now the problems are,

a. When I start my laptop sometimes I  see the grub but it never displays existing Windows 8. To make something  clear here, while installation Ubuntu didn't detected the existing  Windows 8 OS but I still went ahead and installed it. The GNU/GRUB  location is in the separate partition of Ubuntu. How can I get the entry  of Window 8 in the GRUB?

b. Ubuntu doesn't boots giving different errors each time.

c. If I want to remove Ubuntu, How can I remove it now and at least restore the old Windows 8 booting?

So  apparently I am not able to boot my machine in the normal way as there  is no windows entry in the grub and Ubuntu doesn't boots..... :(

Can anyone please help me out here....

Thanks

Gunesh

---

### Post by TheFu on 2013-09-16
Read the relevant links in my signature, especially **boot-repair** and **boot-info**. If that doesn't work google for "ubuntu UEFI" and try to remember if you followed those instructions.

Windows8 has been causing issues since SecureBoot, UEFI and GPT disks are all relatively new.

---

### Post by jamesisin on 2013-09-16
You might launch the live CD (the installer CD) and from there run GParted.  This should show you all your current partitions.  You can see there if your Windows partitions still exist.

Regardless, the links TheFu has provided are full of useful information.

---

