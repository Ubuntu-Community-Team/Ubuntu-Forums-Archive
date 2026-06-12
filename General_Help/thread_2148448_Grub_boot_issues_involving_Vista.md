---
title: "Grub boot issues involving Vista"
date: 2013-05-25
forum: General Help
---

### Post by Maintech on 2013-05-25
Using 12.04 I was able to choose either Ubuntu or Vista and boot either. I upgraded to 13.04 and lost the ability to boot Vista. I thought the issue was caused by upgrading instead of doing an install as I had other issues as well. I decided to do a 'fresh install' leaving only my home directory untouched. All went well and all the other issues I was having were solved. However, the booting issue has not been resolved. I have 4 drives. Vista is on drive 1 and Ubuntu is on drive 3. I have grub installed on drive 3 because Vista will not let me write to the boot mbr and I have bios set up to boot from drive 3. Ubuntu starts and runs from grub but Vista does not. However, I can go into bios and set it to have drive 1 as first boot and I don't get the grub menu but I do get to start and run Vista so there are no issues with the boot mbr in Vista. I was using drive 3 for grub when running 12.04 and had no problems with booting Vista so it has to be something different with grub in 13.04. Grub2-pc is a bit different from what I have worked with in the past so I am not very familiar with it. Any ideas what could be causing this issue would be appreciated.

---

### Post by Mark Phelps on 2013-05-26
You might be able to fix the Vista boot using Boot-Repair:  [http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by Maintech on 2013-05-26
Thanks. I tried that and several other things. Nothing worked. I could change the boot order in my bios and boot MS but I could not get grub to set up the bootloader correctly. I tried to edit grub.conf as a last resort. Again, nothing worked. And, I was getting no help from the forum. So, I downloaded 12.04 alternate 64 and installed it, removing the 13.04 and it's version of grub2. My computer is back to running well again and grub2 works as it is supposed to allowing me to dual-boot. I had to down-grade my wife's computer as well due to the 'glitches' and it ran slower than 12.04. So, my computer and my wife's are both back to 12.04 and running great. The only computers I have that ran well on 13.04 is a VERY old dell precision 530 with dual 32 bit xeon processors and an almost new hp pavilion with A8 AMD quad-core. Nothing else I have works correctly with it.> **Mark Phelps said:**
> You might be able to fix the Vista boot using Boot-Repair:  [http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

