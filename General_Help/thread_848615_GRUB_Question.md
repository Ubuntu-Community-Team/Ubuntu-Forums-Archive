---
title: "GRUB Question"
date: 2008-07-03
forum: General Help
---

### Post by halon on 2008-07-03
I recently built a new system. At the time, I did not have a retail copy of XP so I used an XP disc that came with one of my laptops to partition and get running. However, I never thought about re-installing XP when my retail copy arrived and I installed GRUB on sda1 (the windows partition).

I assume I must move GRUB to my LINUX partition before I reinstall. My thought is to install GRUB on sda2 (my root partition) and then set sda2 to be the boot partition then reinstall. 

Any tips??? 

Of course I will back everything up because I can forsee something going wrong. 


Thanks in advance!!!

---

### Post by VMC on 2008-07-03
You can just go ahead and re-install XP over the old XP partition, which of course will wipe out Grub. 

Then a simple grub install will take over again. Or you can backup mbr using dd, then re-install mbr again using dd. Your flavor.

There are links about installing Windows after linux is installed.

---

### Post by nick_h on 2008-07-03
Here is a link - [Recovering Ubuntu After Installing Windows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

