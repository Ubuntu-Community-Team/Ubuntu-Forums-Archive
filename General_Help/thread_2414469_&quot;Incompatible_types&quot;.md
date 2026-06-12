---
title: "&quot;Incompatible types&quot;"
date: 2019-03-11
forum: General Help
---

### Post by butinbutout on 2019-03-11
Hi,

I am installing a program (LINX 2.5.1) and receive three similar error codes to which I find no answer online. Therefore I would appreciate any help! I am running Ubuntu 12.04 with kernel 3.13.x.

I am getting the following errors:

```
root@user-HP-Compaq-Elite-8300-CMT:/home/user/Downloads/linx-2.5.1/net/linx# make# ARCH=x86_64
# KERNEL=/lib/modules/3.13.0-117-generic/build
# VERBOSE=no
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-117-generic'
  CC [M]  /home/user/Downloads/linx-2.5.1/net/linx/af_linx.o
/home/user/Downloads/linx-2.5.1/net/linx/af_linx.c: In function ‘linx_alloc_send_pskb’:
/home/user/Downloads/linx-2.5.1/net/linx/af_linx.c:999:17: error: incompatible types when assigning to type ‘struct <anonymous>’ from type ‘struct page *’
/home/user/Downloads/linx-2.5.1/net/linx/af_linx.c: In function ‘linx_skb_store_bits’:
/home/user/Downloads/linx-2.5.1/net/linx/af_linx.c:1075:4: error: incompatible type for argument 1 of ‘kmap’
include/linux/highmem.h:56:21: note: expected ‘struct page *’ but argument is of type ‘struct <anonymous>’
/home/user/Downloads/linx-2.5.1/net/linx/af_linx.c:1087:4: error: incompatible type for argument 1 of ‘kunmap’
include/linux/highmem.h:62:20: note: expected ‘struct page *’ but argument is of type ‘struct <anonymous>’
make[2]: *** [/home/user/Downloads/linx-2.5.1/net/linx/af_linx.o] Error 1
make[1]: *** [_module_/home/user/Downloads/linx-2.5.1/net/linx] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-117-generic'
make: *** [modules] Error 2



```

Does anybody have experience with such errors?

---

### Post by Autodave on 2019-03-11
I don't.  However, you are running an ancient version of Ubuntu which could (probably is) be your problem.  Time to think about getting 18.04 on that machine.  And I would do a clean install instead of having to try and update through 3 LTS releases.  Make sure that EVERYTHING is backed up before you begin!!

---

### Post by butinbutout on 2019-03-11
> **Autodave said:**
> I don't.  However, you are running an ancient version of Ubuntu which could (probably is) be your problem.  Time to think about getting 18.04 on that machine.  And I would do a clean install instead of having to try and update through 3 LTS releases.  Make sure that EVERYTHING is backed up before you begin!!

[COLOR=#000000]Hi and thanks for the reply,[/COLOR]

[COLOR=#000000]I have tried Ubuntu 16 and 18 for the installation of this program; however after contacting its developer who works at my company, he recommended using Ubuntu 12, since he knows it works on there in combination with Kernel 3.13 :/[/COLOR]

---

### Post by Autodave on 2019-03-11
I understand, but you are running a release that is no longer supported and not safe.  Hopefully, someone else will jump in and give you info for running it successfully and on a newer release.

---

### Post by DuckHook on 2019-03-11
> **butinbutout said:**
> …he recommended using Ubuntu 12, since he knows it works on there in combination with Kernel 3.13…
In which case, he is passing on very irresponsible advice. If he had said, "I recommend using Windows XP as I know that my app works with that OS", would this be acceptable?

If this is a mission critical app that can only run on 12.04, then consider running it in a VM with Precise jailed from the rest of your LAN and certainly completely jailed from the Internet. That is the workaround that I used to run a must-have app after Precise expired.

---

