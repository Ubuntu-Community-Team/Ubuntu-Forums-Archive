---
title: "Is it possible to install RPMs without alien?"
date: 2007-06-17
forum: General Help
---

### Post by woland on 2007-06-17
Hi, I wanted to ask if it is possible, in some way, to install an RPM package if alien fails to convert the package?
I mean, without the use of alien?

---

### Post by markharding557 on 2007-06-17
dont think so best to use debs or an installer script if you can

---

### Post by NilsE on 2007-06-17
> **woland said:**
> Hi, I wanted to ask if it is possible, in some way, to install an RPM package if alien fails to convert the package?
I mean, without the use of alien?

If Alien fails to convert it then the rpm is more than likely corrupt or is simply not compatible with Ubuntu.  

I am not aware of any other way to install rpm's without Alien so I would suggest trying to download the package again and try it with Alien. You might even consider searching for the rpm on another site.

---

### Post by woland on 2007-06-18
Unfortunately the packages are specific to a certain hardware, so I can't download them from any other location. Also they are available in rpm packaging only, so I'm stuck.

Alien exits with the following error message: ```
cp:  Cannot overwrite directory xxx with a non-directory
```
Therefore I don't think it has a compatibility issues with Ubuntu, or Debian, which has similar issues.

Thanks for your answers!

---

### Post by Kodfish on 2007-06-18
Can you find the source? That should be simple to install if the RPM fails to convert.

---

