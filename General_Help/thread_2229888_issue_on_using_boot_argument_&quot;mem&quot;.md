---
title: "issue on using boot argument &quot;mem&quot;"
date: 2014-06-15
forum: General Help
---

### Post by watson3 on 2014-06-15
My system has 5G DDR. I tried to use different boot argument value of “mem” and then use "cat /proc/meminfo" to check the available memory in the system. I get the following.
 
mem = 2G -> TotalMem = 2063392kB
mem = 2500M -> TotalMem = 2521720kB
mem = 3G ->TotalMem = 3100552kB
mem = 3500M ->TotalMem = 3100552kB
mem = 4500M ->TotalMem = 3499968kB
mem = 5G ->TotalMem = 4128648kB
 
When the value is set to a value above 3G, the total memory shown by system doesn't match with it. What's wrong?

PS: I'm testing on Ubuntu 12.04 LTS x32

watson

---

### Post by brantcgardner on 2014-06-16
I would check to see if your graphics card is a shared-memory type card that is potentially 'stealing' system memory for its own use.

Also (and I think modern images do this by default, but this is worth checking) you need a PAE kernel for a 32-bit image to access memory above 4GiB.  I'd use a 64-bit image, if your system supports it.

---

### Post by mörgæs on 2014-06-16
The PAE kernel is indeed default now.

---

### Post by oldos2er on 2014-06-16
Moved to General Help.

---

