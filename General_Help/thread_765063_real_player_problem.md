---
title: "real player problem"
date: 2008-04-24
forum: General Help
---

### Post by Benbow on 2008-04-24
I have downloaded realplayer but when I try to install it I get the following result. Any ideas?

benbow@benbow-desktop:~$ chmod 755 RealPlayer10GOLD.bin
benbow@benbow-desktop:~$ ls -l RealPlayer10GOLD.bin
-rwxr-xr-x 1 benbow benbow 5790356 2008-04-24 17:56 RealPlayer10GOLD.bin
benbow@benbow-desktop:~$ sudo ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
benbow@benbow-desktop:~$

---

### Post by markharding557 on 2008-05-05
i would recommend using mplayer instead works for me without issue

---

### Post by retrow on 2008-05-05
Once you are in the correct directory:
```
sudo chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
```

---

