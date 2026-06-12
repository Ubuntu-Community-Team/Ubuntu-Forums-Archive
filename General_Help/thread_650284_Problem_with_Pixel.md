---
title: "Problem with Pixel"
date: 2007-12-26
forum: General Help
---

### Post by Angelbeast on 2007-12-26
I have installed Pixel Image Editor to try it out and i want to uninstall it. But i don't see it listed in the package manager in the locally installed section How do i uninstall this?

---

### Post by nick_h on 2007-12-26
How did you install it?

---

### Post by Angelbeast on 2007-12-26
> **nick_h said:**
> How did you install it?

With the .deb package from he Pixel web site

---

### Post by nick_h on 2007-12-26
You can find the package name using:
```
dpkg --info package_file.deb
```
Then you can remove it using:
```
sudo dpkg --remove package_name
```

---

### Post by Angelbeast on 2007-12-26
> **nick_h said:**
> You can find the package name using:
```
dpkg --info package_file.deb
```
Then you can remove it using:
```
sudo dpkg --remove package_name
```

Oops...Well i guess i lied...It was an automatic installer that was in a tar.gz file...

---

### Post by nick_h on 2007-12-26
If it was a tar.gz file then it will not use the package management system.  You will either have to remove the files manually or maybe an uninstall utility was provided.

---

### Post by flapane on 2008-01-23
I tried installing the last deb on ubuntu 6.10 but it gives issues with dependencies... how to solve?

Spacchetto pixeldemo (da pixeldemo_1.0.699-1_i386.deb) ...
dpkg: problemi con le dipendenze impediscono la configurazione di pixeldemo:
 pixeldemo dipende da libc6 (>= 2.6-1); comunque:
  La versione di libc6 sul sistema Ã¨ 2.4-1ubuntu12.3.
 pixeldemo dipende da libfreetype6 (>= 2.3.5); comunque:
  La versione di libfreetype6 sul sistema Ã¨ 2.2.1-5ubuntu0.2.
 pixeldemo dipende da libpng12-0 (>= 1.2.13-4); comunque:
  La versione di libpng12-0 sul sistema Ã¨ 1.2.8rel-5.1ubuntu0.3.
 pixeldemo dipende da zlib1g (>= 1:1.2.3.3.dfsg-1); comunque:
  La versione di zlib1g sul sistema Ã¨ 1:1.2.3-13ubuntu2.
dpkg: errore processando pixeldemo (--install):
 problemi con le dipendenze - lasciato non configurato
Sono occorsi degli errori processando:
 pixeldemo

---

