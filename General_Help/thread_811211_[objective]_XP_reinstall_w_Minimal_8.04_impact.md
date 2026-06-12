---
title: "[objective] XP reinstall w/ Minimal 8.04 impact"
date: 2008-05-28
forum: General Help
---

### Post by borisattva on 2008-05-28
I need to put on XP onto this Ubuntu box which has been MS free for over a year. It was a fresh Ubuntu install with following drive layout:


/dev/sda 100gb
/dev/sda1 29.29gb /
/dev/sda3 60.03gb /home
/dev/sda2 Ext
+/dev/sda5 4gb SWAP

/dev/sdb 250gb
/dev/sdb1 78.15 Former WinXP partition
/dev/sdb2 Ext
+/dev/sdb5 154.73gb Former WinXP Dox&Settings partition (ext3 filesystem for cross OS sharing)


when i boot from the xp install cd, i am able to view them all, and i have alreday succesfully formatted the /sdb1 over, in hopes of putting the xp back on, but instead i get NRM saying "to install windows xp on sdb1, the installation must be able to write to the the /sda drive, which it cant do becaus ethat drive is not formatted for use with windows. (i'm paraphrasing here).

i'm guessing its trying to write the boot section so the sdb1 can be booted into after installation, but i'm not sure how i'm supposed to accomplish this without affecting the linux install.

is this happening because linux is on the primary drive and xp wants that for itself?

is there anyway to install xp without swapping drives (and screwing up the order in the process) ?

its a shame i have to install xp on this box when it purrs along on ubuntu 8.04 so well, but i absolutely need it back to be able to run some applications from work. any insight is much appreciated.

---

### Post by borisattva on 2008-05-31
to recap:

i had a 100Gb hd set as MASTER on a PRIMARY ATA controller.

i decided to add a 250gb HD as SLAVE to install xp along side ubutnu, but was prevented by the XP installation wizard from installing on SLAVE, without reformatting the drive on MASTER.

solution was to swap the HD's around. making the 250gb temporary MASTER, installing XP, and switching around.

XP proved to me auto capable of recognizing the drive change and reconfiguring itself appropriately, even with the added complexity of a shared EXT3 partition on the 250gb as the shared docs drive.
Ubuntu on the other hand detected the windows partition and saved me the trouble of configuring grub.

Ubuntu Fi

---

