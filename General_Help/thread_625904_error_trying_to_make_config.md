---
title: "error trying to make config"
date: 2007-11-28
forum: General Help
---

### Post by Cr0n_J0b on 2007-11-28
I'm just trying to make some modules for a drive install...on my 7.04 system it works fine, but on the 7.10 system I get the following...

any help?

root@uNAS:/usr/src/linux-headers-2.6.22-14# make config
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:107:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:108:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:109:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:111:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:112:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:113:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from scripts/basic/fixdep.c:115:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:116:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:117:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function âusageâ:
scripts/basic/fixdep.c:131: warning: implicit declaration of function âfprintfâ
scripts/basic/fixdep.c:131: warning: incompatible implicit declaration of built-in function âfprintfâ
scripts/basic/fixdep.c:131: error: âstderrâ undeclared (first use in this function)
scripts/basic/fixdep.c:131: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:131: error: for each function it appears in.)
scripts/basic/fixdep.c:132: warning: implicit declaration of function âexitâ
scripts/basic/fixdep.c:132: warning: incompatible implicit declaration of built-in function âexitâ
scripts/basic/fixdep.c: In function âprint_cmdlineâ:
scripts/basic/fixdep.c:140: warning: implicit declaration of function âprintfâ
scripts/basic/fixdep.c:140: warning: incompatible implicit declaration of built-in function âprintfâ
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:143: error: âNULLâ undeclared here (not in a function)
scripts/basic/fixdep.c: In function âgrow_configâ:
scripts/basic/fixdep.c:156: warning: implicit declaration of function âreallocâ
scripts/basic/fixdep.c:156: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:158: warning: implicit declaration of function âperrorâ
scripts/basic/fixdep.c:158: warning: incompatible implicit declaration of built-in function âexitâ
scripts/basic/fixdep.c: In function âis_defined_configâ:
scripts/basic/fixdep.c:174: warning: implicit declaration of function âmemcmpâ
scripts/basic/fixdep.c: In function âdefine_configâ:
scripts/basic/fixdep.c:187: warning: implicit declaration of function âmemcpyâ
scripts/basic/fixdep.c:187: warning: incompatible implicit declaration of built-in function âmemcpyâ
scripts/basic/fixdep.c: In function âuse_configâ:
scripts/basic/fixdep.c:206: error: âPATH_MAXâ undeclared (first use in this function)
scripts/basic/fixdep.c:214: warning: incompatible implicit declaration of built-in function âmemcpyâ
scripts/basic/fixdep.c:220: warning: implicit declaration of function âtolowerâ
scripts/basic/fixdep.c:222: warning: incompatible implicit declaration of built-in function âprintfâ
scripts/basic/fixdep.c:206: warning: unused variable âsâ
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:225: error: expected declaration specifiers or â...â before âsize_tâ
scripts/basic/fixdep.c: In function âparse_config_fileâ:
scripts/basic/fixdep.c:227: error: âlenâ undeclared (first use in this function)
scripts/basic/fixdep.c:233: warning: implicit declaration of function ântohlâ
scripts/basic/fixdep.c:244: warning: implicit declaration of function âisalnumâ
scripts/basic/fixdep.c: In function âstrrcmpâ:
scripts/basic/fixdep.c:261: warning: implicit declaration of function âstrlenâ
scripts/basic/fixdep.c:261: warning: incompatible implicit declaration of built-in function âstrlenâ
scripts/basic/fixdep.c: In function âdo_config_fileâ:
scripts/basic/fixdep.c:272: error: storage size of âstâ isnât known
scripts/basic/fixdep.c:276: warning: implicit declaration of function âopenâ
scripts/basic/fixdep.c:276: error: âO_RDONLYâ undeclared (first use in this function)
scripts/basic/fixdep.c:278: warning: incompatible implicit declaration of built-in function âfprintfâ
scripts/basic/fixdep.c:278: error: âstderrâ undeclared (first use in this function)
scripts/basic/fixdep.c:280: warning: incompatible implicit declaration of built-in function âexitâ
scripts/basic/fixdep.c:282: warning: implicit declaration of function âfstatâ
scripts/basic/fixdep.c:284: warning: implicit declaration of function âcloseâ
scripts/basic/fixdep.c:287: warning: implicit declaration of function âmmapâ
scripts/basic/fixdep.c:287: error: âPROT_READâ undeclared (first use in this function)
scripts/basic/fixdep.c:287: error: âMAP_PRIVATEâ undeclared (first use in this function)
scripts/basic/fixdep.c:287: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:294: error: too many arguments to function âparse_config_fileâ
scripts/basic/fixdep.c:296: warning: implicit declaration of function âmunmapâ
scripts/basic/fixdep.c:272: warning: unused variable âstâ
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:301: error: expected declaration specifiers or â...â before âsize_tâ
scripts/basic/fixdep.c: In function âparse_dep_fileâ:
scripts/basic/fixdep.c:304: error: âlenâ undeclared (first use in this function)
scripts/basic/fixdep.c:306: error: âPATH_MAXâ undeclared (first use in this function)
scripts/basic/fixdep.c:308: warning: implicit declaration of function âstrchrâ
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function âstrchrâ
scripts/basic/fixdep.c:310: warning: incompatible implicit declaration of built-in function âfprintfâ
scripts/basic/fixdep.c:310: error: âstderrâ undeclared (first use in this function)
scripts/basic/fixdep.c:311: warning: incompatible implicit declaration of built-in function âexitâ
scripts/basic/fixdep.c:313: warning: incompatible implicit declaration of built-in function âmemcpyâ
scripts/basic/fixdep.c:314: warning: incompatible implicit declaration of built-in function âprintfâ
scripts/basic/fixdep.c:306: warning: unused variable âsâ
scripts/basic/fixdep.c: In function âprint_depsâ:
scripts/basic/fixdep.c:343: error: storage size of âstâ isnât known
scripts/basic/fixdep.c:347: error: âO_RDONLYâ undeclared (first use in this function)
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function âfprintfâ
scripts/basic/fixdep.c:349: error: âstderrâ undeclared (first use in this function)
scripts/basic/fixdep.c:351: warning: incompatible implicit declaration of built-in function âexitâ
scripts/basic/fixdep.c:355: warning: incompatible implicit declaration of built-in function âfprintfâ
scripts/basic/fixdep.c:359: error: âPROT_READâ undeclared (first use in this function)
scripts/basic/fixdep.c:359: error: âMAP_PRIVATEâ undeclared (first use in this function)
scripts/basic/fixdep.c:359: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:366: error: too many arguments to function âparse_dep_fileâ
scripts/basic/fixdep.c:343: warning: unused variable âstâ
scripts/basic/fixdep.c: In function âtrapsâ:
scripts/basic/fixdep.c:378: warning: incompatible implicit declaration of built-in function âfprintfâ
scripts/basic/fixdep.c:378: error: âstderrâ undeclared (first use in this function)
scripts/basic/fixdep.c:380: warning: incompatible implicit declaration of built-in function âexitâ
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2

---

### Post by Cr0n_J0b on 2007-11-28
do I need kernel sources or something like that which I may not have?

---

### Post by kjuliano on 2008-03-15
I have this same problem. 
i am trying to recompile the kernel to try to get acpi to work in gutsy, i have found other posts with the same acpi problem that have me too as the only response. 

I have noticed that issues like these tend to be ignored here... I am not sure why... bad luck i guess.

---

### Post by kkw on 2008-03-16
hi,
I have encountered the same problem on 7.10.
After googling, I found this tutorial - [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
I just installed the required package as stated in step 2 in the tutorial. The "make config" command works well now.

Hope this helps. :)

Regards,
kkw

---

