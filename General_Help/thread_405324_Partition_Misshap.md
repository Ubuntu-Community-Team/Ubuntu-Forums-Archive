---
title: "Partition Misshap"
date: 2007-04-09
forum: General Help
---

### Post by CadMasterAdam on 2007-04-09
so i got vista and ubuntu working just fine. 

issue: the ubuntu partition is about 250gigs. but i want it to be like 80

and my vista is about 80 and i want that to be 250. 

question:

can i use the vista partition editor to safely take space from the ubuntu partition and give it to the vista partition? if i loose ubuntu thats okay!

---

### Post by strabes on 2007-04-09
I don't know about vista's partition editor but just use a gparted live CD to resize both: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

You could also create a data vfat or ntfs partition on which you could put all of your data that you want to share between windows and linux. It's really convenient.

---

