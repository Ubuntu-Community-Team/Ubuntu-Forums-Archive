---
title: "Errors configuring and installin Yersinia"
date: 2007-03-09
forum: General Help
---

### Post by rayj00 on 2007-03-09
Please see bolded text inline......

root@RayJ-PenTest:/Tools/Yersinia/yersinia-0.7.1# ./configure --disable-gtk
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... none
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for a BSD-compatible install... /usr/bin/install -c
[B]checking for makedepend... /usr/bin/makedepend
./configure: line 4176: AC_LBL_UNALIGNED_ACCESS: command not found[/B]
checking for main in -lsocket... no
checking for main in -lresolv... yes
checking for main in -lnsl... yes
checking for main in -lrt... yes
checking for a complete set of pcap headers... found /usr/include
checking for pcap_lib_version in -lpcap... yes
checking for pcap_dump_flush in -lpcap... yes
checking for a complete set of libnet headers... found /usr/include
checking for libnet_build_stp_conf in -lnet... yes
checking if libnet is at least version 1.1.2... yes
checking for sys/sockio.h... no
checking for sys/ioctl.h... yes
checking for net/if.h... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking bstring.h usability... no
checking bstring.h presence... no
checking for bstring.h... no
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking netinet/in_systm.h usability... yes
checking netinet/in_systm.h presence... yes
checking for netinet/in_systm.h... yes
checking for inttypes.h... (cached) yes
checking netinet/in_system.h usability... no
checking netinet/in_system.h presence... no
checking for netinet/in_system.h... no
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether byte ordering is bigendian... no
checking if struct sockaddr has sa_len field... no
checking for memcpy... yes
checking for memset... yes
checking for pthread_setconcurrency... yes
checking for strerror... yes
checking for strtok_r... yes
checking for rand_r... yes
checking for calloc_r... no
checking for malloc_r... no
checking for free_r... no
checking for ctime_r... yes
checking for nanosleep... yes
checking for strerror_r... yes
checking if strerror_r is on glibc version >= 2.0... yes
checking semaphore.h usability... yes
checking semaphore.h presence... yes
checking for semaphore.h... yes
checking sched.h usability... yes
checking sched.h presence... yes
checking for sched.h... yes
checking sys/sched.h usability... no
checking sys/sched.h presence... no
checking for sys/sched.h... no
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pthread_create in -lpthread... yes
checking for pthreads support... ok
configure: checking "location of ncurses.h file"...
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/config.h
config.status: executing depfiles commands

 Yersinia, our beloved one, has been configured with the following options.
                         Remote admin : true
                          Use ncurses : false
                              Use gtk : no

-----------------------------------------------------------------------------

root@RayJ-PenTest:/Tools/Yersinia/yersinia-0.7.1# **make**
Making all in src
make[1]: Entering directory `/Tools/Yersinia/yersinia-0.7.1/src'
make  all-am
make[2]: Entering directory `/Tools/Yersinia/yersinia-0.7.1/src'
**gcc `/libnet-config --defines` -DHAVE_CONFIG_H  -I. -I. -I.      -O3 -Wall -g -c terminal.c**
terminal.c: In function â€˜term_destroyâ€™:
terminal.c:193: error: â€˜struct terminalsâ€™ has no member named â€˜gui_thâ€™
make[2]: *** [terminal.o] Error 1
make[2]: Leaving directory `/Tools/Yersinia/yersinia-0.7.1/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/Tools/Yersinia/yersinia-0.7.1/src'
make: *** [all-recursive] Error 1
root@RayJ-PenTest:/Tools/Yersinia/yersinia-0.7.1# 

------------------------------------------------------------------------
Any ideas what I'm doing wrong?

Thanks,

Ray

---

### Post by rayj00 on 2007-03-10
Please disregard this post. I was trying to install the hard way...

Why not just let Synoptic handle it!! Yahooo! It worked great!!!

I get more and more impressed by this distro!!!

Ray

---

### Post by baekster on 2007-12-30
I recently ran into the same problem.  I was wondering if the ubuntu source fixes the problem...it doesn't.  It turns out that if you don't have ncurses5-dev package installed (ncurses dev library), then the configure script will produce Makefile without ncurses flag (HAS_CURSES) for compiler...and there's one line in the exit routine for the program, where there should be ifdef...endif statement around the offending line (see the patch).

So you won't see the bug if you have ncurses library, but you will see the bug if you DON'T have it.

Anyway, here's the patch:
--- yersinia-0.7.1/src/terminal.c       2006-07-16 08:37:31.000000000 -0400
+++ yersinia-0.7.1_patched/src/terminal.c       2007-12-30 13:22:11.000000000 -0500
@@ -190,7 +190,9 @@
 #endif
 
    pthread_mutex_destroy(&terms->admin_listen_th.finished);
+#ifdef HAS_CURSES
    pthread_mutex_destroy(&terms->gui_th.finished);
+#endif
    pthread_mutex_destroy(&terms->pcap_listen_th.finished);
    pthread_mutex_destroy(&terms->uptime_th.finished);

---

