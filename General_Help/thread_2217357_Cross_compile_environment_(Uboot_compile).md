---
title: "Cross compile environment (Uboot compile)"
date: 2014-04-16
forum: General Help
---

### Post by adcuevas on 2014-04-16
Hello,

I 've been trying to compile uboot. but I get this error:
make[1]: *** No rule to make target `/usr/lib/gcc/i486-linux-gnu/4.4.3/include/stddef.h', needed by `img2srec.o'.  Stop.

it seems to ve a problem with he environment settings (lib should be from /usr/arm-linux-gnueabi/include/linux/stddef.h instead of the other path) but i cannot get it to work.

any advice will be highly appreciated

---

### Post by HermanAB on 2014-04-17
Howdy,

You need to make a QEMU ARM VM and compile natively in ARM code.

So, install QEMU and go from there.

---

### Post by adcuevas on 2014-04-17
Thank you for the information but i actually want to compile the uboot. As far as i understand qemu will run aemulated environment for arm processor.

soni only need to specify the lib path while using make command to complete the compilation

---

### Post by steeldriver on 2014-04-17
Not sure I can help but you should probably mention (1) which specific ARM toolchain you are using and (2) what is the target device

---

