---
title: "Ubuntu 14.04 Kernel 4.4Build Errors"
date: 2016-02-03
forum: General Help
---

### Post by Redalien0304 on 2016-02-03
Have Ubuntu 14.04 installed. Get Kernel Build Errors when trying to install Kernel 4.4. Have got kernel 4.4 installed but NO  WIFI. Have kernel 4.1.5 Installed works fine. Only issue was Wifi on Kernel 4.1.5 got that working by doing "sudo apt-get install --reinstall bcmwl-kernel-source". That does not work on kernel 4.4.
>  DKMS make.log for bcmwl-6.30.223.271+bdcom for kernel 4.4.0-040400-generic (x86_64)Wed Feb  3 10:46:36 PST 2016
make: Entering directory `/usr/src/linux-headers-4.4.0-040400-generic'
Makefile:660: Cannot use CONFIG_CC_STACKPROTECTOR_STRONG: -fstack-protector-strong not supported by compiler
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o
gcc: error: unrecognized command line option ‘-fstack-protector-strong’
make[1]: *** [/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/shared/linux_osl.o] Error 1
make: *** [_module_/var/lib/dkms/bcmwl/6.30.223.271+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-4.4.0-040400-generic'  

Thanks for any help in advance Thanks

---

### Post by Doug S on 2016-02-03
Yes, Kernel 4.4 expects to be built with a newer version of gcc, that supports fstack-protector-strong.
You have two options: Install a newer version of the compiler; Change the kernel configuration to not require CONFIG_CC_STACKPROTECTOR_STRONG.
Myself, and on my 14.04 server, I change the kernel configuration. I run this from the linux directory:```
scripts/config --disable CC_STACKPROTECTOR_STRONG
```For these differences (using 4.5rc1 as an example):```
doug@s15:~/temp-k-git/linux$ diff .config-4.5.0-040500rc1-generic .config
3c3
< # Linux/x86_64 4.5.0-040500rc1-generic Kernel Configuration
---
> # Linux/x86 4.5.0-rc1 Kernel Configuration
286,287c286,287
< CONFIG_CC_STACKPROTECTOR=y
< # CONFIG_CC_STACKPROTECTOR_NONE is not set
---
> # CONFIG_CC_STACKPROTECTOR is not set
> CONFIG_CC_STACKPROTECTOR_NONE=y
289c289
< CONFIG_CC_STACKPROTECTOR_STRONG=y
---
> # CONFIG_CC_STACKPROTECTOR_STRONG is not set

```

---

### Post by Redalien0304 on 2016-02-04
Ok Thanks can you explain more & where to get a Newer version compiler? gcc i assume??


[COLOR=#000000][INDENT]Thanks for any help in advance Thanks[/INDENT]
[/COLOR]

---

### Post by Doug S on 2016-02-05
> **Redalien0304 said:**
> Ok Thanks can you explain more & where to get a Newer version compiler? gcc i assume??Not really, as I didn't go that route. Have a look in and around [here]("http://ubuntuforums.org/showthread.php?t=2303120&page=7&p=13400796#post13400796"). Yes, gcc.

---

### Post by Redalien0304 on 2016-02-10
Thanks Doug S. that got me on the Right Track. So i Solved it by going from the Instructions on this Page
[http://askubuntu.com/questions/466651/how-do-i-use-the-latest-gcc-4-9-on-ubuntu-14-04](http://askubuntu.com/questions/466651/how-do-i-use-the-latest-gcc-4-9-on-ubuntu-14-04)

---

