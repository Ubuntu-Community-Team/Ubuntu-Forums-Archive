---
title: "NetBeans Bundle Error Install"
date: 2005-08-18
forum: General Help
---

### Post by amodena on 2005-08-18
Hi, i'm newbie to ubuntu and i try to move from windows...
i've problem to install netbeans 4.1 bundled with SunAppServer8.1 PE...i searcing in this forum and in other place, but dont found nothing for boundle...
i install j2sdk 1.5, copy the sjsas_pe-8_1_02_2005Q2-nb-4_1-linux.bin into my home and call install -v sjsas_pe-8_1_02_2005Q2-nb-4_1-linux.bin netbeans4_1 ... starting the install phase and at the end of this i try to run netbeans...it's work fine...but i don't find where is SunAppServer8.1 and PointBase...i look the install log and read this:

Command Error:
/home/amodena/netbeans-4.1/_uninst/sjsas_pe-8_1_02_2005Q2-fcs-bin-b06-linux-13_may_2005.bin: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

and other errors all referred to the libstdc++-libc6.2-2.so.3....

i open synaptic and find my install version: libc6 version 2.3.2.ds1-22

any idea to solve this problem? or other way to install SunAppServer8.1 and PointBase for use in Netbeans 4.1?

Thanks in advance
Alessio

---

### Post by amodena on 2005-08-18
solved...
simply create a link from my lib and requested lib...

cd /usr/lib
sudo ln -s libstdc++.so.6.0.4 libstdc++-libc6.2-2.so.3
sudo ldconfig -v

...now works... :razz:

---

### Post by SkyScrap on 2006-01-21
Hi,

thanks for mentioning and also solving the problem. I don't know what the root source is - is it netbeans' or ubuntu's fault for example - but I will try your workaround now.

Thanks,
Sky

---

### Post by SkyScrap on 2006-01-21
I don't know what I'm doing wrong, but ldconfig seems to remove that link:

```

andreas@ebbipc:/usr/lib$ sudo ls -l  libstdc++-libc6.2-2.so.3
ls: libstdc++-libc6.2-2.so.3: Datei oder Verzeichnis nicht gefunden
andreas@ebbipc:/usr/lib$ sudo ln -s libstdc++.so.6.0.4 libstdc++-libc6.2-2.so.3
andreas@ebbipc:/usr/lib$ sudo ls -l  libstdc++-libc6.2-2.so.3
lrwxrwxrwx  1 root root 18 2006-01-21 11:57 libstdc++-libc6.2-2.so.3 -> libstdc++.so.6.0.4
andreas@ebbipc:/usr/lib$ sudo ldconfig
andreas@ebbipc:/usr/lib$ sudo ls -l  libstdc++-libc6.2-2.so.3
ls: libstdc++-libc6.2-2.so.3: Datei oder Verzeichnis nicht gefunden

```

---

### Post by SkyScrap on 2006-01-21
I had to use libstdc++.so.6.0.5 to make it working #-o :oops:

---

