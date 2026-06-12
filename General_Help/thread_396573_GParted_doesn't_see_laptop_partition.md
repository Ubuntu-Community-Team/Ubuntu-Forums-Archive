---
title: "GParted doesn't see laptop partition"
date: 2007-03-29
forum: General Help
---

### Post by PaulFXH on 2007-03-29
I have installed a dual boot system (Windows XP and Ubuntu) a number of times before on desktops. Always without any problems.
Now I'm trying the exact same thing on a laptop (HP pavilion dv 1000, CPU 1.46 GHz, 512 MB RAM, 60GB HDD).
As a first step, I tried to use GParted 3.4.5 to reduce the Windows partition from 50GB to 30GB and then create a 20GB extended partition into which I wished to create 3 logical partitions to receive the Ubuntu root, home and swap.
However, even though GParted repórted seeing media in /dev/hda/ while it was booting, when I got to operate GParted it reported that no devices were detected.
I presume that this means that it wasn't seeing the HDD that I intended to partition.
Anybody know what's up with this?
Thanks
Paul

---

### Post by zvacet on 2007-03-29
I don´t know,maybe try Gparted Live CD?

---

### Post by PaulFXH on 2007-03-29
Thanks, but I am using the Live CD.
I'm not sure if my problem is because I'm using a newer version of GParted than I had used before. Could it be that there's something I'm forgetting?

---

### Post by equability on 2007-03-30
Hi Paul.

Try to use another LiveCD, e.g. Knoppix.

---

### Post by PaulFXH on 2007-03-30
Thanks but you lost me with that suggestion.
Why will using the Knoppix Live CD allow a partitioner to more easily "see" my HDDs?

---

### Post by PaulFXH on 2007-03-30
Just bringing this investigation a little further:
As GParted 0.3.4.5 (Live CD) failed to see my HDD on this laptop, I tried an earlier version of GParted (0.3.1).
However, this similarly reported "no devices" when it should have been showing me my HDD with its two partitions (50 GB for WinXP and about 8GB for the HP recovery system).
While GParted was booting, it mentioned that /dev/hda/ was "write protected". This is interesting as it certainly is not write protected when WinXP is running.
Can anybody suggest what I might try next?
Thanks
Paul

---

### Post by Zymonick on 2008-05-08
Hi,

it is about a year later and I have exactly the same problem. Gparted does not recognize my partitions.

The weird thing is that Ubuntu started from the LiveCD can see my Windows partitions and even mounts them automatically correct. 

I was using gparted as it is on the most recent Ubuntu LiveCV and I got a Laptop from Packard Bell. 

Thanks for any suggestions,
Zymonick

---

