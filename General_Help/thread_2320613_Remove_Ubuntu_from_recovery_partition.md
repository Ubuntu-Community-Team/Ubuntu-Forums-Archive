---
title: "Remove Ubuntu from recovery partition"
date: 2016-04-15
forum: General Help
---

### Post by elie-mrad88 on 2016-04-15
I had windows 8 on my laptop HP Envy DV6-7304ee when I bought it and it came with a recovery partition (D: drive). I upgraded to 8.1 then windows 10. At some point, I installed Ubuntu alongside Windows (I think it was windows 8.1) with dual boot from Grub. I then removed Ubuntu and upgraded to windows 10. However, my HDD has been having problems. So I bought an SSD drive and decided to recover my laptop from the recovery partition to clone a clean copy of windows 8 as it came from the factory. The recovery went fine; however, when I had to do the recovery again, the recovery menu could not find it. Only reset and refresh were available (options from microsoft not from HP) and even the reset did not work. I logged in to windows and went to the d: drive. There was only one folder "EFI2" and a file "recovery". Inside the folder was two folders "boot" and "ubuntu". So I checked for hidden system files and found all windows recovery files and folders. How can I remove ubuntu files from the recovery partition and restore it to the factory settings (only windows 8). I can't unhide the files and folders manually.

---

### Post by grahammechanical on 2016-04-15
The last Microsoft OS I used was Windows 98. And as you only have Windows on that machine I am no help.

---

### Post by nerdtron on 2016-04-15
You mean, you still the Grub boot menu? Last time I tried, windows will be happy to wipe it out from your drive. Boot into recovery mode, then choose Startup (or boot?) repair. Next time you boot, the Grub should no longer show. (at least on Windows 7 this worked).

---

