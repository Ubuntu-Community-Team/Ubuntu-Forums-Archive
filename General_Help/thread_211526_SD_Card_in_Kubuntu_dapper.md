---
title: "SD Card in Kubuntu dapper?"
date: 2006-07-08
forum: General Help
---

### Post by deuce868 on 2006-07-08
I've been searching for how to get my SD card reader working on my HP dv5000t laptop. In looking over the past threads it seemed that this was supposed to be corrected in dapper, but I also saw some notes that SD card readers were working better in 2.6.17 whereas I seem to have .15 right now. 

Can anyone update on what the status is and if this should/should not be working?

Thanks for the help/pointing me to the right places.

---

### Post by deuce868 on 2006-07-09
bump?

I did find a post that texas instruments readers could work. They has some instructions like this

> 
$ lspci -n |grep 0805
0000:08:06.3 0805: 104c:803c

$ setpci -s 08:06.3 4c=22
pcilib: Cannot open /sys/bus/pci/devices/0000:08:06.3/config


Any hardware gurus know where I can go from here?

Thanks

---

