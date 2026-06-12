---
title: "I want to put all my personal data on it's own Partition"
date: 2008-05-14
forum: General Help
---

### Post by Ioky on 2008-05-14
Sence Ubuntu is great, and I don't need to reinstall it as many as I did in like Windows. and I will only reinstall when it is time to install to install the next version of the OS. 

I would like to have a pratition that only use to store my personal File and Data, like my HTML code of my site, my photo, picture, and etc. 

I wonder What will a good local to mount such Pratition? and how I can address to the pratition from my Desktop

like /home/PersonalData or something like that 


Thanks

---

### Post by Oldsoldier2003 on 2008-05-14
> **Ioky said:**
> Sence Ubuntu is great, and I don't need to reinstall it as many as I did in like Windows. and I will only reinstall when it is time to install to install the next version of the OS. 

I would like to have a pratition that only use to store my personal File and Data, like my HTML code of my site, my photo, picture, and etc. 

I wonder What will a good local to mount such Pratition? and how I can address to the pratition from my Desktop

like /home/PersonalData or something like that 


Thanks

I have a data partition that i mount in my fstab.
```
UUID=eeb6cdb7-d438-45c3-ae97-5de120f3bda6 /mnt/data       ext3    nodev,nosuid 
``` Then I link a folder in my home to the partition. i access the data through /home/me/data ...

---

### Post by macaholic on 2008-05-14
> **Oldsoldier2003 said:**
> I have a data partition that i mount in my fstab.
```
UUID=eeb6cdb7-d438-45c3-ae97-5de120f3bda6 /mnt/data       ext3    nodev,nosuid 
``` Then I link a folder in my home to the partition. i access the data through /home/me/data ...
Just curious, couldn't you also mount it say as ~/personal_data/ right from fstab? As long as there is a directory there that it can mount to.

---

### Post by Oldsoldier2003 on 2008-05-14
> **macaholic said:**
> Just curious, couldn't you also mount it say as ~/personal_data/ right from fstab? As long as there is a directory there that it can mount to.

yes you sure can. I didn't go into great detail as to why i do it this way, but the data partion is further broken down into private userspace folders so i only mount the main partition and then use symlinks as appropriate.

---

### Post by macaholic on 2008-05-14
> **Oldsoldier2003 said:**
> yes you sure can. I didn't go into great detail as to why i do it this way, but the data partion is further broken down into private userspace folders so i only mount the main partition and then use symlinks as appropriate.
Good to know, I just wanted to make sure this works as I have suggested as a solution before, wanted to make sure I wasn't a perpetrator of fallacy.

---

