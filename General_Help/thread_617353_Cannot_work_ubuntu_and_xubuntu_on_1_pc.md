---
title: "Cannot work ubuntu and xubuntu on 1 pc"
date: 2007-11-19
forum: General Help
---

### Post by sponsoredwalk on 2007-11-19
Hello i am using ubuntu 6.06 with 256ram and yesterday after many arduous and time consuming tries i downloaded the xubuntu 7.10 alternate iso (the many downloads beforehand had problems...md5\defect cd...) to burn and put on my newly purchased second 400g hard drive. I cannot access or mount the drive through ubuntu 6.06 although it shows up in 'computer' and cannot enable or format it using gnome partition editor. So i tried to put xubuntu on my new 400g hard drive clean from ubuntu (ubuntu 6.06 is on my 40g maxed out master drive - 900mb free!!!) and it installed fine. however the last question asked to install on grub and said it should be fine with the listed OS' (it listed ubuntu 6.06) and i clicked ok. then on rebooting i got error 21 and neither OS' loaded. I put in my old ubuntu 6.06 disc and chanced reinstalling the grub menu which , thankfully, worked but there is no sign of xubuntu and when i load up from my slave drive i get error 21, my only idea would be to download the normal xubuntu 7.10 (not alternate) and, manually removing my 40g drive to allow the new 400g drive to be used, install xubuntu onto that. would there be a grub problem in that it would remove 6.06 or is there some way to fix the existing xubuntu? if its any help

sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664832 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot Start End Blocks Id System
/dev/hda1 * 1 4772 38331058+ 83 Linux
/dev/hda2 4773 4865 747022+ 5 Extended
/dev/hda5 4773 4865 746991 82 Linux swap / Solaris

Disk /dev/hdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot Start End Blocks Id System
/dev/hdb1 * 1 48548 389961778+ 83 Linux
/dev/hdb2 48549 48641 747022+ 5 Extended
/dev/hdb5 48549 48641 746991 82 Linux swap / Solaris

---

### Post by monktbd on 2007-11-19
can you post your grub menu.lst from your dapper installation?

manually adding the xubuntu boot options there should work if xubuntu installed properly.

---

