---
title: "HELP:successfully mounted my windows partition but only read no write!"
date: 2006-12-13
forum: General Help
---

### Post by abh83 on 2006-12-13
I've successfully managed to mount my windows ntfs partition but it seems I've missed something out because i can only copy off it (read) but NOT paste (as in no writing permission)?!?

I'm trying to search for the HowTo that i used (to post it here as reference) but i can't seem to find it anymore.

can someone explain in simple newb terms how to go about this problem!?

cheers
ABH

---

### Post by snigri on 2006-12-13
Linux write support in NTFS partitions is in experimental stage.

Please see:

[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntsf+%2Bwrite](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntsf+%2Bwrite)

for details.

---

### Post by taurus on 2006-12-13
If you want to write to ntfs, you need to install ntfs-3g...

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by meng on 2006-12-13
This is the default! NFTS-writing from Linux is still in relatively early stages. But if you insist, then install nfts-3g
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by abh83 on 2006-12-13
thx everyone for the quick responce! I think i'd rather wait since NTFS-writing seems rather unstable at this point in time! has anyone actually tested NTFS-wrting?

---

