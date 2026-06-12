---
title: "Package removal failed! Help please"
date: 2015-04-26
forum: General Help
---

### Post by QuietSwami on 2015-04-26
I was trying to install steam, and the installation failed because I was missing some i386 libs. So I searched google trying to find a solution and I came up to this command 
```
sudo apt-get install libc-bin:i386
```,
And since then I was not able to install or remove any packages, can any one please help??
Thank You!!

---

### Post by matt_symes on 2015-04-26
Hi

Open up a terminal and copy and paste this into it. It will update the package cache.

```
sudo apt-get update
```

Post any errors back here. 

Only if the above command completes successfully, type

```
sudo apt-get install htop
```

Again post back any errors.

Kind regards

---

