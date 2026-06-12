---
title: "wine problem"
date: 2008-05-18
forum: General Help
---

### Post by pisio on 2008-05-18
I can't  start  mediacoder  to convert avi to mp4.
```
pisio@gaara:~$ sudo env WINEPREFIX="/home/pisio/.wine" wine "C:\Program Files\MediaCoder PSP Edition\mediacoder.exe"
wine: /home/pisio/.wine is not owned by you
pisio@gaara:~$  env WINEPREFIX="/home/pisio/.wine" wine "C:\Program Files\MediaCoder PSP Edition\mediacoder.exe"
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
Trying to load PE image for unsupported architecture (AMD-64)
preloader: Warning: failed to reserve range 00000000-60000000
Trying to load PE image for unsupported architecture (AMD-64)
wine: could not load L"C:\\Program Files\\MediaCoder PSP Edition\\mediacoder.exe": Bad EXE format for 
pisio@gaara:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
pisio@gaara:~$
```

---

### Post by damis648 on 2008-05-18
WOW i JUST had this problem... just run
```
sudo sysctl -w vm.mmap_min_addr=0
```
in terminal and you should be good to go ;)!

---

### Post by pisio on 2008-05-18
10x->Ubuntuforums->Rulz();
:popcorn::KS

---

### Post by damis648 on 2008-05-18
:popcorn::popcorn::popcorn::popcorn::popcorn:

---

