---
title: "Can i remove these (files taking up space)"
date: 2008-06-30
forum: General Help
---

### Post by wbutchart on 2008-06-30
Hi i have noticed that since running a upgrade file i have lost a lot of space.  I ran the disk usage analyser and it shows that a lot of it is being used in var>cache>apt>archives.

Am i able to delete the files in the archives folder? they appear to be install files, i was thinking the may be left over from the system update?.

Didnt want to do anything until i checked.

Thanks :D

---

### Post by avtolle on 2008-06-30
Try from terminal```
sudo apt-get clean
```and ```
sudo apt-get autoclean
```

---

### Post by sisco311 on 2008-06-30
Use```
sudo aptitude clean
```to remove the files from /var/chace/apt/archives

man aptitude:
> clean
           Removes all previously downloaded files from the package cache directory (usually /var/cache/apt/archives).


---

