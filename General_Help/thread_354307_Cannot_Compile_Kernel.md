---
title: "Cannot Compile Kernel"
date: 2007-02-05
forum: General Help
---

### Post by mawdryn on 2007-02-05
Hi,

I'm unable to recompile my Ubuntu kernel to allow for Intel fan control and other ACPI option.

make menuconfig works ok, so I can make the changes, however when compiling, I get the following output:

```
  CHK     include/linux/version.h
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/i386/Kconfig
#
# using defaults found in .config
#
  SPLIT   include/linux/autoconf.h -> include/config/*
  HOSTCC  scripts/genksyms/genksyms.o
  HOSTCC  scripts/genksyms/lex.o
  HOSTCC  scripts/genksyms/parse.o
  HOSTLD  scripts/genksyms/genksyms
  HOSTCC  scripts/mod/mk_elfconfig
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
  HOSTCC  scripts/kallsyms
  HOSTCC  scripts/conmakehash
make[1]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make: *** [init] Error 2

```

I've tried a 'make clean' and a 'make mrproper' however I get the following output:

```
scripts/Makefile.clean:17: /usr/src/linux-headers-2.6.17-10-generic/drivers/infiniband/ulp/srp/Makefile: No such file or directory
make[3]: *** No rule to make target `/usr/src/linux-headers-2.6.17-10-generic/drivers/infiniband/ulp/srp/Makefile'.  Stop.
make[2]: *** [drivers/infiniband/ulp/srp] Error 2
make[1]: *** [drivers/infiniband] Error 2
make: *** [_clean_drivers] Error 2

```

I'm running Ubuntu Edgy (uname -r displays 2.6.17-10-generic), and have installed the 'linux-headers-2.6.17-10' and the 'linux-headers-2.6.17-10-generic' packages using the Synaptic tool.

I've tried running make from both the /usr/src/linux-headers-2.6.17-10 directory and the /usr/src/linux-headers-2.6.17-10-generic directory with the same result.

No other kernel headers or universe/Multiverse dev packages are installed.  I've read elsewhere that the incorrect kernel header packages can be the cause of this, but I'm pretty sure I'm using the correct packages.

Could anyone please shed some light on this issue.
Many Thanks.

---

### Post by mawdryn on 2007-02-05
Hi,

Found out the generic 'linux source' package had to be installed and then extracted to perform kernel recompiles. I've obviously had linux-header mixed up with linux-source.

---

