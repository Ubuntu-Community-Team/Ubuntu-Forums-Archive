---
title: "Answer Quick!!!"
date: 2007-04-20
forum: General Help
---

### Post by GuitarRocker2562 on 2007-04-20
I am about to re-install feisty (from beta to final, I don't wanna upgrade). I want to re partition my system and I want a root partition and a home partition. I have a few questions.

1.I have 50 GB for linux, and I want my Swap 1GB, how much should root be, will 10GB be enough, can I do less?

2. Can I put my root, home and swap partitions on an extended partition, or will GRUB not work?

3. If my root partition has to be a physical partition, can my home and swap be on an extended one?

Answer quick!

---

### Post by mahlib on 2007-04-20
1. 10GB should be more than enough for a normal install. Some people prefer to have more packages, so that would require more space. Technically, you can go lower than 10 (ie. my current install is at 4GB), but 10 sounds fine to me.

2. All of those partitions can be on an extended partition.

3. Yes.

---

### Post by GuitarRocker2562 on 2007-04-20
Thanks, and I have lots of programs and I love installing them to the right folders, yay "sudo chown <username> /..."

---

### Post by GuitarRocker2562 on 2007-04-21
I got GRUB error 17, and I had to recover windows and my partitions are gone! Is this error because my root partition was on an extended partition?

---

### Post by GuitarRocker2562 on 2007-04-21
bump

---

### Post by zvacet on 2007-04-21
[http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

