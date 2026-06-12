---
title: "Installer doesnt detects my partitions"
date: 2006-08-24
forum: General Help
---

### Post by smb on 2006-08-24
When i try to install Ubuntu Linux on my computer it doesnt detects my partitions and shows me wrong size of my hdd(about 30 gigabytes instead of 120). This happens when I boot from cd changing first boot device to cd-rom in bios, but when I boot from cd pressing <C> while Seagate Dynamic Drive Overlay(it was installed when i used Seagates DiscWizard for formatting my hdd) loading, Linux shows me the wright size of my hdd, but still no partitions found. On my second hdd there was analogical problem, but it disappeared after reformatting the hdd. I use DiscWizard for setting up hdds.
P.S. I tried to install Ubuntu 6.06 and 5.10, but its no difference.

---

### Post by John.Michael.Kane on 2006-08-24
You can try the [**gparted.livecd**]("http://gparted.sourceforge.net/livecd.php").it should allow you to size the partitions as you feel fit,and allow the install cd to see them.

---

### Post by Ocxic on 2006-08-25
ok don't use disc wizard, the ubuntu installer can do eveything for you, or you can mannually setup you drives and paritions. sound like the dynamic drive overlay thing is messing stuff up, if you not concerned with losin data, then i suggest using a fdisk to erase the partion table and start fresh.

---

### Post by smb on 2006-08-25
I start to understand why there is such problem :) There is a jumper on my hdd that limits its size to 33.8 gb, because old bioses cant work with bigger hdds, and this Seagates Dynamic Drive Overlay loads after bios and expands my hdd to its real size ([http://www.seagate.com/support/kb/disc/capacity/32_338/index.html)](http://www.seagate.com/support/kb/disc/capacity/32_338/index.html)).
But when I install Ubuntu, this utility disappeares, and GRUB writes me error 17(maybe because this utility didnt loaded and didnt expanded my hdd?).

---

### Post by Ocxic on 2006-08-26
ok remove that jumper so it doesn't limit your drive size, you shouldn't need it, then try to install.

---

