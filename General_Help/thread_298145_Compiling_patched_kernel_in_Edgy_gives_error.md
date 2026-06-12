---
title: "Compiling patched kernel in Edgy gives error"
date: 2006-11-12
forum: General Help
---

### Post by simoncullen on 2006-11-12
Dear Ubutuers,

I have been trying to patch my kernel to undervolt my Core 2 Duo, according to this howto: [https://wiki.ubuntu.com/UndervoltingHowto]("https://wiki.ubuntu.com/UndervoltingHowto")

Everything runs smoothly until I get to the step where I build the new package:

```
$ AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic
```

It compiles swimmingly for a few minutes, and then spits out this error:

```
-2.6.17/debian/linux-headers-2.6.17-10-0fb/usr/src/linux-headers-2.6.17-10-0fb/./usr/Kconfig not created: newer or same age version exists
cpio: /home/simon/undervolt/linux-source-2.6.17-2.6.17/debian/build/linux-source-2.6.17/debian/linux-headers-2.6.17-10-0fb/usr/src/linux-headers-2.6.17-10-0fb/./usr/Makefile not created: newer or same age version exists
cpio: /home/simon/undervolt/linux-source-2.6.17-2.6.17/debian/build/linux-source-2.6.17/debian/linux-headers-2.6.17-10-0fb/usr/src/linux-headers-2.6.17-10-0fb/arch/i386/kernel/asm-offsets.s not created: newer or same age version exists
28 blocks
dpkg-gencontrol -isp -DArchitecture=i386 -plinux-headers-2.6.17-10-0fb \
                                          -P/home/simon/undervolt/linux-source-2.6.17-2.6.17/debian/build/linux-source-2.6.17/debian/linux-headers-2.6.17-10-0fb/
dpkg-gencontrol: error: package linux-headers-2.6.17-10-0fb not in control info
make[2]: *** [debian/linux-headers-2.6.17-10-0fb] Error 255
make[2]: Leaving directory `/home/simon/undervolt/linux-source-2.6.17-2.6.17/debian/build/linux-source-2.6.17'
make[1]: *** [binary/linux-headers-2.6.17-10-0fb] Error 2
make[1]: Leaving directory `/home/simon/undervolt/linux-source-2.6.17-2.6.17/debian/build/linux-source-2.6.17'
make: *** [binary-debs] Error 2
simon@ahimsa:~/undervolt/linux-source-2.6.17-2.6.17$ 
```



I have updated my system completely, reinstalled the kernel-headers, etc., all to no avail.  I will be infinitely appreciative if anyone could help!

Thanks!
Simon

---

### Post by simoncullen on 2006-11-13
Bump!  (Ouch!)

---

### Post by Kateikyoushi on 2006-11-16
Same problem here, I guess I have to config it myself.

---

### Post by simoncullen on 2006-11-18
> **Kateikyoushi said:**
> Same problem here, I guess I have to config it myself.

Could you explain how to do that?

---

