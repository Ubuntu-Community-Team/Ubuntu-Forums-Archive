---
title: "Libpcap Problem"
date: 2008-04-27
forum: General Help
---

### Post by reyhan on 2008-04-27
hello i just want to compile libpcap
but theres something wrong this something when i type 
```
./configure
```

> checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking gcc version... 4
checking for inline... inline
checking for __attribute__... yes
checking for u_int8_t using gcc... yes
checking for u_int16_t using gcc... yes
checking for u_int32_t using gcc... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sys/ioccom.h usability... no
checking sys/ioccom.h presence... no
checking for sys/ioccom.h... no
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking for net/pfvar.h... no
checking for netinet/if_ether.h... yes
checking for ANSI ioctl definitions... yes
checking for strerror... yes
checking for strlcpy... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for library containing gethostbyname... none required
checking for library containing socket... none required
checking for library containing putmsg... none required
checking for ether_hostton... yes
checking whether ether_hostton is declared... no
checking netinet/ether.h usability... yes
checking netinet/ether.h presence... yes
checking for netinet/ether.h... yes
checking whether ether_hostton is declared... yes
checking if --disable-protochain option is specified... enabled
checking packet capture type... linux
checking for getifaddrs... yes
checking ifaddrs.h usability... yes
checking ifaddrs.h presence... yes
checking for ifaddrs.h... yes
checking if --enable-ipv6 option is specified... no
checking whether to build optimizer debugging code... no
checking whether to build parser debugging code... no
checking Linux kernel version... 2
checking if if_packet.h has tpacket_stats defined... yes
checking whether we have /proc/net/dev... yes
checking whether we have DAG API headers... no (/usr/local/include)
checking whether we have Septel API... no
checking for flex... flex
checking for flex 2.4 or higher... yes
checking for bison... bison
checking for ranlib... ranlib
checking if sockaddr struct has sa_len member... no
checking if sockaddr_storage struct exists... yes
checking if dl_hp_ppa_info_t struct has dl_module_id_1 member... no
checking if unaligned accesses fail... no
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating config.h
config.status: config.h is unchanged

can someone help me?

---

### Post by Unix_Slayer on 2008-05-30
I have the same problem compiling GCC. Anyone have an idea?

> config.status: creating Makefile
config.status: WARNING:  ../.././libcpp/Makefile.in seems to ignore the --datarootdir setting


---

