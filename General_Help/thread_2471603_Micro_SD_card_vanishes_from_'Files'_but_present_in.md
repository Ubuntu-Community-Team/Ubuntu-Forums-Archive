---
title: "Micro SD card vanishes from 'Files' but present in 'Disks'"
date: 2022-02-03
forum: General Help
---

### Post by tapasray on 2022-02-03
I had formatted a 32 GB micro SD card in Ubuntu, choosing 'Compatible with all systems and devices (MBR / DOS)'. It has since vanished from 'Files' - both from the list of drives in the left side bar and from the list in Computer > User > Media. Screenshot attached.

Please help!

---

### Post by Impavidus on 2022-02-04
It says the sd card uses MBR partitioning and is full of unallocated space. Unallocated means that it's not assigned to any partition or filesystem. So it looks like you only created a new partition table, but not a new filesystem. Without a filesystem, it cannot be mounted and the file manager won't show it. And of course no files can be stored on it.

So create a partition and a filesystem in that partition. If you want it to work with everything (Linux, Windows, phones, cameras, ...), you can use exFAT. On small drives (I think 32GB is still small) FAT32 is another option. To use it on just Ubuntu and Windows, or only Ubuntu, there are other (better) options.

---

### Post by tapasray on 2022-02-04
Thank you so much, @Impavidus!

---

### Post by tapasray on 2022-02-04
> **Impavidus said:**
> ... you can use exFAT. On small drives (I think 32GB is still small) FAT32 is another option ... 

Hi! Thanks again. 
I have created a filesystem, and it seems to have defaulted to FAT. Now I am trying to format it as exFAT, but am stuck as exFAT and most other options are greyed-out. Please see the screenshot.

---

