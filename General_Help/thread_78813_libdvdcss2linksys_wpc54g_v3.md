---
title: "libdvdcss2/linksys wpc54g v3"
date: 2005-10-19
forum: General Help
---

### Post by Llewxam on 2005-10-19
i try installing this and i keep getting this error:

libdvdcss2:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed

can anyone tell me how to update/substitute this? 

also i just got the linksys wpc54g v3 notebook adapter card. it shows up in my hardware settings but i can't configure it. 

any help will be greatly appreciated. this is all i need to have a full working system -.-

---

### Post by aclaunch on 2005-10-19
You can start to configure your wireles card via the System->Admin=>Networking tab. Is the interface shown? If yes, configure your card; if no, google for the name of the chipset (may be atheros, atmel or another) and report back.

Have you done an apt-get update before trying to install libdvdcss2?

Good Luck
Alan

---

### Post by Llewxam on 2005-10-19
yes i tried. what i need to change is libc6. that is my only problem. as for my wireless card it's recognized in the device manager but not in network settings.

---

