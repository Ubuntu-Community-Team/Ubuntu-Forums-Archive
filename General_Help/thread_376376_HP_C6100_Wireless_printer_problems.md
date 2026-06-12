---
title: "HP C6100 Wireless printer problems"
date: 2007-03-04
forum: General Help
---

### Post by manjo on 2007-03-04
Hi,

I had gotten the HP C6100 wireless printer to work before on my edgy box, but I think after an upgrade I get this error message: 

Printing: /usr/lib/cups/backend/socket failed

I use "CUPS", :/net/Photosmart_C6100_series?ip=192.168.1.101, and chose the appropriate make and drivers. I also tried other protocol HP Direct Jet, port 9100  but I get 

Paused: /usr/lib/cups/backend/socket failed

---

### Post by manjo on 2007-03-04
Correction: URI I used was : 

hp:/net/Photosmart_C6100_series?ip=192.168.1.101

I can  ping 192.168.1.101 but cannot print.

---

### Post by manjo on 2007-03-04
I also get this error if I use CUPS sometimes.. 

Ready: Unable to lookup host 'hp' - Unknown host

---

### Post by manjo on 2007-03-04
I had to apt-get install HPLIP drivers, and chose that driver. Also, I remove the word socket and put in hp:/net/Photosmart_C6100_series?ip=192.168.1.101

Make and Model: HP PhotoSmart C6100 Foomatic/hpijs (recommended) - HPLIP 1.7.1
Device URI: hp:/net/Photosmart_C6100_series?ip=192.168.1.101

And that FIXED IT!

---

### Post by armware on 2007-04-13
using kubuntu 6.10...

i had to reinstall cupsys and add an entry for it in the hosts file, then the add printer wizard in the system settings dialog worked for me perfectly.

---

