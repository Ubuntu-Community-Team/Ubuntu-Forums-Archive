---
title: "Hard Drive is Not Usable in Windows"
date: 2007-11-08
forum: General Help
---

### Post by Prefectionist on 2007-11-08
I was (admittedly) messing around with my hard drives, trying out different layouts for a dual boot system with Windows Vista (blegh) and Ubuntu 7.10. I have two 320GB hard drives, and was using Vista's partitioning manager, and I selected "delete volume" for the second hd (so I could install Ubuntu) after moving everything important to the main hd. Ubuntu wasn't booting properly, so I used "delete partition" on the second hd again (to get rid of Ubuntu), and found that I could not access the hd in Vista. It does not show up in "My Computer," and in disk manager it displays as, of course, "Unallocated Space."
I have since restored my computer to factory settings, but the second hd remains unallocated space.

Is there any way I can fix this?

(Please note that I am absolutely new to most of this. I only found Ubuntu and discovered the possibility of dual-booting around a month ago. So, yeah, it probably wasn't a good idea to mess around.)

---

### Post by Prefectionist on 2007-11-08
Yes I did, several times without problem. It being on my second hd just ended up being not what I wanted, so I'm certain that there is nothing wrong with the LiveCD...

---

### Post by dcstar on 2007-11-08
> **Prefectionist said:**
> I was (admittedly) messing around with my hard drives, trying out different layouts for a dual boot system with Windows Vista (blegh) and Ubuntu 7.10. I have two 320GB hard drives, and was using Vista's partitioning manager, and I selected "delete volume" for the second hd (so I could install Ubuntu) after moving everything important to the main hd. Ubuntu wasn't booting properly, **so I used "delete partition" on the second hd again** (to get rid of Ubuntu), and found that I could not access the hd in Vista. It does not show up in "My Computer," and in disk manager it displays as, of course, "Unallocated Space."
I have since restored my computer to factory settings, but the second hd remains unallocated space.

Is there any way I can fix this?

(Please note that I am absolutely new to most of this. I only found Ubuntu and discovered the possibility of dual-booting around a month ago. So, yeah, it probably wasn't a good idea to mess around.)

It will remain "Unallocated Space" until you create a partition that Windows can work with and format it (Windows does NOT access EXT2/3 Linux partitions).

Install the **gparted** package and use that to set it up, or boot windows and use that to format the drive.

---

### Post by Prefectionist on 2007-11-08
Ah, thanks dcstar... I'll format in Windows. I hadn't been sure what the option meant exactly, and wasn't particularly inclined on tempting fate...
It's looking like everything is going to be working properly soon.
Thanks again!

---

