---
title: "Basic Wubi question"
date: 2008-05-30
forum: General Help
---

### Post by dph948 on 2008-05-30
I'm likely to use Wubi when I get my new laptop sometime over the summer, and I've done a bit of research online, but I still have one basic question, that perhaps I didn't understand from my readings, or perhaps I missed entirely.

If I was partitioning my hard drive, I'd allocate a fixed amount of space (say 20 or 40 GB) for Ubuntu, and use the rest for Vista.  If I use Wubi, do I still do this, or does Wubi take space as needed (perhaps starting out with  5-6 GB and expanding as I added more files to it)?

Thanks for your help,
dph948

---

### Post by avtolle on 2008-05-30
> **dph948 said:**
> I'm likely to use Wubi when I get my new laptop sometime over the summer, and I've done a bit of research online, but I still have one basic question, that perhaps I didn't understand from my readings, or perhaps I missed entirely.

If I was partitioning my hard drive, I'd allocate a fixed amount of space (say 20 or 40 GB) for Ubuntu, and use the rest for Vista.  If I use Wubi, do I still do this, or does Wubi take space as needed (perhaps starting out with  5-6 GB and expanding as I added more files to it)?


Thanks for your help,
dph948
Wubi creates a "virtual disk" within the Vista partition. During the installation process, you may choose how large to make this for Ubuntu (as I recall, I elected to go 15 gigs). You will need to choose the size you will want at that time. There is no need to partition the HDD if installing via Wubi. Should you determine to install permanently, then you would repartition your HDD as you suggest, and install Ubuntu to the partition you have created for it. Wubi does not take additional space as needed, thus the need to choose wisely when first installing.

---

