---
title: "Laptop Recovery Partition"
date: 2008-03-05
forum: General Help
---

### Post by Scorpuk on 2008-03-05
My hardcrive is dieing (SMART Status Bad) :(

I copied my data using the ubuntu live CD to a usb drive.


I then installed ubuntu and managed to work out that is it damaged in only half the drive as I could boot with an installation to 50% of the HDD.


BUT now I want to reinstall windows before sending the laptop back and I cannot get the recovery partition to boot as it looks as though grub decided to take that partition as the boot partition totally destroying the boot option to recover.


Any idea on how to reinstate this?


All the data is still there to do the recovery, just cant get the thing to boot to it. :|

---

### Post by maxmanders on 2008-03-05
You could try using the live cd and running gparted to view your partitions - I can't be certain but I believe there is an option to set active partitions, i.e. the recovery partition.  It'd be interesting to see what comes out of this because I have often had the same sort of concerns, should I ever need to return my laptop under warrenty.

---

### Post by Scorpuk on 2008-03-06
I used ubuntu install to take a copy of the recovery partition.

Its just that ubuntu used the recovery partition as the boot partition over writing the MBR with grub, so now I need a way to reinstate xp boot to that partition to get it to boot from it.


I have also been trying to find a way to create a boot dvd with the information, but man thats a whole world of pain. No simple solution. :-(

---

