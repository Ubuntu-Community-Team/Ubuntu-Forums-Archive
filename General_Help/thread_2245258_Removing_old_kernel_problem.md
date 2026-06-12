---
title: "Removing old kernel problem"
date: 2014-09-22
forum: General Help
---

### Post by Jarmo_Uusi-Maahi on 2014-09-22
Hi,
I tried to remove old kernel packages in the same way that I did before...

```
sudo apt-get autoremove linux-image-3.13.0-24-generic
```

But now system apt-get wants remove all these packages...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firefox-locale-fi libgstreamer-plugins-base0.10-0:i386
  libgstreamer0.10-0:i386 libqt5declarative5 libssl0.9.8
  linux-image-3.13.0-24-generic linux-image-3.13.0-27-generic
  linux-image-3.13.0-29-generic linux-image-3.13.0-30-generic
  linux-image-3.13.0-32-generic linux-image-3.13.0-33-generic
  linux-image-extra-3.13.0-24-generic linux-image-extra-3.13.0-27-generic
  linux-image-extra-3.13.0-29-generic linux-image-extra-3.13.0-30-generic
  linux-image-extra-3.13.0-32-generic linux-image-extra-3.13.0-33-generic
0 upgraded, 0 newly installed, 17 to remove and 0 not upgraded.
After this operation, 1 172 MB disk space will be freed.
Do you want to continue? [Y/n]

Is this ok, or is there possible something wrong with the package database? Is it safe to proceed?

--Jarmo--

---

### Post by mörgæs on 2014-09-22
Hi, welcome to the fora.

Best you can do is 
```
sudo apt-get update
sudo apt-get autoremove
```

and let the system decide from here.

---

### Post by Jarmo_Uusi-Maahi on 2014-09-22
Ok, thanks. I'll try that.

> **mörgæs said:**
> Hi, welcome to the fora.

Best you can do is 
```
sudo apt-get update
sudo apt-get autoremove
```

and let the system decide from here.

---

