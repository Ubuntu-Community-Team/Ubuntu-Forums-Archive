---
title: "dmraid doesn't work on HPT370"
date: 2007-01-08
forum: General Help
---

### Post by rokafeller on 2007-01-08
Hi all,
my situation is: ubuntu installed on an IDE disk, 3 fat32 partitions on a raid0 array on HTP370 integrated in an abit KG7 raid. My goal: to get access to fat32 partitions from ubuntu. I tried dmraid -ay -v but nothing happens. After running this command /dev/mapper is still empty. If I run dmraid -r I get the correct identification of the raid controller...

can you help me? I'd like to run ubuntu because it's the only distro I tried where I've been able to get my conexant adsl modem work but the only one where I can't see my raid array :(

thanx in advance
d

---

### Post by haydnw on 2007-01-19
I'm having exactly the same problem! I have an nvraid array of two disks in Raid 0, and dmraid just doesn't want to do anything with them. Yet if I do dmraid -s it shows the striped array perfectly. I've been using v6.10 of Ubuntu (Efty Edge?), but now I've decided to slide back down to 6.06 (Dapper?). I'm new to all this but it seems to have been very difficult to get anywhere with loading Ubuntu onto an nvidia raid array. I thought Windows was difficult because of a bug in the nvidia drivers but to be honest, slipstreaming the drivers onto a new XP cd was miles easier than everything I'd tried with Ubuntu so far. Someone please restore my new-found and new-lost interest in Ubunutu!

---

