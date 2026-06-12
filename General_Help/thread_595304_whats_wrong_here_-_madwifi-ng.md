---
title: "whats wrong here? - madwifi-ng"
date: 2007-10-28
forum: General Help
---

### Post by telovoyagarcar on 2007-10-28
After doing this:

svn checkout [http://svn.madwifi.org/madwifi/trunk/](http://svn.madwifi.org/madwifi/trunk/) madwifi-ng

i got the madwifi driver in a folder in the home directory.
So now i just use the "make" command and this is what i get... there are errors... i don't know what to do. 

```

axo@kubuntaxo:~/madwifi-ng$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/axo/madwifi-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/axo/madwifi-ng/ath/if_ath.o
  CC [M]  /home/axo/madwifi-ng/ath/if_ath_pci.o
  LD [M]  /home/axo/madwifi-ng/ath/ath_pci.o
  CC [M]  /home/axo/madwifi-ng/ath_hal/ah_os.o
  HOSTCC  /home/axo/madwifi-ng/ath_hal/uudecode
/home/axo/madwifi-ng/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/axo/madwifi-ng/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/axo/madwifi-ng/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/axo/madwifi-ng/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/axo/madwifi-ng/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/axo/madwifi-ng/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/axo/madwifi-ng/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/axo/madwifi-ng/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/axo/madwifi-ng/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/axo/madwifi-ng/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/axo/madwifi-ng/ath_hal/uudecode.c: At top level:
/home/axo/madwifi-ng/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/axo/madwifi-ng/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/axo/madwifi-ng/ath_hal/uudecode.c: In function 'main':
/home/axo/madwifi-ng/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/axo/madwifi-ng/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/axo/madwifi-ng/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/axo/madwifi-ng/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/axo/madwifi-ng/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/axo/madwifi-ng/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/axo/madwifi-ng/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/axo/madwifi-ng/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/axo/madwifi-ng/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/axo/madwifi-ng/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/axo/madwifi-ng/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/axo/madwifi-ng/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/axo/madwifi-ng/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/axo/madwifi-ng/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/axo/madwifi-ng/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/axo/madwifi-ng/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/axo/madwifi-ng/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/axo/madwifi-ng/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/axo/madwifi-ng/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/axo/madwifi-ng/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/axo/madwifi-ng/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/axo/madwifi-ng/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/axo/madwifi-ng/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/axo/madwifi-ng/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/axo/madwifi-ng/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/axo/madwifi-ng/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/axo/madwifi-ng/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/axo/madwifi-ng/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/axo/madwifi-ng/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/axo/madwifi-ng/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/axo/madwifi-ng/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/axo/madwifi-ng/ath_hal/uudecode] Error 1
make[2]: *** [/home/axo/madwifi-ng/ath_hal] Error 2
make[1]: *** [_module_/home/axo/madwifi-ng] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2

```


The idea is to patch the driver after i see it actually works. and then reinstall the patched driver. But i see that the "vanilla" driver is not finishing to compile itself as is right?

---

### Post by telovoyagarcar on 2007-10-28
Bump... nobody has any clue?

---

### Post by telovoyagarcar on 2007-10-29
I give up. Can't install and make work neither the internal wireless adapter that came with this notebook or the external PCMCIA card. Linux is a waste of time when dealing with wireless stuff.
I can't believe so many articles and stupids saying that it is easier and better than vista.

---

### Post by mnml on 2007-10-29
sudo aptitude install build-essential

---

