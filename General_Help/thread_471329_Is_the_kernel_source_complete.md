---
title: "Is the kernel source complete?"
date: 2007-06-11
forum: General Help
---

### Post by ravindra.rajaram on 2007-06-11
My "uname -r" shows *2.6.20-16-generic* 
I've only downloaded the kernel source using apt-get. But, I'm not sure if the headers/source that I've downloaded is complete.
When I run 'make mrproper' I see the following errros:
1. 
[I]scripts/Makefile.clean:17: /usr/src/linux-headers-2.6.20-16/drivers/infiniband/hw/amso1100/Makefile: No such file or directory
make[3]: *** No rule to make target `/usr/src/linux-headers-2.6.20-16/drivers/infiniband/hw/amso1100/Makefile'.  Stop.
make[2]: *** [drivers/infiniband/hw/amso1100] Error 2
make[1]: *** [drivers/infiniband] Error 2
make: *** [_clean_drivers] Error 2

[/I]

2. 
[I]scripts/Makefile.clean:17: /usr/src/linux-headers-2.6.20-16/drivers/infiniband/ulp/srp/Makefile: No such file or directory
make[3]: *** No rule to make target `/usr/src/linux-headers-2.6.20-16/drivers/infiniband/ulp/srp/Makefile'.  Stop.
make[2]: *** [drivers/infiniband/ulp/srp] Error 2
make[1]: *** [drivers/infiniband] Error 2
make: *** [_clean_drivers] Error 2
[/I]

3. 
[I]scripts/Makefile.clean:17: /usr/src/linux-headers-2.6.20-16/Documentation/DocBook/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.20-16/Documentation/DocBook/Makefile'.  Stop.
make: *** [_mrproper_Documentation/DocBook] Error 2
[/I]


I tried to proceed further by creating dummy makefiles (didn't think above were necessary :) )
 But, in any case why are above files missing and what am I missing?

Thanks,
Ravindra.

---

### Post by energiya on 2007-06-12
After installing the source using apt-get you should see it under /usr/src/linux-2.6.x.x . I never had/heard of errors like this. Maybe the deb is corupted?

---

### Post by ravindra.rajaram on 2007-06-13
how can re-download all the files?
when I do an apt-get , I see that all my files are up to date!
-Ravindra.

---

