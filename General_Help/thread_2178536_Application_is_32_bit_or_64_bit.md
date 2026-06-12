---
title: "Application is 32 bit or 64 bit"
date: 2013-10-03
forum: General Help
---

### Post by sreejithmylachal on 2013-10-03
Hi,

    How to check ( command for it) an application installed in Ubuntu 12.04  is 32 bit application or 64 bit application. I need to check PostgreSQL  which is already got installed there in Ubuntu 12.04. Please provide Linux command to check whether this PostgreSQL  is 32 bit or 64 bit.

---

### Post by wojox on 2013-10-03
*apt-cache* will show you package information. Then pipe it to grep to get the Arch.
```
sudo apt-cache show postgresql | grep Architecture
```

---

### Post by deadflowr on 2013-10-04
> **wojox said:**
> *apt-cache* will show you package information. Then pipe it to grep to get the Arch.
```
sudo apt-cache show postgresql | grep Architecture
```

Do you need to sudo to run apt-cache?

---

### Post by wojox on 2013-10-04
> **deadflowr said:**
> Do you need to sudo to run apt-cache?

No just a habit of my apt skills to add sudo.

---

### Post by sanderj on 2013-10-04
> **sreejithmylachal said:**
> Hi,

    How to check ( command for it) an application installed in Ubuntu 12.04  is 32 bit application or 64 bit application. I need to check PostgreSQL  which is already got installed there in Ubuntu 12.04. Please provide Linux command to check whether this PostgreSQL  is 32 bit or 64 bit.

You can run 'file' against the binary to see what it is. For example

```
sander@flappie:~$ file /usr/lib/chromium-browser/chromium-browser
/usr/lib/chromium-browser/chromium-browser: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x47a4b12a46cb7121f88413d51598f58b568cd042, stripped
sander@flappie:~$ 
```

So my chromium-browser is ... 64-bit

---

