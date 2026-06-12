---
title: "packages for ubuntu 6.10"
date: 2007-01-23
forum: General Help
---

### Post by saikumar_divvela on 2007-01-23
Hi ,

I am a newbie to installing linux.
I have installed ubuntu 6.10 on my sata disk after many unsuccessful attempts with debian.
I want to compile a driver for network card. It requires some files like make gcc etc. But the files /usr/bin/make /usr/bin/gcc etc are missing and the directory /usr/src is also empty.
Where can i get these files. Does one package contain all these files or tools. 
Kindly help me.

Thanks,
Sai

---

### Post by mexlinux on 2007-01-23
Install build-essential package

---

### Post by mayonaise15 on 2007-01-24
Just to be a little more specific:

Open up your terminal by clicking "Applications" then "Accessories" then "Terminal"

then type this in:

```
sudo apt-get install build-essential
```

Sorry if that was redundant.

---

