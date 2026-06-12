---
title: "Dual Boot Vista / Ubuntu 7.04"
date: 2008-01-21
forum: General Help
---

### Post by KevMeistr on 2008-01-21
I have recently installed windows vista and need to install ubuntu 7.04...the problem is that when I boot up with ubuntu liveCD, I cannot install ubuntu on the same harddrive as vista as they say I don't have write, or something like that, priveliges...that means, when I'm in the process of installing ubuntu, and get to the part of partitioning the drives, I can see /dev/sda but there is no other information in the partition about this drive...

Help is really appreciated.

---

### Post by Sef on 2008-01-21
Use the partitioner that comes with Vista to shrink it.

---

### Post by KevMeistr on 2008-01-21
> **Sef said:**
> Use the partitioner that comes with Vista to shrink it.
How will that help me in getting permission to install ubuntu on the same drive as vista

---

### Post by KevMeistr on 2008-01-21
Anybody got any ideas on how to gain permissions to install ubuntu on the same drive but different partition as vista.

---

### Post by Sef on 2008-01-21
You will have empty space on the hard disk.   Don't forget to defrag vista first a few times.

---

### Post by KevMeistr on 2008-01-21
Must I shrink the drive for the swap as well or just the drive for the ubuntu base

---

### Post by njparton on 2008-01-21
It sounds like you've only got one hard drive so just free up around 5GB or more of space if you can afford it.  Install ubuntu to that free space.  

How big is the hard drive and how much ram do you have?  This will determine recommended partitioning of ubuntu.  Go for 3 partitions:

swap
/
/home

the size of the ubuntu swap partition will depend on your ram and may be as little as 512MB if you have 2GB+ of ram. Go for 1GB otherwise to be safe. Divide the rest of the space into 1/3 for "/" and 2/3 for "/home".

5GB may be a bit OTT, but it allows for future expansion.

---

### Post by danwood76 on 2008-01-21
> **KevMeistr said:**
> Anybody got any ideas on how to gain permissions to install ubuntu on the same drive but different partition as vista.

At default ubuntu will not modify ntfs partitons I think.
Resize it in vista so you have 8 or 10 GB free then  try to install ubuntu.
And make sure that ubuntu only uses the free space.

regards,
Danny

---

