---
title: "vmware cd booting"
date: 2005-06-16
forum: General Help
---

### Post by oly on 2005-06-16
hi, i am trying to setup vmware on my pc so i can run a few windows apps in particualr psp9 as i dont like gimp and it misses some of the features i use like, media layers and vector layers, i have it installed and working fine but i can not get it to recognise a bootable cd.

i have 2 cd drive and tried these drives
/dev/hdb/ 
/dev/hdd/ 
/media/cdrom 
/media/cdrom1
/dev/dvd
/dev/dvd1
/dev/dvdrw
none of them seem to let me boot but both drives work fine in linux and mount onto desktop, what should i use ? and any ideas as to why vmware does not pick them up ?
i tried the windows cd and a ubuntu live cd neither worked and it skips to the network boot phase.

---

### Post by intangible on 2005-06-17
VMWare 5 or 4?  5 seems to handle an already mounted cdrom ok, but 4 always gave me trouble if the cdrom was already mounted (eg: icon on the desktop).  Try umount /dev/cdrom and then see if it works.

---

### Post by faqpete on 2005-06-18
Hi!
My device ist set to /dev/hdc, I enabled Legacy emulation and for the Virtual Device Node I used IDE 1:0 ... That works for me
Regards
faqpete

---

