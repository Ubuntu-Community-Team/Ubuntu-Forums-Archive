---
title: "choppy dvd playback"
date: 2007-05-24
forum: General Help
---

### Post by atlfalcons866 on 2007-05-24
hi
i  am getting choppy dvd playback or choppy video that comes from my dvd drive.

---

### Post by mbradlcu on 2007-05-25
check out 'hdparm', you want to make sure "using_dma = 1", here's my output:

> daturan@matt-x64:~$ hdparm /dev/cdrom 

/dev/cdrom:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)


if it's not using dma then the following will enable it:
```
sudo hdparm -d /dev/cdrom
```

---

