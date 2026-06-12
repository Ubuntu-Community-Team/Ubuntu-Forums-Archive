---
title: "making debs from rpms"
date: 2006-12-19
forum: General Help
---

### Post by rpm13 on 2006-12-19
There is this rpm source package of canon printer drivers.
I want to do the following chain
rpm -> deb-src -> configure;make -> make deb package
The last part of this chain is described in
 [http://www.debian.org/doc/manuals/maint-guide/index.en.html](http://www.debian.org/doc/manuals/maint-guide/index.en.html)

But is there any help/program for rpm to deb-src

I ran alien on the rpm and got a deb. As far as I know this is not correct

---

### Post by aysiu on 2006-12-19
```
sudo aptitude update
sudo aptitude install alien
sudo alien -i *.rpm
```

---

### Post by rpm13 on 2006-12-19
> **aysiu said:**
> ```
sudo aptitude update
sudo aptitude install alien
sudo alien -i *.rpm
```

The alien -i installs the rpm after debianizing it
But these rpms are source rpms not binaries

What I have done for now is

rpm2cpio cndrvcups-capt-1.30-1.src.rpm > cnd.cpio
cpio -idv < cnd.cpio

This generates a tar file and a spec file
Dont know if I can use the spec file in any way

cded to the directory and ran make

Which gave (as one expects!) pagefulls of errors

---

### Post by PriceChild on 2006-12-19
just don't type the "-i" then.

---

### Post by aysiu on 2006-12-19
I'm not sure, but you may find [this thread](http://ubuntuforums.org/showthread.php?t=77628) helpful.

---

