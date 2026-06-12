---
title: "Strange Problem Ubuntu Slowed down"
date: 2007-02-12
forum: General Help
---

### Post by ambuj123 on 2007-02-12
Hello 
well i had been using  ubuntu 6.10 for over a week now it has been working like a charm however  now i have a  strange problem it seems my swap partition is not being mounted automatically/ not being used automatically by ubuntu  my laptop runs very slow when i boot into ubuntu and have to type sudo swapon /dev/hda5 everytime to mount my swap partition and make ubuntu use it after this ubuntu works perfectly well and  fast ???? so how can i correct this ?? i dont want to type this everytime i start ubuntu ???

and also once while i was installing app it crashed and i feel since then i have been having this problem ??? is it possible ?

Thanx 
bye

---

### Post by dcstar on 2007-02-12
> **ambuj123 said:**
> Hello 
well i had been using  ubuntu 6.10 for over a week now it has been working like a charm however  now i have a  strange problem it seems my swap partition is not being mounted automatically/ not being used automatically by ubuntu  my laptop runs very slow when i boot into ubuntu and have to type sudo swapon /dev/hda5 everytime to mount my swap partition and make ubuntu use it after this ubuntu works perfectly well and  fast ???? so how can i correct this ?? i dont want to type this everytime i start ubuntu ???

and also once while i was installing app it crashed and i feel since then i have been having this problem ??? is it possible ?

Thanx 
bye

You should check your /etc/fstab file to see if the swap partition is listed correctly, and also check the partition table of your disks.

---

