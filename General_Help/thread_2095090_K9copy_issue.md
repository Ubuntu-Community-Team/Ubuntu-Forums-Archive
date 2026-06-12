---
title: "K9copy issue"
date: 2012-12-15
forum: General Help
---

### Post by taunnt on 2012-12-15
Hello, I'm tring to rip a dvd to avi with K9copy. I can copy the files from the dvd to my hard drive with no issue, but if I try to encode it a window opens for a second then says copying complete. I tried changing the codec from xvid to divx and it does the same thing. mencoder is installed, sp I don't know what the issue might be. What should I try to fix it?

Thanks

---

### Post by superdaveozzborn on 2012-12-15
did you[SIZE=2] Activate Support for Encrypted DVDs[/SIZE]

64-bit
```
$ wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
$ sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
```32-bit
```
$ wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
$ sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
```

---

### Post by taunnt on 2012-12-16
Boom! That was it, it's fixed now.

Thanks.

> **superdaveozzborn said:**
> did you[SIZE=2] Activate Support for Encrypted DVDs[/SIZE]

64-bit
```
$ wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
$ sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb
```32-bit
```
$ wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
$ sudo dpkg -i libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
```

---

### Post by superdaveozzborn on 2012-12-16
You Are Welcome. :popcorn:

---

