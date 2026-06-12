---
title: "Samba 4.0.9"
date: 2013-10-04
forum: General Help
---

### Post by TheHammer101 on 2013-10-04
I would still say I'm a bit of a Linux noob, but here goes:

I am running Ubuntu Server 12.04.3 LTS x86 on a box being used as my router, HTPC, and NAS device with 5 gigabit Ethernet ports.

One is designated WAN, and the other 4 are bridged into LAN. Everything works perfectly, aside from weird issues with Samba.

The apt-get install samba version works just fine at first. I've set up several shares that work fine, but when either the Ubuntu router (LaServer), or my main computer running Windoze 7 (Little Boy) restart/sleep/hibernate/disconnect from the network in any way my normal Samba transfer speeds of anywhere from 60-90 megabytes per second drop to below 500 kilobytes per second!?! I know it's not the network connection, because I still obtain nearly gigabit speeds to other computers, and faster speeds over the internet than what I obtain via Samba. I have tried nearly EVERYTHING I could find on both machines to get this to stop happening. I'm not sure if this happens on the other machines on the network, because they generally don't access the shares. I've reformatted both LaServer and Little Boy several times with several different configurations trying to get this to work right with 0 luck at all. The only thing that seems to make any difference is changing the LAN port I'm using.. :confused: I run out of ports after 3 plug changes though! Plus it's a pain to change the port I'm using every time I use my computer.

Being that the apt-get install samba doesn't install the latest version I have been trying to compile and run Samba 4.0.9 from scratch, in the hope that this issue has been fixed. I've followed several guides with mainly the same idea, and for some reason Samba 4 will not start! All parts of the process seem to work just fine "./configure", "make", "make install", and adding the script to init.d do not throw any sort of error at the end, although there are minor problems it seems to encounter during the process..

```
[ 625/3781] Compiling lib/tevent/tevent_util.c
[ 626/3781] Compiling lib/tevent/tevent_wakeup.c
[ 627/3781] Compiling lib/tevent/tevent_epoll.c
[ 628/3781] Compiling lib/tevent/pytevent.c
../lib/tevent/pytevent.c: In function âpy_tevent_context_newâ:
../lib/tevent/pytevent.c:639:2: warning: passing argument 4 of âPyArg_ParseTupleAndKeywordsâ from incompatible pointer type [enabled by default]
/usr/include/python2.7/modsupport.h:28:17: note: expected âchar **â but argument is of type âconst char * const*â
[ 629/3781] Compiling lib/addns/dnsquery.c
[ 630/3781] Compiling lib/addns/dnsrecord.c
[ 631/3781] Compiling lib/addns/dnsutils.c
[ 632/3781] Compiling lib/addns/dnssock.c
[ 633/3781] Compiling lib/addns/dnsgss.c
[ 634/3781] Compiling lib/addns/dnsmarshall.c
[ 635/3781] Compiling lib/addns/error.c
[ 636/3781] Compiling lib/ccan/hash/hash.c
[ 637/3781] Compiling lib/ccan/ilog/ilog.c
[ 638/3781] Compiling lib/ccan/read_write_all/read_write_all.c
[ 639/3781] Compiling lib/ccan/str/debug.c
[ 640/3781] Compiling lib/ccan/str/str.c
[ 641/3781] Compiling lib/ccan/tally/tally.c
[ 642/3781] Compiling lib/ccan/likely/likely.c
[ 643/3781] Compiling lib/ccan/err/err.c
[ 644/3781] Compiling lib/tdb/common/check.c
[ 645/3781] Compiling lib/tdb/common/error.c
[ 646/3781] Compiling lib/tdb/common/tdb.c
[ 647/3781] Compiling lib/tdb/common/traverse.c
[ 648/3781] Compiling lib/tdb/common/freelistcheck.c
[ 649/3781] Compiling lib/tdb/common/lock.c
[ 650/3781] Compiling lib/tdb/common/dump.c
[ 651/3781] Compiling lib/tdb/common/freelist.c
[ 652/3781] Compiling lib/tdb/common/io.c
[ 653/3781] Compiling lib/tdb/common/open.c
[ 654/3781] Compiling lib/tdb/common/transaction.c
[ 655/3781] Compiling lib/tdb/common/hash.c
[ 656/3781] Compiling lib/tdb/common/summary.c
[ 657/3781] Compiling lib/tdb/common/rescue.c
[ 658/3781] Compiling lib/tdb/tools/tdbtorture.c
[ 659/3781] Compiling lib/tdb/tools/tdbrestore.c
[ 660/3781] Compiling lib/tdb/tools/tdbdump.c
../lib/tdb/tools/tdbdump.c: In function âdump_tdbâ:
../lib/tdb/tools/tdbdump.c:113:3: warning: passing argument 3 of âtdb_rescueâ discards âconstâ qualifier from pointer target type [enabled by default]
default/include/public/tdb.h:835:5: note: expected âvoid *â but argument is of type âconst char *â
[ 661/3781] Compiling lib/tdb/tools/tdbbackup.c
[ 662/3781] Compiling lib/tdb/tools/tdbtool.c
[ 663/3781] Compiling lib/tdb/test/external-agent.c
[ 664/3781] Compiling lib/tdb/test/lock-tracking.c
[ 665/3781] Compiling lib/tdb/test/logging.c
[ 666/3781] Compiling lib/tdb/test/run-3G-file.c
```

I read the below link and saw that maybe my compile process is bugged, but I have no idea what they're referring to in order to fix this problem.

[https://lists.samba.org/archive/samba-technical/2012-August/085892.html](https://lists.samba.org/archive/samba-technical/2012-August/085892.html)

Does anybody have any suggestions at all? I'm so lost on this I'm thinking about moving to straight Debian, or some other form of Linux where things seem to just work without issue like this..

---

### Post by TheHammer101 on 2013-10-04
This is the entire compile process I have so far..

# ./configure
```
Checking for program gcc or cc           : /usr/bin/gcc
Checking for program cpp                 : /usr/bin/cpp
Checking for program ar                  : /usr/bin/ar
Checking for program ranlib              : /usr/bin/ranlib
Checking for gcc                         : ok
Checking for program git                 : not found
Check for -MD                            : yes
Checking for program gdb                 : /usr/bin/gdb
Checking build system                    : Linux LaServer 3.5.0-41-generic #64~precise1-Ubuntu SMP Thu Sep 12 17:01:55 UTC 2013 i686 i686 i386 GNU/Linux
Checking for header sys/utsname.h        : yes
Checking uname sysname type              : Linux
Checking uname machine type              : i686
Checking uname release type              : 3.5.0-41-generic
Checking uname version type              : #64~precise1-Ubuntu SMP Thu Sep 12 17:01:55 UTC 2013
Checking for header stdio.h              : yes
Checking simple C program                : ok
Checking for rpath library support       : ok
Checking for -Wl,--version-script support  : ok
Checking compiler accepts -fPIC            : yes
Checking for inline                        : inline
Checking for pkg-config version >= 0.0.0   : yes
Checking for header sys/types.h            : yes
Checking for header sys/stat.h             : yes
Checking for header stdlib.h               : yes
Checking for header stddef.h               : yes
Checking for header memory.h               : yes
Checking for header string.h               : yes
Checking for header strings.h              : yes
Checking for header inttypes.h             : yes
Checking for header stdint.h               : yes
Checking for header unistd.h               : yes
Checking for header minix/config.h         : no
Checking for header ctype.h                : yes
Checking for header standards.h            : no
Checking for header stdbool.h              : yes
Checking for header stdarg.h               : yes
Checking for header vararg.h               : no
Checking for header limits.h               : yes
Checking for header assert.h               : yes
Checking getconf LFS_CFLAGS                : -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64
Checking getconf large file support flags work : ok
Checking for large file support without additional flags : ok
Checking for header sys/time.h                           : yes
Checking for header time.h                               : yes
Checking for WORDS_BIGENDIAN                             : not found
Checking for header signal.h                             : yes
Checking if signal handlers return int                   : not found
Checking for variable __FUNCTION__                       : ok
Checking for va_copy                                     : ok
Checking for HAVE__VA_ARGS__MACRO                        : ok
Checking compiler accepts ['']                           : yes
Checking compiler accepts ['-Werror']                    : yes
Checking for header linux/types.h                        : yes
Checking for header crypt.h                              : yes
Checking for header locale.h                             : yes
Checking for header acl/libacl.h                         : yes
Checking for header compat.h                             : no
Checking for header attr/xattr.h                         : yes
Checking for header dustat.h                             : no
Checking for header fcntl.h                              : yes
Checking for header fnmatch.h                            : yes
Checking for header glob.h                               : yes
Checking for header history.h                            : no
Checking for header krb5.h                               : yes
Checking for header langinfo.h                           : yes
Checking for header libaio.h                             : yes
Checking for header ndir.h                               : no
Checking for header pwd.h                                : yes
Checking for header shadow.h                             : myes
Checking for header sys/acl.h                            : ayes
Checking for header sys/attributes.h                     : kno
Checking for header attr/attributes.h                    : eyes
Checking for header sys/capability.h                     : no
Checking for header sys/dir.h                            : yes
Checking for header sys/epoll.h                          : yes
Checking for header sys/fcntl.h                          : yes
Checking for header sys/filio.h                          : no
Checking for header sys/filsys.h                         : no
Checking for header sys/fs/s5param.h                     : no
Checking for header sys/fs/vx/quota.h                    : no
Checking for header sys/id.h                             : no
Checking for header sys/ioctl.h                          : yes
Checking for header sys/ipc.h                            : yes
Checking for header sys/mman.h                           : yes
Checking for header sys/mode.h                           : no
Checking for header sys/ndir.h                           : no
Checking for header sys/priv.h                           : no
Checking for header sys/resource.h                       : yes
Checking for header sys/security.h                       : no
Checking for header sys/shm.h                            : yes
Checking for header sys/statfs.h                         : yes
Checking for header sys/statvfs.h                        : yes
Checking for header sys/termio.h                         : no
Checking for header sys/vfs.h                            : yes
Checking for header sys/xattr.h                          : yes
Checking for header termio.h                             : yes
Checking for header termios.h                            : yes
Checking for header sys/file.h                           : yes
Checking for header sys/ucontext.h                       : yes
Checking for header sys/wait.h                           : yes
Checking for header malloc.h                             : yes
Checking for header grp.h                                : yes
Checking for header sys/select.h                         : yes
Checking for header setjmp.h                             : yes
Checking for header utime.h                              : yes
Checking for header sys/syslog.h                         : yes
Checking for header syslog.h                             : yes
Checking for header sys/mount.h                          : yes
Checking for header mntent.h                             : yes
Checking for header stropts.h                            : yes
Checking for header unix.h                               : no
Checking for header sys/param.h                          : yes
Checking for header sys/socket.h                         : yes
Checking for header netinet/in.h                         : yes
Checking for header netdb.h                              : yes
Checking for header arpa/inet.h                          : yes
Checking for header netinet/in_systm.h                   : yes
Checking for header netinet/ip.h                         : yes
Checking for header netinet/tcp.h                        : yes
Checking for header netinet/in_ip.h                      : no
Checking for header sys/sockio.h                         : no
Checking for header sys/un.h                             : yes
Checking for header sys/uio.h                            : yes
Checking for header ifaddrs.h                            : yes
Checking for header direct.h                             : no
Checking for header dirent.h                             : yes
Checking for header windows.h                            : no
Checking for header winsock2.h                           : no
Checking for header ws2tcpip.h                           : no
Checking for header libintl.h                            : yes
Checking for header errno.h                              : yes
Checking for header gcrypt.h                             : yes
Checking for header getopt.h                             : yes
Checking for header iconv.h                              : yes
Checking for header sys/inotify.h                        : yes
Checking for header nss.h                                : yes
Checking for header sasl/sasl.h                          : no
Checking for header security/pam_appl.h                  : yes
Checking for header zlib.h                               : yes
Checking for header asm/unistd.h                         : yes
Checking for header aio.h                                : yes
Checking for header sys/unistd.h                         : yes
Checking for header rpc/rpc.h                            : yes
Checking for header rpc/nettype.h                        : no
Checking for header alloca.h                             : yes
Checking for header float.h                              : yes
Checking for header rpcsvc/nis.h                         : yes
Checking for header rpcsvc/ypclnt.h                      : yes
Checking for header sys/prctl.h                          : yes
Checking for header sys/sysctl.h                         : yes
Checking for header sys/fileio.h                         : no
Checking for header sys/filesys.h                        : no
Checking for header sys/dustat.h                         : no
Checking for header sys/sysmacros.h                      : yes
Checking for header xfs/libxfs.h                         : no
Checking for header netgroup.h                           : no
Checking for header rpcsvc/yp_prot.h                     : yes
Checking for HAVE_RPCSVC_YP_PROT_H                       : ok
Checking for header valgrind.h                           : no
Checking for header valgrind/valgrind.h                  : no
Checking for header valgrind/memcheck.h                  : no
Checking for header nss_common.h                         : no
Checking for header nsswitch.h                           : no
Checking for header ns_api.h                             : no
Checking for header sys/extattr.h                        : no
Checking for header sys/ea.h                             : no
Checking for header sys/proplist.h                       : no
Checking for header sys/cdefs.h                          : yes
Checking for header utmp.h                               : yes
Checking for header utmpx.h                              : yes
Checking for header lastlog.h                            : yes
Checking for header syscall.h                            : yes
Checking for header sys/syscall.h                        : yes
Checking for O_DIRECT flag to open(2)                    : ok
Checking for long long                                   : ok
Checking for intptr_t                                    : ok
Checking for uintptr_t                                   : ok
Checking for ptrdiff_t                                   : ok
Checking for comparison_fn_t                             : ok
Checking for _Bool                                       : ok
Checking for bool                                        : ok
Checking for int8_t                                      : ok
Checking for uint8_t                                     : ok
Checking for int16_t                                     : ok
Checking for uint16_t                                    : ok
Checking for int32_t                                     : ok
Checking for uint32_t                                    : ok
Checking for int64_t                                     : ok
Checking for uint64_t                                    : ok
Checking for size_t                                      : ok
Checking for ssize_t                                     : ok
Checking for ino_t                                       : ok
Checking for loff_t                                      : ok
Checking for offset_t                                    : not found
Checking for volatile int                                : ok
Checking for uint_t                                      : not found
Checking for blksize_t                                   : ok
Checking for blkcnt_t                                    : ok
Checking size of bool                                    : 1
Checking size of char                                    : 1
Checking size of int                                     : 4
Checking size of long long                               : 8
Checking size of long                                    : 4
Checking size of short                                   : 2
Checking size of size_t                                  : 4
Checking size of ssize_t                                 : 4
Checking size of int8_t                                  : 1
Checking size of uint8_t                                 : 1
Checking size of int16_t                                 : 2
Checking size of uint16_t                                : 2
Checking size of int32_t                                 : 4
Checking size of uint32_t                                : 4
Checking size of int64_t                                 : 8
Checking size of uint64_t                                : 8
Checking size of void*                                   : 4
Checking size of off_t                                   : 8
Checking size of dev_t                                   : 8
Checking size of ino_t                                   : 8
Checking size of time_t                                  : 4
Checking for socklen_t                                   : ok
Checking for struct ifaddrs                              : ok
Checking for struct addrinfo                             : ok
Checking for struct sockaddr                             : ok
Checking for HAVE_STRUCT_SOCKADDR_IN6                    : ok
Checking for struct sockaddr_storage                     : ok
Checking for sa_family_t                                 : ok
Checking for sig_atomic_t                                : ok
Checking for inet_ntoa                                   : ok
Checking for inet_aton                                   : ok
Checking for inet_ntop                                   : ok
Checking for inet_pton                                   : ok
Checking for connect                                     : ok
Checking for gethostbyname                               : ok
Checking for getaddrinfo                                 : ok
Checking for getnameinfo                                 : ok
Checking for freeaddrinfo                                : ok
Checking for gai_strerror                                : ok
Checking for socketpair                                  : ok
Checking for variable IPV6_V6ONLY                        : ok
Checking for HAVE_IPV6                                   : ok
Checking whether we have ucontext_t                      : ok
Checking for strdup                                      : ok
Checking for memmem                                      : ok
Checking for printf                                      : ok
Checking for memset                                      : ok
Checking for memcpy                                      : ok
Checking for memmove                                     : ok
Checking for strcpy                                      : ok
Checking for strncpy                                     : ok
Checking for bzero                                       : ok
Checking for shl_load                                    : not found
Checking for shl_unload                                  : not found
Checking for shl_findsym                                 : not found
Checking for pipe                                        : ok
Checking for strftime                                    : ok
Checking for srandom                                     : ok
Checking for random                                      : ok
Checking for srand                                       : ok
Checking for rand                                        : ok
Checking for usleep                                      : ok
Checking for setbuffer                                   : ok
Checking for lstat                                       : ok
Checking for getpgrp                                     : ok
Checking for utime                                       : ok
Checking for utimes                                      : ok
Checking for setuid                                      : ok
Checking for seteuid                                     : ok
Checking for setreuid                                    : ok
Checking for setresuid                                   : ok
Checking for setgid                                      : ok
Checking for setegid                                     : ok
Checking for setregid                                    : ok
Checking for setresgid                                   : ok
Checking for chroot                                      : ok
Checking for strerror                                    : ok
Checking for vsyslog                                     : ok
Checking for setlinebuf                                  : ok
Checking for mktime                                      : ok
Checking for ftruncate                                   : ok
Checking for chsize                                      : not found
Checking for rename                                      : ok
Checking for waitpid                                     : ok
Checking for wait4                                       : ok
Checking for initgroups                                  : ok
Checking for pread                                       : ok
Checking for pwrite                                      : ok
Checking for strndup                                     : ok
Checking for strcasestr                                  : ok
Checking for strtok_r                                    : ok
Checking for mkdtemp                                     : ok
Checking for dup2                                        : ok
Checking for dprintf                                     : ok
Checking for vdprintf                                    : ok
Checking for isatty                                      : ok
Checking for chown                                       : ok
Checking for lchown                                      : ok
Checking for link                                        : ok
Checking for readlink                                    : ok
Checking for symlink                                     : ok
Checking for realpath                                    : ok
Checking for snprintf                                    : ok
Checking for vsnprintf                                   : ok
Checking for asprintf                                    : ok
Checking for vasprintf                                   : ok
Checking for setenv                                      : ok
Checking for unsetenv                                    : ok
Checking for strnlen                                     : ok
Checking for strtoull                                    : ok
Checking for __strtoull                                  : not found
Checking for strtouq                                     : ok
Checking for strtoll                                     : ok
Checking for __strtoll                                   : not found
Checking for strtoq                                      : ok
Checking for memalign                                    : ok
Checking for posix_memalign                              : ok
Checking for strlcpy                                     : not found
Checking for strlcat                                     : not found
Checking for strlcpy                                     : not found
Checking for strlcat                                     : not found
Checking for library bsd                                 : yes
Checking for strlcpy                                     : ok
Checking for strlcat                                     : ok
Checking for getpeereid                                  : not found
Checking for getpeereid                                  : ok
Checking for setproctitle                                : ok
Checking whether we can use SO_PEERCRED to get socket credentials : ok
Checking correct behavior of strtoll                              : not found
Checking for if_nametoindex                                       : ok
Checking for strerror_r                                           : ok
Checking for getdirentries                                        : ok
Checking for getdents                                             : not found
Checking for syslog                                               : ok
Checking for gai_strerror                                         : ok
Checking for get_current_dir_name                                 : ok
Checking for timegm                                               : ok
Checking for getifaddrs                                           : ok
Checking for freeifaddrs                                          : ok
Checking for mmap                                                 : ok
Checking for setgroups                                            : ok
Checking for syscall                                              : ok
Checking for setsid                                               : ok
Checking for getgrent_r                                           : ok
Checking for getgrgid_r                                           : ok
Checking for getgrnam_r                                           : ok
Checking for getgrouplist                                         : ok
Checking for getpagesize                                          : ok
Checking for getpwent_r                                           : ok
Checking for getpwnam_r                                           : ok
Checking for getpwuid_r                                           : ok
Checking for epoll_create                                         : ok
Checking for fgetxattr                                            : ok
Checking for flistea                                              : not found
Checking for flistxattr                                           : ok
Checking for fremovexattr                                         : ok
Checking for fsetxattr                                            : ok
Checking for getxattr                                             : ok
Checking for listxattr                                            : ok
Checking for removexattr                                          : ok
Checking for setxattr                                             : ok
Checking for library attr                                         : yes
Checking for flistea                                              : not found
Checking whether xattr interface takes additional options         : not found
Checking for dlopen                                               : not found
Checking for dlsym                                                : not found
Checking for dlerror                                              : not found
Checking for dlclose                                              : not found
Checking for library dl                                           : yes
Checking for dlopen                                               : ok
Checking for dlsym                                                : ok
Checking for dlerror                                              : ok
Checking for dlclose                                              : ok
Checking for declaration of dlopen                                : ok
Checking C prototype for dlopen                                   : not found
Checking for fdatasync                                            : ok
Checking for declaration of fdatasync                             : ok
Checking for clock_gettime                                        : not found
Checking for library rt                                           : yes
Checking for clock_gettime                                        : ok
Checking whether the clock_gettime clock ID CLOCK_MONOTONIC is available : ok
Checking whether the clock_gettime clock ID CLOCK_PROCESS_CPUTIME_ID is available : ok
Checking whether the clock_gettime clock ID CLOCK_REALTIME is available           : ok
Checking for struct timespec                                                      : ok
Checking for header net/if.h                                                      : yes
Checking for header arpa/nameser.h                                                : yes
Checking for header resolv.h                                                      : yes
Checking for res_search                                                           : not found
Checking for library resolv                                                       : yes
Checking for res_search                                                           : ok
Checking for gettext                                                              : ok
Checking for library intl                                                         : not found
Checking for dgettext                                                             : ok
Checking for pthread_create                                                       : not found
Checking for library pthread                                                      : yes
Checking for pthread_create                                                       : ok
Checking for crypt                                                                : not found
Checking for library crypt                                                        : yes
Checking for crypt                                                                : ok
Checking for header readline.h                                                    : no
Checking for header readline/readline.h                                           : yes
Checking for header readline/history.h                                            : yes
Checking for variable rl_event_hook                                               : ok
Checking for declaration of snprintf                                              : ok
Checking for declaration of vsnprintf                                             : ok
Checking for declaration of asprintf                                              : ok
Checking for declaration of vasprintf                                             : ok
Checking for declaration of errno                                                 : ok
Checking for declaration of environ                                               : ok
Checking for declaration of getgrent_r                                            : ok
Checking for declaration of getpwent_r                                            : ok
Checking for declaration of pread                                                 : ok
Checking for declaration of pwrite                                                : ok
Checking for declaration of setenv                                                : ok
Checking for declaration of setresgid                                             : ok
Checking for declaration of setresuid                                             : ok
Checking for header poll.h                                                        : yes
Checking for poll                                                                 : ok
Checking for strptime                                                             : ok
Checking for declaration of strptime                                              : ok
Checking for working strptime                                                     : ok
Checking for HAVE_GETTIMEOFDAY_TZ                                                 : ok
Checking for C99 vsnprintf                                                        : ok
Checking for HAVE_SHARED_MMAP                                                     : ok
Checking for HAVE_MREMAP                                                          : ok
Checking for HAVE_INCOHERENT_MMAP                                                 : not found
Checking for HAVE_IMMEDIATE_STRUCTURES                                            : ok
Checking for HAVE_MKDIR_MODE                                                      : ok
Checking for member st_mtim.tv_nsec in struct stat                                : ok
Checking for member st_rdev in struct stat                                        : ok
Checking for member st_rdev in struct stat                                        : ok
Checking for member ss_family in struct sockaddr_storage                          : ok
Checking for member __ss_family in struct sockaddr_storage                        : not found
Checking for member sa_len in struct sockaddr                                     : not found
Checking for member sin_len in struct sockaddr_in                                 : not found
Checking for HAVE_UNIXSOCKET                                                      : ok
Checking for HAVE_SECURE_MKSTEMP                                                  : ok
Checking compiler accepts -fvisibility=hidden                                     : yes
Checking for HAVE_VISIBILITY_ATTR                                                 : ok
Checking for HAVE_IFACE_GETIFADDRS                                                : ok
Checking for getpass                                                              : ok
Checking for getpassphrase                                                        : not found
Checking for REPLACE_GETPASS                                                      : ok
Checking for getpwnam_r                                                           : ok
Checking for getpwuid_r                                                           : ok
Checking for getpwent_r                                                           : ok
Checking for declaration of getpwent_r                                            : ok
Checking C prototype for getpwent_r                                               : not found
Checking for declaration of getgrent_r                                            : ok
Checking C prototype for getgrent_r                                               : not found
Checking C prototype for getpwent_r                                               : not found
Checking C prototype for getgrent_r                                               : not found
Checking for getgrouplist                                                         : ok
Checking for program perl                                                         : /usr/bin/perl
Checking for program xsltproc                                                     : not found
Checking for program python                                                       : /usr/bin/python
Checking for program python                                                       : /usr/bin/python
Checking for program python                                                       : /usr/bin/python
Checking for Python version >= 2.4.2                                              : ok 2.7.3
Checking for library python2.7                                                    : yes
Checking for program python2.7-config                                             : /usr/bin/python2.7-config
Checking for custom code                                                          : yes
Dynconfig[STATEDIR]:                                                              : '/usr/local/samba/var/locks'
Dynconfig[SCRIPTSBINDIR]:                                                         : '/usr/local/samba/sbin'
Dynconfig[PAMMODULESDIR]:                                                         : '/usr/local/samba/lib/security'
Dynconfig[WINBINDD_SOCKET_DIR]:                                                   : '/usr/local/samba/var/run/winbindd'
Dynconfig[PRIVATE_DIR]:                                                           : '/usr/local/samba/private'
Dynconfig[SETUPDIR]:                                                              : '/usr/local/samba/share/setup'
Dynconfig[PIDDIR]:                                                                : '/usr/local/samba/var/run'
Dynconfig[PKGCONFIGDIR]:                                                          : '/usr/local/samba/lib/pkgconfig'
Dynconfig[DATADIR]:                                                               : '/usr/local/samba/share'
Dynconfig[CACHEDIR]:                                                              : '/usr/local/samba/var/cache'
Dynconfig[SBINDIR]:                                                               : '/usr/local/samba/sbin'
Dynconfig[NCALRPCDIR]:                                                            : '/usr/local/samba/var/run/ncalrpc'
Dynconfig[LMHOSTSFILE]:                                                           : '/usr/local/samba/etc/lmhosts'
Dynconfig[LOCKDIR]:                                                               : '/usr/local/samba/var/lock'
Dynconfig[SWATDIR]:                                                               : '/usr/local/samba/share/swat'
Dynconfig[PYTHONARCHDIR]:                                                         : '/usr/local/samba/lib/python2.7/site-packages'
Dynconfig[LOGFILEBASE]:                                                           : '/usr/local/samba/var'
Dynconfig[PYTHONDIR]:                                                             : '/usr/local/samba/lib/python2.7/site-packages'
Dynconfig[NTP_SIGND_SOCKET_DIR]:                                                  : '/usr/local/samba/var/lib/ntp_signd'
Dynconfig[CONFIGFILE]:                                                            : '/usr/local/samba/etc/smb.conf'
Dynconfig[SOCKET_DIR]:                                                            : '/usr/local/samba/var/run'
Dynconfig[MODULESDIR]:                                                            : '/usr/local/samba/lib'
Dynconfig[WINBINDD_PRIVILEGED_SOCKET_DIR]:                                        : '/usr/local/samba/var/lib/winbindd_privileged'
Dynconfig[LIBDIR]:                                                                : '/usr/local/samba/lib'
Dynconfig[LOCALEDIR]:                                                             : '/usr/local/samba/share/locale'
Dynconfig[NMBDSOCKETDIR]:                                                         : '/usr/local/samba/var/run/nmbd'
Dynconfig[INCLUDEDIR]:                                                            : '/usr/local/samba/include'
Dynconfig[CODEPAGEDIR]:                                                           : '/usr/local/samba/share/codepages'
Dynconfig[PRIVATELIBDIR]:                                                         : '/usr/local/samba/lib/private'
Dynconfig[PRIVILEGED_SOCKET_DIR]:                                                 : '/usr/local/samba/var/lib'
Dynconfig[LIBEXECDIR]:                                                            : '/usr/local/samba/libexec'
Dynconfig[SMB_PASSWD_FILE]:                                                       : '/usr/local/samba/private/smbpasswd'
Dynconfig[BINDIR]:                                                                : '/usr/local/samba/bin'
Dynconfig[CONFIGDIR]:                                                             : '/usr/local/samba/etc'
Checking for system tdb >= 1.2.11                                                 : not found
Checking for stylesheet http://docbook.sourceforge.net/release/xsl/current/manpages/docbook.xsl : not found
Checking for program python                                                                     : /usr/bin/python
Checking for Python version >= 2.4.2                                                            : ok 2.7.3
Checking for python headers                                                                     : using cache
Checking linker accepts -Wl,-no-undefined                                                       : yes
Checking linker accepts ['-undefined', 'dynamic_lookup']                                        : no
Checking for system talloc >= 2.0.7                                                             : not found
Checking for system pytalloc-util >= 2.0.7                                                      : not found
Checking for stylesheet http://docbook.sourceforge.net/release/xsl/current/manpages/docbook.xsl : not found
Checking for program python                                                                     : /usr/bin/python
Checking for Python version >= 2.4.2                                                            : ok 2.7.3
Checking for python headers                                                                     : using cache
Checking linker accepts -Wl,-no-undefined                                                       : yes
Checking linker accepts ['-undefined', 'dynamic_lookup']                                        : no
Checking for system tevent >= 0.9.18                                                            : not found
Checking for epoll_create                                                                       : ok
Checking value of NSIG                                                                          : 65
Checking value of _NSIG                                                                         : 65
Checking value of SIGRTMAX                                                                      : 64
Checking value of SIGRTMIN                                                                      : 34
Checking for program python                                                                     : /usr/bin/python
Checking for Python version >= 2.4.2                                                            : ok 2.7.3
Checking for python headers                                                                     : using cache
Checking linker accepts -Wl,-no-undefined                                                       : yes
Checking linker accepts ['-undefined', 'dynamic_lookup']                                        : no
Checking for system popt                                                                        : yes
Checking for header popt.h                                                                      : yes
Checking for library popt                                                                       : yes
Checking for poptGetContext                                                                     : ok
Checking for program python                                                                     : /usr/bin/python
Checking for program xsltproc                                                                   : not found
Checking for Python version >= 2.4.2                                                            : ok 2.7.3
Checking for python headers                                                                     : using cache
Checking for system ldb >= 1.1.16                                                               : not found
Checking for system pyldb-util >= 1.1.16                                                        : not found
Checking linker accepts -Wl,-no-undefined                                                       : yes
Checking linker accepts ['-undefined', 'dynamic_lookup']                                        : no
Checking for u_char                                                                             : ok
Checking for u_int32_t                                                                          : ok
Checking for header err.h                                                                       : yes
Checking for header sys/bswap.h                                                                 : no
Checking for header sys/stropts.h                                                               : yes
Checking for header sys/timeb.h                                                                 : yes
Checking for header sys/times.h                                                                 : yes
Checking for header timezone.h                                                                  : no
Checking for header ttyname.h                                                                   : no
Checking for header netinet/in6.h                                                               : no
Checking for header netinet6/in6.h                                                              : no
Checking for header curses.h                                                                    : no
Checking for header term.h                                                                      : no
Checking for header termcap.h                                                                   : no
Checking for atexit                                                                             : ok
Checking for cgetent                                                                            : not found
Checking for getprogname                                                                        : not found
Checking for setprogname                                                                        : not found
Checking for gethostname                                                                        : ok
Checking for putenv                                                                             : ok
Checking for rcmd                                                                               : ok
Checking for readv                                                                              : ok
Checking for sendmsg                                                                            : ok
Checking for setitimer                                                                          : ok
Checking for strlwr                                                                             : not found
Checking for strncasecmp                                                                        : ok
Checking for strptime                                                                           : ok
Checking for strsep                                                                             : ok
Checking for strsep_copy                                                                        : not found
Checking for strtok_r                                                                           : ok
Checking for strupr                                                                             : not found
Checking for swab                                                                               : ok
Checking for umask                                                                              : ok
Checking for uname                                                                              : ok
Checking for unsetenv                                                                           : ok
Checking for closefrom                                                                          : not found
Checking for err                                                                                : ok
Checking for warn                                                                               : ok
Checking for errx                                                                               : ok
Checking for warnx                                                                              : ok
Checking for flock                                                                              : ok
Checking for writev                                                                             : ok
Checking for strerror_r                                                                         : ok
Checking for XSI (rather than GNU) prototype for strerror_r                                     : not found
Checking for hstrerror                                                                          : ok
Checking for socket                                                                             : ok
Checking for getipnodebyname                                                                    : not found
Checking for gethostent                                                                         : ok
Checking for gethostent_r                                                                       : ok
Checking for sethostent                                                                         : ok
Checking for endhostent                                                                         : ok
Checking for getipnodebyaddr                                                                    : not found
Checking for freehostent                                                                        : not found
Checking for gethostbyname_r                                                                    : ok
Checking for gethostbyaddr                                                                      : ok
Checking for library socket                                                                     : not found
Checking for library nsl                                                                        : yes
Checking for getipnodebyname                                                                    : not found
Checking for getipnodebyaddr                                                                    : not found
Checking for freehostent                                                                        : not found
Checking for iruserok                                                                           : ok
Checking for bswap16                                                                            : not found
Checking for bswap32                                                                            : not found
Checking for header sys/termios.h                                                               : yes
Checking for struct winsize                                                                     : ok
Checking for member ws_xpixel in struct winsize                                                 : ok
Checking for member ws_ypixel in struct winsize                                                 : ok
Checking for variable h_errno                                                                   : ok
Checking for declaration of h_errno                                                             : ok
Checking for res_nsearch                                                                        : not found
Checking for res_ndestroy                                                                       : not found
Checking for dns_search                                                                         : not found
Checking for dn_expand                                                                          : not found
Checking for res_nsearch                                                                        : ok
Checking for res_ndestroy                                                                       : not found
Checking for dns_search                                                                         : not found
Checking for dn_expand                                                                          : ok
Checking for variable _res                                                                      : ok
Checking for declaration of _res                                                                : ok
Checking for openpty                                                                            : not found
Checking for library util                                                                       : yes
Checking for openpty                                                                            : ok
Checking for dirfd                                                                              : ok
Checking for declaration of dirfd                                                               : ok
Checking for member dd_fd in DIR                                                                : not found
Using in-tree heimdal kerberos defines
Checking for program krb5-config.heimdal                                                        : not found
Checking for program krb5-config                                                                : /usr/bin/krb5-config
Checking for system com_err                                                                     : yes
Checking for library com_err                                                                    : yes
Checking for com_right_r                                                                        : ok
Checking for gnutls >= 1.4.0 and broken versions                                                : yes
Checking for library gnutls                                                                     : yes
Checking for gnutls_global_init                                                                 : ok
Checking for header gnutls/x509.h                                                               : yes
Checking for variable gnutls_x509_crt_set_version                                               : ok
Checking for variable gnutls_x509_crt_set_subject_key_id                                        : ok
Checking for gnutls_datum                                                                       : ok
Checking for gnutls_datum_t                                                                     : ok
Checking for library gcrypt                                                                     : yes
Checking for gcry_control                                                                       : ok
Checking for library gpg-error                                                                  : yes
Checking for gpg_err_code_from_errno                                                            : ok
Checking for header linux/fcntl.h                                                               : yes
Checking for declaration of F_SETLEASE                                                          : ok
Checking for declaration of SA_SIGINFO                                                          : ok
Checking for backtrace                                                                          : ok
Checking for backtrace_symbols                                                                  : ok
Checking for sigprocmask                                                                        : ok
Checking for sigblock                                                                           : ok
Checking for sigaction                                                                          : ok
Checking for member f_frsize in struct statvfs                                                  : ok
Checking for statvfs (SVR4)                                                                     : ok
Checking for *bsd style statfs with statfs.f_iosize                                             : not found
Checking if f_fsid is an integer                                                                : ok
Checking whether statvfs.f_flag exists                                                          : ok
Checking whether statvfs.f_flags exists                                                         : not found
Checking for header byteswap.h                                                                  : yes
Checking for bswap_64                                                                           : ok
Checking for HAVE_ATTRIBUTE_COLD                                                                : ok
Checking for HAVE_ATTRIBUTE_CONST                                                               : ok
Checking for HAVE_ATTRIBUTE_NORETURN                                                            : ok
Checking for HAVE_ATTRIBUTE_PRINTF                                                              : ok
Checking for HAVE_ATTRIBUTE_UNUSED                                                              : ok
Checking for HAVE_ATTRIBUTE_USED                                                                : ok
Checking for header endian.h                                                                    : yes
Checking for header sys/endian.h                                                                : no
Checking for HAVE_LITTLE_ENDIAN                                                                 : not found
Checking for HAVE_BIG_ENDIAN                                                                    : not found
Checking for HAVE_LITTLE_ENDIAN - runtime                                                       : ok
Checking for HAVE_BIG_ENDIAN - runtime                                                          : not found
Checking for HAVE_BUILTIN_CHOOSE_EXPR                                                           : ok
Checking for HAVE_BUILTIN_CLZ                                                                   : ok
Checking for HAVE_BUILTIN_CLZL                                                                  : ok
Checking for HAVE_BUILTIN_CLZLL                                                                 : ok
Checking for HAVE_BUILTIN_CONSTANT_P                                                            : ok
Checking for HAVE_BUILTIN_EXPECT                                                                : ok
Checking for HAVE_BUILTIN_POPCOUNTL                                                             : ok
Checking for HAVE_BUILTIN_TYPES_COMPATIBLE_P                                                    : ok
Checking for HAVE_COMPOUND_LITERALS                                                             : ok
Checking for HAVE_FLEXIBLE_ARRAY_MEMBER                                                         : ok
Checking for HAVE_ISBLANK                                                                       : ok
Checking for HAVE_TYPEOF                                                                        : ok
Checking for HAVE_WARN_UNUSED_RESULT                                                            : ok
Checking for small off_t                                                                        : yes
Checking for -D_FILE_OFFSET_BITS=64                                                             : yes
Checking for library z                                                                          : yes
Checking for zlibVersion                                                                        : ok
Checking for ZLIB_VERNUM >= 0x1230 and working link to zlib                                     : ok
Checking for library iconv                                                                      : no
Checking for library iconv                                                                      : not found
Checking for iconv_open                                                                         : ok
Checking for pam_start                                                                          : not found
Checking for library pam                                                                        : yes
Checking for pam_start                                                                          : ok
Checking for header security/pam_modules.h                                                      : yes
Checking for header pam/pam_modules.h                                                           : no
Checking for header nss_dbdefs.h                                                                : no
Checking for member ipnode.af_family in union nss_XbyY_key                                      : not found
Checking for member pw_comment in struct passwd                                                 : not found
Checking for member pw_age in struct passwd                                                     : not found
Checking for system iniparser                                                                   : not found
Checking for header iniparser.h                                                                 : no
Checking for system subunit                                                                     : not found
Checking for library ncurses                                                                    : not found
Checking for tgetent                                                                            : not found
Checking for library curses                                                                     : not found
Checking for tgetent                                                                            : not found
Checking for library termcap                                                                    : yes
Checking for tgetent                                                                            : ok
Checking for rl_completion_t                                                                    : not found
Checking for CPPFunction                                                                        : ok
Checking for library readline                                                                   : yes
Checking for rl_completion_matches                                                              : ok
Checking for history_list                                                                       : ok
Checking for MD5Init                                                                            : not found
Checking for MD5Init                                                                            : ok
Checking for CC_MD5_Init                                                                        : not found
Checking for CC_MD5_Init                                                                        : not found
perl manpage generation                                                                         : ok
perl man1 extension                                                                             : 1p
perl man3 extension                                                                             : 3pm
Checking for program yapp                                                                       : not found
Checking for program pod2man                                                                    : /usr/bin/pod2man
Checking linker accepts -Wl,--export-dynamic                                                    : yes
Checking for header libexc.h                                                                    : no
Checking for header libunwind.h                                                                 : no
Checking for header linux/falloc.h                                                              : yes
Checking for getcwd                                                                             : ok
Checking for fchown                                                                             : ok
Checking for chmod                                                                              : ok
Checking for fchmod                                                                             : ok
Checking for mknod                                                                              : ok
Checking for strtol                                                                             : ok
Checking for strchr                                                                             : ok
Checking for strupr                                                                             : not found
Checking for chflags                                                                            : not found
Checking for getrlimit                                                                          : ok
Checking for fsync                                                                              : ok
Checking for fdatasync                                                                          : ok
Checking for setpgid                                                                            : ok
Checking for setsid                                                                             : ok
Checking for glob                                                                               : ok
Checking for strpbrk                                                                            : ok
Checking for crypt16                                                                            : not found
Checking for getauthuid                                                                         : not found
Checking for sigprocmask                                                                        : ok
Checking for sigblock                                                                           : ok
Checking for sigaction                                                                          : ok
Checking for sigset                                                                             : ok
Checking for innetgr                                                                            : ok
Checking for initgroups                                                                         : ok
Checking for select                                                                             : ok
Checking for poll                                                                               : ok
Checking for rdchk                                                                              : not found
Checking for getgrnam                                                                           : ok
Checking for getgrent                                                                           : ok
Checking for pathconf                                                                           : ok
Checking for setpriv                                                                            : not found
Checking for setgidx                                                                            : not found
Checking for setuidx                                                                            : not found
Checking for setgroups                                                                          : ok
Checking for syscall                                                                            : ok
Checking for sysconf                                                                            : ok
Checking for atexit                                                                             : ok
Checking for grantpt                                                                            : ok
Checking for posix_openpt                                                                       : ok
Checking for fallocate                                                                          : ok
Checking for posix_fallocate                                                                    : ok
Checking for fseeko                                                                             : ok
Checking for setluid                                                                            : not found
Checking for getpwnam                                                                           : ok
Checking for fdopendir                                                                          : ok
Checking for getpwent_r                                                                         : ok
Checking for setenv                                                                             : ok
Checking for strcasecmp                                                                         : ok
Checking for fcvt                                                                               : ok
Checking for fcvtl                                                                              : not found
Checking for syslog                                                                             : ok
Checking for vsyslog                                                                            : ok
Checking for timegm                                                                             : ok
Checking for setlocale                                                                          : ok
Checking for nanosleep                                                                          : ok
Checking for lutimes                                                                            : ok
Checking for futimes                                                                            : ok
Checking for utimensat                                                                          : ok
Checking for futimens                                                                           : ok
Checking for mlock                                                                              : ok
Checking for munlock                                                                            : ok
Checking for mlockall                                                                           : ok
Checking for munlockall                                                                         : ok
Checking for memalign                                                                           : ok
Checking for posix_memalign                                                                     : ok
Checking for hstrerror                                                                          : ok
Checking for shmget                                                                             : ok
Checking for shm_open                                                                           : not found
Checking for shm_open                                                                           : ok
Checking for gettext                                                                            : ok
Checking for dgettext                                                                           : ok
Checking for bindtextdomain                                                                     : ok
Checking for textdomain                                                                         : ok
Checking for bind_textdomain_codeset                                                            : ok
Checking for yp_get_default_domain                                                              : ok
Checking for _dn_expand                                                                         : not found
Checking for __dn_expand                                                                        : ok
Checking for declaration of fdatasync                                                           : ok
Checking for declaration of readahead                                                           : ok
Checking for HAVE_LINUX_SPLICE                                                                  : ok
Checking for declaration of splice                                                              : ok
Checking for kernel change notify support                                                       : ok
Checking for Linux kernel oplocks                                                               : ok
Checking for IRIX kernel oplock types                                                           : not found
Checking for kernel share modes                                                                 : ok
Checking for header fam.h                                                                       : no
no suitable FAM library found
Checking for DMAPI library existence
Checking for library dm                                                                         : not found
Checking for dm_get_eventlist                                                                   : not found
Checking for library jfsdm                                                                      : not found
Checking for dm_get_eventlist                                                                   : not found
Checking for library dmapi                                                                      : not found
Checking for dm_get_eventlist                                                                   : not found
Checking for library xdsm                                                                       : not found
Checking for dm_get_eventlist                                                                   : not found
Checking for header sys/dmi.h                                                                   : no
Checking for header xfs/dmapi.h                                                                 : no
Checking for header sys/jfsdmapi.h                                                              : no
Checking for header sys/dmapi.h                                                                 : no
Checking for header dmapi.h                                                                     : no
Checking whether DMAPI lib  can be used                                                         : not found
Checking for member st_blocks in struct stat                                                    : ok
Checking for member st_blksize in struct stat                                                   : ok
Checking for member st_flags in struct stat                                                     : not found
Checking for header replace.h                                                                   : no
Checking whether blkcnt_t is 32 bit                                                             : not found
Checking whether blkcnt_t is 64 bit                                                             : ok
Checking for library cap                                                                        : not found
Checking for cap_get_proc                                                                       : not found
Checking for int16 typedef included by rpc/rpc.h                                                : not found
Checking for uint16 typedef included by rpc/rpc.h                                               : not found
Checking for int32 typedef included by rpc/rpc.h                                                : not found
Checking for uint32 typedef included by rpc/rpc.h                                               : not found
Checking for broken nisplus include files                                                       : ok
Checking if the compiler will optimize out functions                                            : ok
Checking for LL suffix on long long integers                                                    : ok
Checking for _acl                                                                               : not found
Checking for __acl                                                                              : not found
Checking for atexit                                                                             : ok
Checking for bindtextdomain                                                                     : ok
Checking for _chdir                                                                             : not found
Checking for __chdir                                                                            : not found
Checking for chflags                                                                            : not found
Checking for chmod                                                                              : ok
Checking for _close                                                                             : not found
Checking for __close                                                                            : ok
Checking for _closedir                                                                          : not found
Checking for __closedir                                                                         : not found
Checking for crypt16                                                                            : not found
Checking for devnm                                                                              : not found
Checking for dgettext                                                                           : ok
Checking for dirfd                                                                              : ok
Checking for DNSServiceRegister                                                                 : not found
Checking for _dup                                                                               : not found
Checking for __dup                                                                              : not found
Checking for _dup2                                                                              : not found
Checking for __dup2                                                                             : ok
Checking for endmntent                                                                          : ok
Checking for execl                                                                              : ok
Checking for _facl                                                                              : not found
Checking for __facl                                                                             : not found
Checking for _fchdir                                                                            : not found
Checking for __fchdir                                                                           : not found
Checking for fchmod                                                                             : ok
Checking for fchown                                                                             : ok
Checking for _fcntl                                                                             : not found
Checking for __fcntl                                                                            : ok
Checking for fcvt                                                                               : ok
Checking for fcvtl                                                                              : not found
Checking for fdatasync                                                                          : ok
Checking for _fork                                                                              : not found
Checking for __fork                                                                             : ok
Checking for fseeko                                                                             : ok
Checking for fsetxattr                                                                          : ok
Checking for _fstat                                                                             : not found
Checking for __fstat                                                                            : ok
Checking for fsync                                                                              : ok
Checking for futimens                                                                           : ok
Checking for futimes                                                                            : ok
Checking for __fxstat                                                                           : ok
Checking for getauthuid                                                                         : not found
Checking for getcwd                                                                             : ok
Checking for _getcwd                                                                            : not found
Checking for __getcwd                                                                           : not found
Checking for getdents                                                                           : not found
Checking for __getdents                                                                         : not found
Checking for getdirentries                                                                      : ok
Checking for getgrent                                                                           : ok
Checking for getgrnam                                                                           : ok
Checking for getgrouplist                                                                       : ok
Checking for getgrset                                                                           : not found
Checking for getmntent                                                                          : ok
Checking for getpagesize                                                                        : ok
Checking for getpwanam                                                                          : not found
Checking for getpwent_r                                                                         : ok
Checking for getrlimit                                                                          : ok
Checking for gettext                                                                            : ok
Checking for glob                                                                               : ok
Checking for grantpt                                                                            : ok
Checking for hstrerror                                                                          : ok
Checking for initgroups                                                                         : ok
Checking for innetgr                                                                            : ok
Checking for llseek                                                                             : ok
Checking for _llseek                                                                            : not found
Checking for __llseek                                                                           : not found
Checking for _lseek                                                                             : not found
Checking for __lseek                                                                            : ok
Checking for _lstat                                                                             : not found
Checking for __lstat                                                                            : ok
Checking for lutimes                                                                            : ok
Checking for __lxstat                                                                           : ok
Checking for memalign                                                                           : ok
Checking for mknod                                                                              : ok
Checking for mlock                                                                              : ok
Checking for mlockall                                                                           : ok
Checking for munlock                                                                            : ok
Checking for munlockall                                                                         : ok
Checking for _open                                                                              : not found
Checking for __open                                                                             : ok
Checking for _opendir                                                                           : not found
Checking for __opendir                                                                          : not found
Checking for pathconf                                                                           : ok
Checking for poll                                                                               : ok
Checking for posix_fallocate                                                                    : ok
Checking for posix_memalign                                                                     : ok
Checking for prctl                                                                              : ok
Checking for pread                                                                              : ok
Checking for _pread                                                                             : not found
Checking for __pread                                                                            : not found
Checking for pwrite                                                                             : ok
Checking for _pwrite                                                                            : not found
Checking for __pwrite                                                                           : not found
Checking for rdchk                                                                              : not found
Checking for _read                                                                              : not found
Checking for __read                                                                             : ok
Checking for _readdir                                                                           : not found
Checking for __readdir                                                                          : not found
Checking for _seekdir                                                                           : not found
Checking for __seekdir                                                                          : not found
Checking for select                                                                             : ok
Checking for setenv                                                                             : ok
Checking for setgidx                                                                            : not found
Checking for setgroups                                                                          : ok
Checking for setlocale                                                                          : ok
Checking for setluid                                                                            : not found
Checking for setmntent                                                                          : ok
Checking for setpgid                                                                            : ok
Checking for setpriv                                                                            : not found
Checking for setsid                                                                             : ok
Checking for setuidx                                                                            : not found
Checking for shmget                                                                             : ok
Checking for shm_open                                                                           : ok
Checking for sigaction                                                                          : ok
Checking for sigblock                                                                           : ok
Checking for sigprocmask                                                                        : ok
Checking for sigset                                                                             : ok
Checking for _stat                                                                              : not found
Checking for __stat                                                                             : ok
Checking for statvfs                                                                            : ok
Checking for strcasecmp                                                                         : ok
Checking for strchr                                                                             : ok
Checking for strpbrk                                                                            : ok
Checking for strsignal                                                                          : ok
Checking for strtol                                                                             : ok
Checking for strupr                                                                             : not found
Checking for sysconf                                                                            : ok
Checking for sysctl                                                                             : ok
Checking for sysctlbyname                                                                       : not found
Checking for __sys_llseek                                                                       : not found
Checking for syslog                                                                             : ok
Checking for _telldir                                                                           : not found
Checking for __telldir                                                                          : not found
Checking for textdomain                                                                         : ok
Checking for timegm                                                                             : ok
Checking for utimensat                                                                          : ok
Checking for vsyslog                                                                            : ok
Checking for _write                                                                             : not found
Checking for __write                                                                            : ok
Checking for __xstat                                                                            : ok
Checking if can we convert from CP850 to UCS-2LE                                                : ok
Checking if can we convert from UTF-8 to UCS-2LE                                                : ok
building on linux2
Checking for library acl                                                                        : yes
Checking for acl_get_file                                                                       : ok
Checking for POSIX ACL support                                                                  : ok
Checking whether acl_get_perm_np() is available                                                 : not found
Checking for dirfd                                                                              : ok
vfs_fileid: checking for statfs() and struct statfs.f_fsid                                      : ok
Checking whether the Linux 'fallocate' function is available                                    : ok
Checking whether Linux readahead is available                                                   : ok
Checking for declaration of readahead                                                           : ok
Checking for openat                                                                             : ok
Checking for library aio                                                                        : yes
Checking for aio_read                                                                           : not found
Checking for aio_read                                                                           : ok
Checking for asynchronous io support                                                            : ok
Checking for aio_write                                                                          : ok
Checking for aio_fsync                                                                          : ok
Checking for aio_return                                                                         : ok
Checking for aio_error                                                                          : ok
Checking for aio_cancel                                                                         : ok
Checking for aio_suspend                                                                        : ok
Checking for io_submit                                                                          : ok
Checking for header sys/eventfd.h                                                               : yes
Checking for linux kernel asynchronous io support                                               : ok
Checking if we can use msg_control for passing file descriptors                                 : ok
Checking if we can use msg_acctrights for passing file descriptors                              : not found
Checking for program awk                                                                        : /usr/bin/awk
Checking for program perl                                                                       : /usr/bin/perl
Checking for header asm/types.h                                                                 : yes
Checking for major macro                                                                        : ok
Checking for minor macro                                                                        : ok
Checking for member d_off in struct dirent                                                      : ok
Checking for setnetgrent                                                                        : ok
Checking for getnetgrent                                                                        : ok
Checking for endnetgrent                                                                        : ok
Checking compiler accepts -Werror-implicit-function-declaration                                 : yes
Checking for setnetgrent prototype                                                              : ok
Checking for getnetgrent prototype                                                              : ok
Checking for endnetgrent prototype                                                              : ok
Checking for program cups-config                                                                : /usr/bin/cups-config
Checking for /usr/bin/cups-config                                                               : yes
Checking for header cups/cups.h                                                                 : yes
Checking for header cups/language.h                                                             : yes
Checking for library cups                                                                       : yes
Checking for httpConnect                                                                        : ok
Checking for httpConnectEncrypt                                                                 : ok
Checking for header ldap.h                                                                      : yes
Checking for header lber.h                                                                      : yes
Checking for header ldap_pvt.h                                                                  : no
Checking for ber_tag_t                                                                          : ok
Checking for library lber                                                                       : yes
Checking for ber_scanf                                                                          : ok
Checking for ber_sockbuf_add_io                                                                 : ok
Checking for variable LDAP_OPT_SOCKBUF                                                          : ok
Checking for variable LBER_OPT_LOG_PRINT_FN                                                     : ok
Checking for library ldap                                                                       : yes
Checking for ldap_init                                                                          : ok
Checking for ldap_init_fd                                                                       : ok
Checking for ldap_initialize                                                                    : ok
Checking for ldap_set_rebind_proc                                                               : ok
Checking for ldap_add_result_entry                                                              : ok
Checking whether ldap_set_rebind_proc takes 3 arguments                                         : ok
Building with Active Directory support.
Checking for pututline                                                                          : ok
Checking for pututxline                                                                         : ok
Checking for updwtmp                                                                            : ok
Checking for updwtmpx                                                                           : ok
Checking for getutmpx                                                                           : ok
Checking for getutxent                                                                          : ok
Checking for member ut_name in struct utmp                                                      : ok
Checking for member ut_user in struct utmp                                                      : ok
Checking for member ut_id in struct utmp                                                        : ok
Checking for member ut_host in struct utmp                                                      : ok
Checking for member ut_time in struct utmp                                                      : ok
Checking for member ut_tv in struct utmp                                                        : ok
Checking for member ut_type in struct utmp                                                      : ok
Checking for member ut_pid in struct utmp                                                       : ok
Checking for member ut_exit.e_exit in struct utmp                                               : ok
Checking for member ut_syslen in struct utmpx                                                   : not found
Checking whether pututline returns pointer                                                      : ok
Checking size of ((struct utmp *)NULL)->ut_line                                                 : 32
Checking for header avahi-common/watch.h                                                        : yes
Checking for header avahi-client/client.h                                                       : yes
Checking for library avahi-client                                                               : yes
Checking for avahi_client_new                                                                   : ok
Checking for library avahi-common                                                               : yes
Checking for avahi_strerror                                                                     : ok
Checking for header pam/pam_appl.h                                                              : no
Checking for pam_get_data                                                                       : ok
Checking for header security/pam_ext.h                                                          : yes
Checking for header security/_pam_macros.h                                                      : yes
Checking for header pam/pam_ext.h                                                               : no
Checking for header pam/_pam_macros.h                                                           : no
Checking for pam_vsyslog                                                                        : ok
Checking whether PAM_RHOST is available                                                         : ok
Checking whether PAM_TTY is available                                                           : ok
Checking whether PAM_RADIO_TYPE is available                                                    : ok
Checking whether Linux should use 32-bit credential calls                                       : ok
Checking whether we can use Linux thread-specific credentials with 32-bit system calls          : ok
Checking whether Linux netlink is available                                                     : ok
Checking whether Linux rtnetlink is available                                                   : ok
Checking whether fcntl locking is available                                                     : ok
Checking for broken posix_fallocate                                                             : ok
Checking for member st_mtim.tv_nsec in struct stat                                              : ok
Checking for member st_mtimensec in struct stat                                                 : not found
Checking for member st_mtimespec.tv_nsec in struct stat                                         : not found
Checking for member st_mtime_n in struct stat                                                   : not found
Checking for member st_umtime in struct stat                                                    : not found
Checking for member st_birthtime in struct stat                                                 : not found
Checking for member st_birthtimespec.tv_nsec in struct stat                                     : not found
Checking for member st_birthtimensec in struct stat                                             : not found
Checking whether posix_fadvise is available                                                     : ok
Checking whether sysconf(_SC_NGROUPS_MAX) is available                                          : ok
Checking whether sysconf(_SC_NPROC_ONLN) is available                                           : not found
Checking whether sysconf(_SC_NPROCESSORS_ONLN) is available                                     : ok
Checking whether sysconf(_SC_PAGESIZE) is available                                             : ok
Checking whether to use the Darwin-specific initgroups system call                              : not found
Checking whether struct utimbuf is available                                                    : ok
Checking whether we have the struct sigevent                                                    : ok
Checking for member sigev_value.sival_ptr in struct sigevent                                    : ok
Checking for member sigev_value.sigval_ptr in struct sigevent                                   : not found
Checking for the maximum value of the 'time_t' type                                             : not found
Checking whether the macro for makedev is available                                             : ok
Checking whether the realpath function allows a NULL argument                                   : ok
Checking for ftruncate extend                                                                   : ok
Checking for header sys/sendfile.h                                                              : yes
Checking for linux sendfile support                                                             : ok
getcwd takes a NULL argument                                                                    : ok
Checking for library gen                                                                        : not found
Checking for getspnam                                                                           : ok
Checking for header sys/fs/vx_quota.h                                                           : no
Checking for header sys/quota.h                                                                 : yes
Checking for header ufs/ufs/quota.h                                                             : no
Checking for header xfs/xqm.h                                                                   : no
for XFS QUOTA in <sys/quota.h>                                                                  : not found
Checking for member dqb_fsoftlimit in struct dqblk                                              : not found
Checking for member dqb_curbytes in struct dqblk                                                : not found
Checking for header rpcsvc/rquota.h                                                             : yes
Checking for member getquota_rslt_u in struct getquota_rslt                                     : ok
Checking for header ctdb.h                                                                      : not found
building without cluster support: ctdb.h is required for cluster support
Checking whether we can compile with __attribute__((destructor))                                : ok
Checking whether seekdir returns void                                                           : ok
Checking for pthread_attr_init                                                                  : ok
Checking for header gpfs_gpl.h                                                                  : no
Checking linker accepts -Wl,-no-undefined                                                       : yes
Checking linker accepts ['-undefined', 'dynamic_lookup']                                        : no
Checking linker accepts -Wl,--as-needed                                                         : yes
Checking for -lc not needed                                                                     : ok
Checking configure summary                                                                      : ok
Checking compiler for PIE support                                                               : yes
'configure' finished successfully (1m50.340s)
```

---

### Post by TheHammer101 on 2013-10-04
# make
```
WAF_MAKE=1 python ./buildtools/bin/waf build
Waf: Entering directory `/root/samba-4.0.9/bin'
symlink: tevent.py -> python/tevent.py
symlink: samba/__init__.py -> python/samba/__init__.py
symlink: samba/common.py -> python/samba/common.py
symlink: samba/dbchecker.py -> python/samba/dbchecker.py
symlink: samba/descriptor.py -> python/samba/descriptor.py
symlink: samba/drs_utils.py -> python/samba/drs_utils.py
symlink: samba/getopt.py -> python/samba/getopt.py
symlink: samba/hostconfig.py -> python/samba/hostconfig.py
symlink: samba/idmap.py -> python/samba/idmap.py
symlink: samba/join.py -> python/samba/join.py
symlink: samba/kcc_utils.py -> python/samba/kcc_utils.py
symlink: samba/ms_display_specifiers.py -> python/samba/ms_display_specifiers.py
symlink: samba/ms_schema.py -> python/samba/ms_schema.py
symlink: samba/ndr.py -> python/samba/ndr.py
symlink: samba/netcmd/__init__.py -> python/samba/netcmd/__init__.py
symlink: samba/netcmd/common.py -> python/samba/netcmd/common.py
symlink: samba/netcmd/dbcheck.py -> python/samba/netcmd/dbcheck.py
symlink: samba/netcmd/delegation.py -> python/samba/netcmd/delegation.py
symlink: samba/netcmd/dns.py -> python/samba/netcmd/dns.py
symlink: samba/netcmd/domain.py -> python/samba/netcmd/domain.py
symlink: samba/netcmd/drs.py -> python/samba/netcmd/drs.py
symlink: samba/netcmd/dsacl.py -> python/samba/netcmd/dsacl.py
symlink: samba/netcmd/fsmo.py -> python/samba/netcmd/fsmo.py
symlink: samba/netcmd/gpo.py -> python/samba/netcmd/gpo.py
symlink: samba/netcmd/group.py -> python/samba/netcmd/group.py
symlink: samba/netcmd/ldapcmp.py -> python/samba/netcmd/ldapcmp.py
symlink: samba/netcmd/main.py -> python/samba/netcmd/main.py
symlink: samba/netcmd/ntacl.py -> python/samba/netcmd/ntacl.py
symlink: samba/netcmd/processes.py -> python/samba/netcmd/processes.py
symlink: samba/netcmd/rodc.py -> python/samba/netcmd/rodc.py
symlink: samba/netcmd/sites.py -> python/samba/netcmd/sites.py
symlink: samba/netcmd/spn.py -> python/samba/netcmd/spn.py
symlink: samba/netcmd/testparm.py -> python/samba/netcmd/testparm.py
symlink: samba/netcmd/time.py -> python/samba/netcmd/time.py
symlink: samba/netcmd/user.py -> python/samba/netcmd/user.py
symlink: samba/netcmd/vampire.py -> python/samba/netcmd/vampire.py
symlink: samba/ntacls.py -> python/samba/ntacls.py
symlink: samba/provision/__init__.py -> python/samba/provision/__init__.py
symlink: samba/provision/backend.py -> python/samba/provision/backend.py
symlink: samba/provision/common.py -> python/samba/provision/common.py
symlink: samba/provision/sambadns.py -> python/samba/provision/sambadns.py
symlink: samba/samba3/__init__.py -> python/samba/samba3/__init__.py
symlink: samba/samdb.py -> python/samba/samdb.py
symlink: samba/schema.py -> python/samba/schema.py
symlink: samba/sd_utils.py -> python/samba/sd_utils.py
symlink: samba/sites.py -> python/samba/sites.py
symlink: samba/tdb_util.py -> python/samba/tdb_util.py
symlink: samba/tests/__init__.py -> python/samba/tests/__init__.py
symlink: samba/tests/auth.py -> python/samba/tests/auth.py
symlink: samba/tests/blackbox/__init__.py -> python/samba/tests/blackbox/__init__.py
symlink: samba/tests/blackbox/ndrdump.py -> python/samba/tests/blackbox/ndrdump.py
symlink: samba/tests/blackbox/samba_tool_drs.py -> python/samba/tests/blackbox/samba_tool_drs.py
symlink: samba/tests/common.py -> python/samba/tests/common.py
symlink: samba/tests/core.py -> python/samba/tests/core.py
symlink: samba/tests/credentials.py -> python/samba/tests/credentials.py
symlink: samba/tests/dcerpc/__init__.py -> python/samba/tests/dcerpc/__init__.py
symlink: samba/tests/dcerpc/bare.py -> python/samba/tests/dcerpc/bare.py
symlink: samba/tests/dcerpc/dnsserver.py -> python/samba/tests/dcerpc/dnsserver.py
symlink: samba/tests/dcerpc/misc.py -> python/samba/tests/dcerpc/misc.py
symlink: samba/tests/dcerpc/registry.py -> python/samba/tests/dcerpc/registry.py
symlink: samba/tests/dcerpc/rpc_talloc.py -> python/samba/tests/dcerpc/rpc_talloc.py
symlink: samba/tests/dcerpc/rpcecho.py -> python/samba/tests/dcerpc/rpcecho.py
symlink: samba/tests/dcerpc/sam.py -> python/samba/tests/dcerpc/sam.py
symlink: samba/tests/dcerpc/srvsvc.py -> python/samba/tests/dcerpc/srvsvc.py
symlink: samba/tests/dcerpc/testrpc.py -> python/samba/tests/dcerpc/testrpc.py
symlink: samba/tests/dcerpc/unix.py -> python/samba/tests/dcerpc/unix.py
symlink: samba/tests/dns.py -> python/samba/tests/dns.py
symlink: samba/tests/docs.py -> python/samba/tests/docs.py
symlink: samba/tests/dsdb.py -> python/samba/tests/dsdb.py
symlink: samba/tests/gensec.py -> python/samba/tests/gensec.py
symlink: samba/tests/getopt.py -> python/samba/tests/getopt.py
symlink: samba/tests/hostconfig.py -> python/samba/tests/hostconfig.py
symlink: samba/tests/libsmb_samba_internal.py -> python/samba/tests/libsmb_samba_internal.py
symlink: samba/tests/messaging.py -> python/samba/tests/messaging.py
symlink: samba/tests/netcmd.py -> python/samba/tests/netcmd.py
symlink: samba/tests/ntacls.py -> python/samba/tests/ntacls.py
symlink: samba/tests/param.py -> python/samba/tests/param.py
symlink: samba/tests/policy.py -> python/samba/tests/policy.py
symlink: samba/tests/posixacl.py -> python/samba/tests/posixacl.py
symlink: samba/tests/provision.py -> python/samba/tests/provision.py
symlink: samba/tests/registry.py -> python/samba/tests/registry.py
symlink: samba/tests/samba3.py -> python/samba/tests/samba3.py
symlink: samba/tests/samba3sam.py -> python/samba/tests/samba3sam.py
symlink: samba/tests/samba_tool/__init__.py -> python/samba/tests/samba_tool/__init__.py
symlink: samba/tests/samba_tool/base.py -> python/samba/tests/samba_tool/base.py
symlink: samba/tests/samba_tool/gpo.py -> python/samba/tests/samba_tool/gpo.py
symlink: samba/tests/samba_tool/group.py -> python/samba/tests/samba_tool/group.py
symlink: samba/tests/samba_tool/ntacl.py -> python/samba/tests/samba_tool/ntacl.py
symlink: samba/tests/samba_tool/processes.py -> python/samba/tests/samba_tool/processes.py
symlink: samba/tests/samba_tool/timecmd.py -> python/samba/tests/samba_tool/timecmd.py
symlink: samba/tests/samba_tool/user.py -> python/samba/tests/samba_tool/user.py
symlink: samba/tests/samdb.py -> python/samba/tests/samdb.py
symlink: samba/tests/security.py -> python/samba/tests/security.py
symlink: samba/tests/source.py -> python/samba/tests/source.py
symlink: samba/tests/strings.py -> python/samba/tests/strings.py
symlink: samba/tests/unicodenames.py -> python/samba/tests/unicodenames.py
symlink: samba/tests/upgrade.py -> python/samba/tests/upgrade.py
symlink: samba/tests/upgradeprovision.py -> python/samba/tests/upgradeprovision.py
symlink: samba/tests/upgradeprovisionneeddc.py -> python/samba/tests/upgradeprovisionneeddc.py
symlink: samba/tests/xattr.py -> python/samba/tests/xattr.py
symlink: samba/upgrade.py -> python/samba/upgrade.py
symlink: samba/upgradehelpers.py -> python/samba/upgradehelpers.py
symlink: samba/web_server/__init__.py -> python/samba/web_server/__init__.py
symlink: samba/xattr.py -> python/samba/xattr.py
symlink: rpc/dcerpc.py -> python/samba/dcerpc/__init__.py
        Selected embedded Heimdal build
symlink: samba-tool -> ./samba-tool
symlink: samba_dnsupdate -> ./samba_dnsupdate
symlink: samba_spnupdate -> ./samba_spnupdate
symlink: samba_kcc -> ./samba_kcc
symlink: samba_upgradeprovision -> ./samba_upgradeprovision
symlink: samba_upgradedns -> ./samba_upgradedns
Checking project rules ...
Project rules pass
[   1/3781] Generating replace.vscript
[   2/3781] Generating interfaces.vscript
[   3/3781] Generating talloc.vscript
[   4/3781] Generating pytalloc-util.vscript
[   5/3781] Generating tevent.vscript
[   6/3781] Generating addns.vscript
[   7/3781] Generating ccan.vscript
[   8/3781] Generating tdb.vscript
[   9/3781] Generating tdb_compat.vscript
[  10/3781] Generating pyldb-util.vscript
[  11/3781] Generating ldb.vscript
[  12/3781] Generating ldb-cmdline.vscript
[  13/3781] Generating server-role.vscript
[  14/3781] Generating samba-hostconfig.vscript
[  15/3781] Generating samba_python.vscript
[  16/3781] Generating shares.vscript
[  17/3781] Generating ndr-samba4.vscript
[  18/3781] Generating dcerpc-samba4.vscript
[  19/3781] Generating dcerpc-samr.vscript
[  20/3781] Generating dcerpc-atsvc.vscript
[  21/3781] Generating dcerpc.vscript
[  22/3781] Generating dsdb-module.vscript
[  23/3781] Generating samdb.vscript
[  24/3781] Generating samdb-common.vscript
[  25/3781] Generating service.vscript
[  26/3781] Generating process_model.vscript
[  27/3781] Generating cluster.vscript
[  28/3781] Generating samba-net.vscript
[  29/3781] Generating authkrb5.vscript
[  30/3781] Generating auth4.vscript
[  31/3781] Generating auth_unix_token.vscript
[  32/3781] Generating auth_sam_reply.vscript
[  33/3781] Generating gensec.vscript
[  34/3781] Generating samba-credentials.vscript
[  35/3781] Generating winbind-client.vscript
[  36/3781] Generating nss_wrapper_winbind.vscript
[  37/3781] Generating nss_winbind.vscript
[  38/3781] Generating wbclient.vscript
[  39/3781] Generating smbpasswdparser.vscript
[  40/3781] Generating netif.vscript
[  41/3781] Generating ldbsamba.vscript
[  42/3781] Generating registry.vscript
[  43/3781] Generating MESSAGING.vscript
[  44/3781] Generating events.vscript
[  45/3781] Generating cmdline-credentials.vscript
[  46/3781] Generating iniparser.vscript
[  47/3781] Generating samba-util.vscript
[  48/3781] Generating samba-modules.vscript
[  49/3781] Generating asn1util.vscript
[  50/3781] Generating util_tdb.vscript
[  51/3781] Generating tevent-util.vscript
[  52/3781] Generating util_setid.vscript
[  53/3781] Generating tdb-wrap.vscript
[  54/3781] Generating torture.vscript
[  55/3781] Generating dlz_bind9.vscript
[  56/3781] Generating dlz_bind9_9.vscript
[  57/3781] Generating dlz_bind9_for_torture.vscript
[  58/3781] Generating dcerpc_server.vscript
[  59/3781] Generating ntvfs.vscript
[  60/3781] Generating posix_eadb.vscript
[  61/3781] Generating ndr-krb5pac.vscript
[  62/3781] Generating ndr-standard.vscript
[  63/3781] Generating ndr_nbt.vscript
[  64/3781] Generating ndr-samba.vscript
[  65/3781] Generating dcerpc-samba.vscript
[  66/3781] Generating ndr.vscript
[  67/3781] Generating dcerpc-binding.vscript
[  68/3781] Generating cli-ldap.vscript
[  69/3781] Generating LIBWBCLIENT_OLD.vscript
[  70/3781] Generating smbclient-raw.vscript
[  71/3781] Generating smb_transport.vscript
[  72/3781] Generating cli_smb_common.vscript
[  73/3781] Generating errors.vscript
[  74/3781] Generating cli_cldap.vscript
[  75/3781] Generating subunit.vscript
[  76/3781] Generating dbwrap.vscript
[  77/3781] Generating samba-security.vscript
[  78/3781] Generating cli-ldap-common.vscript
[  79/3781] Generating cli-nbt.vscript
[  80/3781] Generating cliauth.vscript
[  81/3781] Generating util_reg.vscript
[  82/3781] Generating samba-policy.vscript
[  83/3781] Generating npa_tstream.vscript
[  84/3781] Generating HDB_SAMBA4.vscript
[  85/3781] Generating pac.vscript
[  86/3781] Generating db-glue.vscript
[  87/3781] Generating samba-sockets.vscript
[  88/3781] Generating flag_mapping.vscript
[  89/3781] Generating netapi.vscript
[  90/3781] Generating smbsharemodes.vscript
[  91/3781] Generating nss_wins.vscript
[  92/3781] Generating gse.vscript
[  93/3781] Generating msrpc3.vscript
[  94/3781] Generating gpo.vscript
[  95/3781] Generating pdb.vscript
[  96/3781] Generating smbldaphelper.vscript
[  97/3781] Generating smbregistry.vscript
[  98/3781] Generating popt_samba3.vscript
[  99/3781] Generating util_cmdline.vscript
[ 100/3781] Generating smbd_shim.vscript
[ 101/3781] Generating libsmb.vscript
[ 102/3781] Generating secrets3.vscript
[ 103/3781] Generating smbldap.vscript
[ 104/3781] Generating ads.vscript
[ 105/3781] Generating smbconf.vscript
[ 106/3781] Generating smbd_conn.vscript
[ 107/3781] Generating smbd_base.vscript
[ 108/3781] Generating printing_migrate.vscript
[ 109/3781] Generating net_keytab.vscript
[ 110/3781] Generating trusts_util.vscript
[ 111/3781] Generating samba3-util.vscript
[ 112/3781] Generating xattr_tdb.vscript
[ 113/3781] Generating CHARSET3.vscript
[ 114/3781] Generating libcli_lsa3.vscript
[ 115/3781] Generating libcli_netlogon3.vscript
[ 116/3781] Generating cli_spoolss.vscript
[ 117/3781] Generating auth.vscript
[ 118/3781] Generating smbclient.vscript
[ 119/3781] Generating idmap.vscript
[ 120/3781] Generating nss_info.vscript
[ 121/3781] Generating dfs_server_ad.vscript
[ 122/3781] Generating krb5samba.vscript
[ 123/3781] Compiling lib/replace/replace.c
[ 124/3781] Compiling lib/replace/getpass.c
[ 125/3781] Linking default/lib/replace/libreplace.so
[ 126/3781] Generating VERSION
[ 127/3781] Generating ldb_version.h
[ 128/3781] Generating param_local_h
[ 129/3781] Generating s3_param_h
[ 130/3781] Generating param_global_h
[ 131/3781] Generating PKGCONFIG_samba-hostconfig.pc
[ 132/3781] Generating PKGCONFIG_dcerpc_samr.pc
[ 133/3781] Generating PKGCONFIG_dcerpc_atsvc.pc
[ 134/3781] Generating PKGCONFIG_dcerpc.pc
[ 135/3781] Generating PKGCONFIG_samdb.pc
[ 136/3781] Generating PKGCONFIG_gensec.pc
[ 137/3781] Generating PKGCONFIG_samba-credentials.pc
[ 138/3781] Generating PKGCONFIG_wbclient.pc
[ 139/3781] Generating PKGCONFIG_registry.pc
[ 140/3781] Generating PKGCONFIG_samba-util.pc
[ 141/3781] Generating PKGCONFIG_torture.pc
[ 142/3781] Generating PKGCONFIG_dcerpc_server.pc
[ 143/3781] Generating PKGCONFIG_ndr_krb5pac.pc
[ 144/3781] Generating PKGCONFIG_ndr_standard.pc
[ 145/3781] Generating PKGCONFIG_ndr_nbt.pc
[ 146/3781] Generating PKGCONFIG_ndr.pc
[ 147/3781] Generating PKGCONFIG_smbclient-raw.pc
[ 148/3781] Generating PKGCONFIG_samba-policy.pc
[ 149/3781] Generating HEIMDAL_ERRORLIST
[ 150/3781] Generating HEIMDAL_NORMALIZE_TABLE
[ 151/3781] Generating HEIMDAL_COMBINING_TABLE
[ 152/3781] Generating HEIMDAL_BIDI_TABLE
[ 153/3781] Generating HEIMDAL_MAP_TABLE
fooresult B.1,rfc4518-map
[ 154/3781] Generating python_samba_dnsupdate
[ 155/3781] Generating python_samba_spnupdate
[ 156/3781] Generating python_samba_upgradedns
[ 157/3781] Generating python_samba_kcc
[ 158/3781] Generating python_samba-tool
[ 159/3781] Generating external_init_py
[ 160/3781] Generating smbd/build_options.c
[ 161/3781] Generating build_env.h
[ 162/3781] Generating PKGCONFIG_netapi.pc
[ 163/3781] Generating PKGCONFIG_smbsharemodes.pc
[ 164/3781] Generating param/param_global_h
[ 165/3781] Generating PKGCONFIG_smbclient.pc
[ 166/3781] Generating INFILE_catalog.xml
[ 167/3781] Generating ../heimdal/lib/asn1/der-protos.h
[ 168/3781] Generating ../heimdal/lib/asn1/der-private.h
[ 169/3781] Compiling lib/replace/replace.c
[ 170/3781] Compiling source4/heimdal/lib/roken/base64.c
[ 171/3781] Compiling source4/heimdal/lib/roken/ct.c
[ 172/3781] Compiling source4/heimdal/lib/roken/hex.c
[ 173/3781] Compiling source4/heimdal/lib/roken/bswap.c
[ 174/3781] Compiling source4/heimdal/lib/roken/dumpdata.c
[ 175/3781] Compiling source4/heimdal/lib/roken/emalloc.c
[ 176/3781] Compiling source4/heimdal/lib/roken/ecalloc.c
[ 177/3781] Compiling source4/heimdal/lib/roken/getarg.c
[ 178/3781] Compiling source4/heimdal/lib/roken/get_window_size.c
[ 179/3781] Compiling source4/heimdal/lib/roken/getdtablesize.c
[ 180/3781] Compiling source4/heimdal/lib/roken/h_errno.c
[ 181/3781] Compiling source4/heimdal/lib/roken/issuid.c
[ 182/3781] Compiling source4/heimdal/lib/roken/net_read.c
[ 183/3781] Compiling source4/heimdal/lib/roken/net_write.c
[ 184/3781] Compiling source4/heimdal/lib/roken/parse_time.c
[ 185/3781] Compiling source4/heimdal/lib/roken/parse_units.c
[ 186/3781] Compiling source4/heimdal/lib/roken/vis.c
[ 187/3781] Compiling source4/heimdal/lib/roken/strlwr.c
[ 188/3781] Compiling source4/heimdal/lib/roken/strsep_copy.c
[ 189/3781] Compiling source4/heimdal/lib/roken/strsep.c
[ 190/3781] Compiling source4/heimdal/lib/roken/strupr.c
[ 191/3781] Compiling source4/heimdal/lib/roken/strpool.c
[ 192/3781] Compiling source4/heimdal/lib/roken/estrdup.c
[ 193/3781] Compiling source4/heimdal/lib/roken/erealloc.c
[ 194/3781] Compiling source4/heimdal/lib/roken/simple_exec.c
[ 195/3781] Compiling source4/heimdal/lib/roken/strcollect.c
[ 196/3781] Compiling source4/heimdal/lib/roken/rtbl.c
[ 197/3781] Compiling source4/heimdal/lib/roken/rand.c
[ 198/3781] Compiling source4/heimdal/lib/roken/cloexec.c
[ 199/3781] Compiling source4/heimdal/lib/roken/xfree.c
[ 200/3781] Compiling source4/heimdal_build/replace.c
[ 201/3781] Compiling source4/heimdal/lib/roken/closefrom.c
[ 202/3781] Compiling source4/heimdal/lib/vers/print_version.c
[ 203/3781] Compiling source4/heimdal_build/version.c
[ 204/3781] Compiling source4/heimdal/lib/vers/print_version.c
[ 205/3781] Compiling source4/heimdal_build/version.c
[ 206/3781] Compiling source4/heimdal/lib/asn1/main.c
[ 207/3781] Compiling source4/heimdal/lib/asn1/gen.c
[ 208/3781] Compiling source4/heimdal/lib/asn1/gen_copy.c
[ 209/3781] Compiling source4/heimdal/lib/asn1/gen_decode.c
[ 210/3781] Compiling source4/heimdal/lib/asn1/gen_encode.c
[ 211/3781] Compiling source4/heimdal/lib/asn1/gen_free.c
[ 212/3781] Compiling source4/heimdal/lib/asn1/gen_glue.c
[ 213/3781] Compiling source4/heimdal/lib/asn1/gen_length.c
[ 214/3781] Compiling source4/heimdal/lib/asn1/gen_seq.c
[ 215/3781] Compiling source4/heimdal/lib/asn1/gen_template.c
[ 216/3781] Compiling source4/heimdal/lib/asn1/hash.c
[ 217/3781] Compiling source4/heimdal/lib/asn1/symbol.c
[ 218/3781] Compiling source4/heimdal/lib/asn1/asn1parse.c
[ 219/3781] Compiling source4/heimdal/lib/asn1/lex.c
[ 220/3781] Compiling source4/heimdal/lib/com_err/parse.c
[ 221/3781] Compiling source4/heimdal/lib/com_err/lex.c
[ 222/3781] Compiling source4/heimdal/lib/com_err/compile_et.c
[ 223/3781] Linking default/source4/heimdal_build/asn1_compile
[ 224/3781] Linking default/source4/heimdal_build/compile_et
[ 225/3781] Compiling ASN1 source4/heimdal/lib/asn1/kx509.asn1
[ 226/3781] Compiling ASN1 source4/heimdal/lib/asn1/digest.asn1
[ 227/3781] Compiling ASN1 source4/heimdal/lib/hdb/hdb.asn1
[ 228/3781] Compiling ASN1 source4/heimdal/lib/gssapi/mech/gssapi.asn1
[ 229/3781] Compiling ASN1 source4/heimdal/lib/gssapi/spnego/spnego.asn1
[ 230/3781] Compiling ASN1 source4/heimdal/lib/asn1/rfc2459.asn1
[ 231/3781] Compiling ASN1 source4/heimdal/lib/asn1/krb5.asn1
[ 232/3781] Compiling ASN1 source4/heimdal/lib/asn1/pkinit.asn1
[ 233/3781] Compiling ASN1 source4/heimdal/lib/asn1/cms.asn1
[ 234/3781] Compiling ASN1 source4/heimdal/lib/hx509/ocsp.asn1
[ 235/3781] Compiling ASN1 source4/heimdal/lib/asn1/pkcs8.asn1
[ 236/3781] Compiling ASN1 source4/heimdal/lib/asn1/pkcs9.asn1
[ 237/3781] Compiling ASN1 source4/heimdal/lib/asn1/pkcs12.asn1
[ 238/3781] Compiling ASN1 source4/heimdal/lib/hx509/pkcs10.asn1
[ 239/3781] Compiling IDL librpc/idl/atsvc.idl
[ 240/3781] Compiling IDL librpc/idl/auth.idl
/root/samba-4.0.9/librpc/idl/auth.idl:112: warning: helper() is pidl-specific and deprecated. Use `include' instead
/root/samba-4.0.9/librpc/idl/auth.idl:104: error: Unable to determine origin of type `struct cli_credentials'
/root/samba-4.0.9/librpc/idl/auth.idl:104: error: Unable to determine origin of type `struct cli_credentials'
[ 241/3781] Compiling IDL librpc/idl/drsuapi.idl
/root/samba-4.0.9/librpc/idl/drsuapi.idl:1824: warning: helper() is pidl-specific and deprecated. Use `include' instead
/root/samba-4.0.9/librpc/idl/drsuapi.idl:147: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/drsuapi.idl:148: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/drsuapi.idl:149: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/drsuapi.idl:150: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/drsuapi.idl:677: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/drsuapi.idl:681: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/drsuapi.idl:689: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/drsuapi.idl:697: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/drsuapi.idl:705: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/drsuapi.idl:713: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
[ 242/3781] Compiling IDL librpc/idl/epmapper.idl
/root/samba-4.0.9/librpc/idl/epmapper.idl:203: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/epmapper.idl:204: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/epmapper.idl:219: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
[ 243/3781] Compiling IDL librpc/idl/initshutdown.idl
[ 244/3781] Compiling IDL librpc/idl/misc.idl
[ 245/3781] Compiling IDL librpc/idl/ntlmssp.idl
/root/samba-4.0.9/librpc/idl/ntlmssp.idl:321: warning: helper() is pidl-specific and deprecated. Use `include' instead
[ 246/3781] Compiling IDL librpc/idl/schannel.idl
/root/samba-4.0.9/librpc/idl/schannel.idl:107: warning: helper() is pidl-specific and deprecated. Use `include' instead
[ 247/3781] Compiling IDL librpc/idl/trkwks.idl
[ 248/3781] Compiling IDL librpc/idl/audiosrv.idl
[ 249/3781] Compiling IDL librpc/idl/dfsblobs.idl
[ 250/3781] Compiling IDL librpc/idl/dsbackup.idl
[ 251/3781] Compiling IDL librpc/idl/eventlog.idl
[ 252/3781] Compiling IDL librpc/idl/file_id.idl
[ 253/3781] Compiling IDL librpc/idl/keysvc.idl
[ 254/3781] Compiling IDL librpc/idl/msgsvc.idl
[ 255/3781] Compiling IDL librpc/idl/ntsvcs.idl
/root/samba-4.0.9/librpc/idl/ntsvcs.idl:264: warning: top-level [out] pointer `unknown5a' is not a [ref] pointer
[ 256/3781] Compiling IDL librpc/idl/remact.idl
[ 257/3781] Compiling IDL librpc/idl/security.idl
/root/samba-4.0.9/librpc/idl/security.idl:576: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
[ 258/3781] Compiling IDL librpc/idl/smb_acl.idl
[ 259/3781] Compiling IDL librpc/idl/unixinfo.idl
[ 260/3781] Compiling IDL librpc/idl/wzcsvc.idl
[ 261/3781] Compiling IDL librpc/idl/browser.idl
[ 262/3781] Compiling IDL librpc/idl/dfs.idl
[ 263/3781] Compiling IDL librpc/idl/dssetup.idl
/root/samba-4.0.9/librpc/idl/dssetup.idl:84: warning: top-level [out] pointer `info' is not a [ref] pointer
[ 264/3781] Compiling IDL librpc/idl/frsapi.idl
[ 265/3781] Compiling IDL librpc/idl/krb5pac.idl
/root/samba-4.0.9/librpc/idl/krb5pac.idl:75: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/krb5pac.idl:80: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
[ 266/3781] Compiling IDL librpc/idl/named_pipe_auth.idl
[ 267/3781] Compiling IDL librpc/idl/orpc.idl
/root/samba-4.0.9/librpc/idl/orpc.idl:214: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
[ 268/3781] Compiling IDL librpc/idl/rot.idl
[ 269/3781] Compiling IDL librpc/idl/spoolss.idl
/root/samba-4.0.9/librpc/idl/spoolss.idl:3207: warning: helper() is pidl-specific and deprecated. Use `include' instead
/root/samba-4.0.9/librpc/idl/spoolss.idl:888: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/spoolss.idl:1094: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/spoolss.idl:1286: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/spoolss.idl:1626: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/spoolss.idl:1650: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/spoolss.idl:1725: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/spoolss.idl:2058: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/spoolss.idl:2409: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/spoolss.idl:861: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:1094: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:1107: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:1286: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:1598: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:1626: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:1650: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:1688: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:1725: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:2058: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:2078: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:2174: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:2216: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:2371: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:2409: warning: top-level [out] pointer `info' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/spoolss.idl:2917: warning: [out] argument `info' not a pointer
[ 270/3781] Compiling IDL librpc/idl/w32time.idl
[ 271/3781] Compiling IDL librpc/idl/xattr.idl
/root/samba-4.0.9/librpc/idl/xattr.idl:198: warning: helper() is pidl-specific and deprecated. Use `include' instead
[ 272/3781] Compiling IDL librpc/idl/dbgidl.idl
[ 273/3781] Compiling IDL librpc/idl/dnsserver.idl
/root/samba-4.0.9/librpc/idl/dnsserver.idl:1530: warning: helper() is pidl-specific and deprecated. Use `include' instead
/root/samba-4.0.9/librpc/idl/dnsserver.idl:1462: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/dnsserver.idl:1518: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
[ 274/3781] Compiling IDL librpc/idl/echo.idl
[ 275/3781] Compiling IDL librpc/idl/frsrpc.idl
/root/samba-4.0.9/librpc/idl/frsrpc.idl:424: warning: helper() is pidl-specific and deprecated. Use `include' instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:19: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:20: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:273: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:277: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:279: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:281: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:293: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:295: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:299: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:301: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:310: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:346: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:385: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:387: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/frsrpc.idl:390: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
[ 276/3781] Compiling IDL librpc/idl/lsa.idl
[ 277/3781] Compiling IDL librpc/idl/nbt.idl
/root/samba-4.0.9/librpc/idl/nbt.idl:680: warning: helper() is pidl-specific and deprecated. Use `include' instead
[ 278/3781] Compiling IDL librpc/idl/dns.idl
/root/samba-4.0.9/librpc/idl/dns.idl:262: warning: helper() is pidl-specific and deprecated. Use `include' instead
[ 279/3781] Compiling IDL librpc/idl/oxidresolver.idl
[ 280/3781] Compiling IDL librpc/idl/samr.idl
[ 281/3781] Compiling IDL librpc/idl/server_id.idl
[ 282/3781] Compiling IDL librpc/idl/srvsvc.idl
/root/samba-4.0.9/librpc/idl/srvsvc.idl:1437: warning: top-level [out] pointer `hnd' is not a [ref] pointer
[ 283/3781] Compiling IDL librpc/idl/winreg.idl
/root/samba-4.0.9/librpc/idl/winreg.idl:191: warning: Got pointer for `size', expected fully derefenced variable
/root/samba-4.0.9/librpc/idl/winreg.idl:191: warning: Got pointer for `length', expected fully derefenced variable
/root/samba-4.0.9/librpc/idl/winreg.idl:191: warning: Got pointer for `size', expected fully derefenced variable
/root/samba-4.0.9/librpc/idl/winreg.idl:191: warning: Got pointer for `length', expected fully derefenced variable
/root/samba-4.0.9/librpc/idl/winreg.idl:191: warning: Got pointer for `length', expected fully derefenced variable
/root/samba-4.0.9/librpc/idl/winreg.idl:191: warning: Got pointer for `length', expected fully derefenced variable
/root/samba-4.0.9/librpc/idl/winreg.idl:268: warning: Got pointer for `data_size', expected fully derefenced variable
/root/samba-4.0.9/librpc/idl/winreg.idl:268: warning: Got pointer for `data_length', expected fully derefenced variable
/root/samba-4.0.9/librpc/idl/winreg.idl:268: warning: Got pointer for `data_size', expected fully derefenced variable
/root/samba-4.0.9/librpc/idl/winreg.idl:268: warning: Got pointer for `data_length', expected fully derefenced variable
/root/samba-4.0.9/librpc/idl/winreg.idl:268: warning: Got pointer for `data_length', expected fully derefenced variable
/root/samba-4.0.9/librpc/idl/winreg.idl:268: warning: Got pointer for `data_length', expected fully derefenced variable
[ 284/3781] Compiling IDL librpc/idl/dcerpc.idl
[ 285/3781] Compiling IDL librpc/idl/drsblobs.idl
/root/samba-4.0.9/librpc/idl/drsblobs.idl:666: warning: helper() is pidl-specific and deprecated. Use `include' instead
/root/samba-4.0.9/librpc/idl/drsblobs.idl:607: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/drsblobs.idl:403: warning: pointless array cntr: 'cntr_service_keys_0': length=0
/root/samba-4.0.9/librpc/idl/drsblobs.idl:403: warning: pointless array `service_keys' will always have size 0
/root/samba-4.0.9/librpc/idl/drsblobs.idl:403: warning: pointless array `service_keys' will always have size 0
[ 286/3781] Compiling IDL librpc/idl/efs.idl
[ 287/3781] Compiling IDL librpc/idl/frstrans.idl
/root/samba-4.0.9/librpc/idl/frstrans.idl:285: warning: frstrans_RawGetFileDataAsync: dcerpc client does not support pipe yet
/root/samba-4.0.9/librpc/idl/frstrans.idl:292: warning: frstrans_RdcGetFileDataAsync: dcerpc client does not support pipe yet
[ 288/3781] Compiling IDL librpc/idl/mgmt.idl
[ 289/3781] Compiling IDL librpc/idl/netlogon.idl
/root/samba-4.0.9/librpc/idl/netlogon.idl:1734: warning: helper() is pidl-specific and deprecated. Use `include' instead
/root/samba-4.0.9/librpc/idl/netlogon.idl:792: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/netlogon.idl:810: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/librpc/idl/netlogon.idl:1054: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
[ 290/3781] Compiling IDL librpc/idl/notify.idl
[ 291/3781] Compiling IDL librpc/idl/policyagent.idl
[ 292/3781] Compiling IDL librpc/idl/scerpc.idl
[ 293/3781] Compiling IDL librpc/idl/svcctl.idl
/root/samba-4.0.9/librpc/idl/svcctl.idl:660: warning: helper() is pidl-specific and deprecated. Use `include' instead
/root/samba-4.0.9/librpc/idl/svcctl.idl:443: warning: top-level [out] pointer `TagId' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/svcctl.idl:454: warning: top-level [out] pointer `service_status' is not a [ref] pointer
[ 294/3781] Compiling IDL librpc/idl/wkssvc.idl
[ 295/3781] Compiling IDL librpc/idl/eventlog6.idl
[ 296/3781] Compiling IDL librpc/idl/backupkey.idl
/root/samba-4.0.9/librpc/idl/backupkey.idl:121: warning: helper() is pidl-specific and deprecated. Use `include' instead
[ 297/3781] Compiling IDL librpc/idl/fsrvp.idl
[ 298/3781] Compiling IDL librpc/idl/wmi.idl
[ 299/3781] Compiling IDL librpc/idl/dcom.idl
/root/samba-4.0.9/librpc/idl/dcom.idl:52: warning: top-level [out] pointer `ppv' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/dcom.idl:91: warning: top-level [out] pointer `ip' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/dcom.idl:104: warning: top-level [out] pointer `pResults' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/dcom.idl:181: warning: top-level [out] pointer `phr' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/dcom.idl:183: warning: top-level [out] pointer `ppMIF' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/dcom.idl:195: warning: top-level [out] pointer `pctinfo' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/dcom.idl:205: warning: top-level [out] pointer `ppTInfo' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/dcom.idl:214: warning: top-level [out] pointer `rgDispId' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/dcom.idl:238: warning: top-level [out] pointer `pVarResult' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/dcom.idl:239: warning: top-level [out] pointer `pExcepInfo' is not a [ref] pointer
/root/samba-4.0.9/librpc/idl/dcom.idl:240: warning: top-level [out] pointer `puArgErr' is not a [ref] pointer
[ 300/3781] Compiling IDL librpc/idl/idmap.idl
[ 301/3781] Compiling IDL librpc/idl/rap.idl
/root/samba-4.0.9/librpc/idl/rap.idl:1076: warning: helper() is pidl-specific and deprecated. Use `include' instead
/root/samba-4.0.9/librpc/idl/rap.idl:348: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:349: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:350: warning: [out] argument `count' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:351: warning: [out] argument `available' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:360: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:362: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:386: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:387: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:388: warning: [out] argument `count' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:389: warning: [out] argument `available' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:396: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:397: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:398: warning: [out] argument `available' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:400: warning: [out] argument `info' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:572: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:573: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:574: warning: [out] argument `count' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:575: warning: [out] argument `available' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:583: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:584: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:585: warning: [out] argument `available' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:587: warning: [out] argument `info' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:591: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:593: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:597: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:599: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:603: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:605: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:610: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:612: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:617: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:619: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:624: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:626: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:633: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:634: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:635: warning: [out] argument `count' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:636: warning: [out] argument `available' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:644: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:645: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:646: warning: [out] argument `available' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:648: warning: [out] argument `info' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:684: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:686: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:739: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:740: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:741: warning: [out] argument `count' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:742: warning: [out] argument `available' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:751: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:752: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:753: warning: [out] argument `available' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:755: warning: [out] argument `info' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:763: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:765: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:772: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:774: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:904: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:905: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:906: warning: [out] argument `available' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:908: warning: [out] argument `info' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:933: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:934: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:935: warning: [out] argument `count' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:936: warning: [out] argument `available' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:945: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:946: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:947: warning: [out] argument `available' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:949: warning: [out] argument `info' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:958: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:960: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:965: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:967: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:986: warning: [out] argument `status' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:987: warning: [out] argument `convert' not a pointer
/root/samba-4.0.9/librpc/idl/rap.idl:989: warning: [out] argument `tod' not a pointer
[ 302/3781] Compiling IDL librpc/idl/ntprinting.idl
/root/samba-4.0.9/librpc/idl/ntprinting.idl:168: warning: helper() is pidl-specific and deprecated. Use `include' instead
[ 303/3781] Compiling IDL librpc/idl/preg.idl
/root/samba-4.0.9/librpc/idl/preg.idl:50: warning: helper() is pidl-specific and deprecated. Use `include' instead
[ 304/3781] Compiling IDL librpc/idl/ioctl.idl
[ 305/3781] Compiling IDL librpc/idl/printcap.idl
[ 306/3781] Compiling IDL librpc/idl/dnsp.idl
/root/samba-4.0.9/librpc/idl/dnsp.idl:274: warning: helper() is pidl-specific and deprecated. Use `include' instead
[ 307/3781] Compiling IDL source4/librpc/idl/irpc.idl
/root/samba-4.0.9/source4/librpc/idl/irpc.idl:28: warning: subcontext() is deprecated. Use represent_as() or transmit_as() instead
/root/samba-4.0.9/source4/librpc/idl/irpc.idl:70: warning: [out] argument `info' not a pointer
/root/samba-4.0.9/source4/librpc/idl/irpc.idl:83: warning: top-level [out] pointer `dcname' is not a [ref] pointer
/root/samba-4.0.9/source4/librpc/idl/irpc.idl:91: warning: [out] argument `num_addrs' not a pointer
/root/samba-4.0.9/source4/librpc/idl/irpc.idl:113: warning: [out] argument `generic_reply' not a pointer
/root/samba-4.0.9/source4/librpc/idl/irpc.idl:159: warning: [out] argument `info' not a pointer
/root/samba-4.0.9/source4/librpc/idl/irpc.idl:70: error: nbtd_information: [out] argument 'info' is not a pointer or array, skip client functions
/root/samba-4.0.9/source4/librpc/idl/irpc.idl:83: error: nbtd_getdcname: [out] argument 'dcname' is a pointer to type 'string', skip client functions
/root/samba-4.0.9/source4/librpc/idl/irpc.idl:91: error: nbtd_proxy_wins_challenge: [out] argument 'num_addrs' is not a pointer or array, skip client functions
/root/samba-4.0.9/source4/librpc/idl/irpc.idl:113: error: kdc_check_generic_kerberos: [out] argument 'generic_reply' is not a pointer or array, skip client functions
/root/samba-4.0.9/source4/librpc/idl/irpc.idl:159: error: smbsrv_information: [out] argument 'info' is not a pointer or array, skip client functions
[ 308/3781] Compiling IDL source4/librpc/idl/nfs4acl.idl
[ 309/3781] Compiling IDL source4/librpc/idl/ntp_signd.idl
[ 310/3781] Compiling IDL source4/librpc/idl/opendb.idl
[ 311/3781] Compiling IDL source4/librpc/idl/sasl_helpers.idl
[ 312/3781] Compiling IDL source4/librpc/idl/winbind.idl
/root/samba-4.0.9/source4/librpc/idl/winbind.idl:35: warning: [out] argument `validation' not a pointer
/root/samba-4.0.9/source4/librpc/idl/winbind.idl:37: warning: [out] argument `authoritative' not a pointer
/root/samba-4.0.9/source4/librpc/idl/winbind.idl:35: error: winbind_SamLogon: [out] argument 'validation' is not a pointer or array, skip client functions
[ 313/3781] Compiling IDL source4/librpc/idl/winsif.idl
/root/samba-4.0.9/source4/librpc/idl/winsif.idl:343: warning: helper() is pidl-specific and deprecated. Use `include' instead
/root/samba-4.0.9/source4/librpc/idl/winsif.idl:243: warning: [out] argument `unc_name' not a pointer
[ 314/3781] Compiling IDL source4/librpc/idl/winsrepl.idl
/root/samba-4.0.9/source4/librpc/idl/winsrepl.idl:180: warning: helper() is pidl-specific and deprecated. Use `include' instead
[ 315/3781] Compiling IDL source4/librpc/idl/winstation.idl
[ 316/3781] Compiling IDL source4/lib/registry/regf.idl
[ 317/3781] Compiling ERRTABLE source4/heimdal/lib/ntlm/ntlm_err.et
[ 318/3781] Compiling ERRTABLE source4/heimdal/lib/hdb/hdb_err.et
[ 319/3781] Compiling ERRTABLE source4/heimdal/lib/gssapi/krb5/gkrb5_err.et
[ 320/3781] Compiling ERRTABLE source4/heimdal/lib/krb5/krb5_err.et
[ 321/3781] Compiling ERRTABLE source4/heimdal/lib/krb5/krb_err.et
[ 322/3781] Compiling ERRTABLE source4/heimdal/lib/krb5/k524_err.et
[ 323/3781] Compiling ERRTABLE source4/heimdal/lib/krb5/heim_err.et
[ 324/3781] Compiling ERRTABLE source4/heimdal/lib/asn1/asn1_err.et
[ 325/3781] Compiling ERRTABLE source4/heimdal/lib/hx509/hx509_err.et
[ 326/3781] Compiling ERRTABLE source4/heimdal/lib/wind/wind_err.et
[ 327/3781] Compiling IDL source3/librpc/idl/messaging.idl
[ 328/3781] Compiling IDL source3/librpc/idl/libnetapi.idl
[ 329/3781] Compiling IDL source3/librpc/idl/open_files.idl
[ 330/3781] Compiling IDL source3/librpc/idl/perfcount.idl
[ 331/3781] Compiling IDL source3/librpc/idl/secrets.idl
[ 332/3781] Compiling IDL source3/librpc/idl/libnet_join.idl
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:73: warning: helper() is pidl-specific and deprecated. Use `include' instead
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:37: warning: [out] argument `account_name' not a pointer
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:38: warning: [out] argument `netbios_domain_name' not a pointer
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:39: warning: [out] argument `dns_domain_name' not a pointer
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:40: warning: [out] argument `forest_name' not a pointer
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:41: warning: [out] argument `dn' not a pointer
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:43: warning: [out] argument `modified_config' not a pointer
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:44: warning: [out] argument `error_string' not a pointer
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:46: warning: [out] argument `domain_is_ad' not a pointer
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:64: warning: [out] argument `netbios_domain_name' not a pointer
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:65: warning: [out] argument `dns_domain_name' not a pointer
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:66: warning: [out] argument `forest_name' not a pointer
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:67: warning: [out] argument `modified_config' not a pointer
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:68: warning: [out] argument `error_string' not a pointer
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:69: warning: [out] argument `disabled_machine_account' not a pointer
/root/samba-4.0.9/source3/librpc/idl/libnet_join.idl:71: warning: [out] argument `deleted_machine_account' not a pointer
[ 333/3781] Compiling IDL source3/librpc/idl/smbXsrv.idl
[ 334/3781] Compiling IDL source3/librpc/idl/wbint.idl
[ 335/3781] HEIMDAL_KX509_ASN1_C: bin/default/source4/heimdal/lib/asn1/asn1_kx509_asn1.x -> bin/default/source4/heimdal/lib/asn1/asn1_kx509_asn1.c
[ 336/3781] HEIMDAL_KX509_ASN1_H: bin/default/source4/heimdal/lib/asn1/kx509_asn1.hx -> bin/default/source4/heimdal/lib/asn1/kx509_asn1.h
[ 337/3781] HEIMDAL_KX509_ASN1_PRIV_H: bin/default/source4/heimdal/lib/asn1/kx509_asn1-priv.hx -> bin/default/source4/heimdal/lib/asn1/kx509_asn1-priv.h
[ 338/3781] HEIMDAL_DIGEST_ASN1_C: bin/default/source4/heimdal/lib/asn1/asn1_digest_asn1.x -> bin/default/source4/heimdal/lib/asn1/asn1_digest_asn1.c
[ 339/3781] HEIMDAL_DIGEST_ASN1_H: bin/default/source4/heimdal/lib/asn1/digest_asn1.hx -> bin/default/source4/heimdal/lib/asn1/digest_asn1.h
[ 340/3781] HEIMDAL_DIGEST_ASN1_PRIV_H: bin/default/source4/heimdal/lib/asn1/digest_asn1-priv.hx -> bin/default/source4/heimdal/lib/asn1/digest_asn1-priv.h
[ 341/3781] HEIMDAL_HDB_ASN1_C: bin/default/source4/heimdal/lib/asn1/asn1_hdb_asn1.x -> bin/default/source4/heimdal/lib/asn1/asn1_hdb_asn1.c
[ 342/3781] HEIMDAL_HDB_ASN1_H: bin/default/source4/heimdal/lib/asn1/hdb_asn1.hx -> bin/default/source4/heimdal/lib/asn1/hdb_asn1.h
[ 343/3781] HEIMDAL_HDB_ASN1_PRIV_H: bin/default/source4/heimdal/lib/asn1/hdb_asn1-priv.hx -> bin/default/source4/heimdal/lib/asn1/hdb_asn1-priv.h
[ 344/3781] HEIMDAL_GSSAPI_ASN1_C: bin/default/source4/heimdal/lib/gssapi/asn1_gssapi_asn1.x -> bin/default/source4/heimdal/lib/gssapi/asn1_gssapi_asn1.c
[ 345/3781] HEIMDAL_GSSAPI_ASN1_H: bin/default/source4/heimdal/lib/gssapi/gssapi_asn1.hx -> bin/default/source4/heimdal/lib/gssapi/gssapi_asn1.h
[ 346/3781] HEIMDAL_GSSAPI_ASN1_PRIV_H: bin/default/source4/heimdal/lib/gssapi/gssapi_asn1-priv.hx -> bin/default/source4/heimdal/lib/gssapi/gssapi_asn1-priv.h
[ 347/3781] HEIMDAL_SPNEGO_ASN1_C: bin/default/source4/heimdal/lib/gssapi/asn1_spnego_asn1.x -> bin/default/source4/heimdal/lib/gssapi/asn1_spnego_asn1.c
[ 348/3781] HEIMDAL_SPNEGO_ASN1_H: bin/default/source4/heimdal/lib/gssapi/spnego_asn1.hx -> bin/default/source4/heimdal/lib/gssapi/spnego_asn1.h
[ 349/3781] HEIMDAL_SPNEGO_ASN1_PRIV_H: bin/default/source4/heimdal/lib/gssapi/spnego_asn1-priv.hx -> bin/default/source4/heimdal/lib/gssapi/spnego_asn1-priv.h
[ 350/3781] HEIMDAL_RFC2459_ASN1_C: bin/default/source4/heimdal/lib/asn1/asn1_rfc2459_asn1.x -> bin/default/source4/heimdal/lib/asn1/asn1_rfc2459_asn1.c
[ 351/3781] HEIMDAL_RFC2459_ASN1_H: bin/default/source4/heimdal/lib/asn1/rfc2459_asn1.hx -> bin/default/source4/heimdal/lib/asn1/rfc2459_asn1.h
[ 352/3781] HEIMDAL_RFC2459_ASN1_PRIV_H: bin/default/source4/heimdal/lib/asn1/rfc2459_asn1-priv.hx -> bin/default/source4/heimdal/lib/asn1/rfc2459_asn1-priv.h
[ 353/3781] HEIMDAL_KRB5_ASN1_C: bin/default/source4/heimdal/lib/asn1/asn1_krb5_asn1.x -> bin/default/source4/heimdal/lib/asn1/asn1_krb5_asn1.c
[ 354/3781] HEIMDAL_KRB5_ASN1_H: bin/default/source4/heimdal/lib/asn1/krb5_asn1.hx -> bin/default/source4/heimdal/lib/asn1/krb5_asn1.h
[ 355/3781] HEIMDAL_KRB5_ASN1_PRIV_H: bin/default/source4/heimdal/lib/asn1/krb5_asn1-priv.hx -> bin/default/source4/heimdal/lib/asn1/krb5_asn1-priv.h
[ 356/3781] HEIMDAL_PKINIT_ASN1_C: bin/default/source4/heimdal/lib/asn1/asn1_pkinit_asn1.x -> bin/default/source4/heimdal/lib/asn1/asn1_pkinit_asn1.c
[ 357/3781] HEIMDAL_PKINIT_ASN1_H: bin/default/source4/heimdal/lib/asn1/pkinit_asn1.hx -> bin/default/source4/heimdal/lib/asn1/pkinit_asn1.h
[ 358/3781] HEIMDAL_PKINIT_ASN1_PRIV_H: bin/default/source4/heimdal/lib/asn1/pkinit_asn1-priv.hx -> bin/default/source4/heimdal/lib/asn1/pkinit_asn1-priv.h
[ 359/3781] HEIMDAL_CMS_ASN1_C: bin/default/source4/heimdal/lib/asn1/asn1_cms_asn1.x -> bin/default/source4/heimdal/lib/asn1/asn1_cms_asn1.c
[ 360/3781] HEIMDAL_CMS_ASN1_H: bin/default/source4/heimdal/lib/asn1/cms_asn1.hx -> bin/default/source4/heimdal/lib/asn1/cms_asn1.h
[ 361/3781] HEIMDAL_CMS_ASN1_PRIV_H: bin/default/source4/heimdal/lib/asn1/cms_asn1-priv.hx -> bin/default/source4/heimdal/lib/asn1/cms_asn1-priv.h
[ 362/3781] HEIMDAL_OCSP_ASN1_C: bin/default/source4/heimdal/lib/hx509/asn1_ocsp_asn1.x -> bin/default/source4/heimdal/lib/hx509/asn1_ocsp_asn1.c
[ 363/3781] HEIMDAL_OCSP_ASN1_H: bin/default/source4/heimdal/lib/hx509/ocsp_asn1.hx -> bin/default/source4/heimdal/lib/hx509/ocsp_asn1.h
[ 364/3781] HEIMDAL_OCSP_ASN1_PRIV_H: bin/default/source4/heimdal/lib/hx509/ocsp_asn1-priv.hx -> bin/default/source4/heimdal/lib/hx509/ocsp_asn1-priv.h
[ 365/3781] HEIMDAL_PKCS8_ASN1_C: bin/default/source4/heimdal/lib/asn1/asn1_pkcs8_asn1.x -> bin/default/source4/heimdal/lib/asn1/asn1_pkcs8_asn1.c
[ 366/3781] HEIMDAL_PKCS8_ASN1_H: bin/default/source4/heimdal/lib/asn1/pkcs8_asn1.hx -> bin/default/source4/heimdal/lib/asn1/pkcs8_asn1.h
[ 367/3781] HEIMDAL_PKCS8_ASN1_PRIV_H: bin/default/source4/heimdal/lib/asn1/pkcs8_asn1-priv.hx -> bin/default/source4/heimdal/lib/asn1/pkcs8_asn1-priv.h
[ 368/3781] HEIMDAL_PKCS9_ASN1_C: bin/default/source4/heimdal/lib/asn1/asn1_pkcs9_asn1.x -> bin/default/source4/heimdal/lib/asn1/asn1_pkcs9_asn1.c
[ 369/3781] HEIMDAL_PKCS9_ASN1_H: bin/default/source4/heimdal/lib/asn1/pkcs9_asn1.hx -> bin/default/source4/heimdal/lib/asn1/pkcs9_asn1.h
[ 370/3781] HEIMDAL_PKCS9_ASN1_PRIV_H: bin/default/source4/heimdal/lib/asn1/pkcs9_asn1-priv.hx -> bin/default/source4/heimdal/lib/asn1/pkcs9_asn1-priv.h
[ 371/3781] HEIMDAL_PKCS12_ASN1_C: bin/default/source4/heimdal/lib/asn1/asn1_pkcs12_asn1.x -> bin/default/source4/heimdal/lib/asn1/asn1_pkcs12_asn1.c
[ 372/3781] HEIMDAL_PKCS12_ASN1_H: bin/default/source4/heimdal/lib/asn1/pkcs12_asn1.hx -> bin/default/source4/heimdal/lib/asn1/pkcs12_asn1.h
[ 373/3781] HEIMDAL_PKCS12_ASN1_PRIV_H: bin/default/source4/heimdal/lib/asn1/pkcs12_asn1-priv.hx -> bin/default/source4/heimdal/lib/asn1/pkcs12_asn1-priv.h
[ 374/3781] HEIMDAL_PKCS10_ASN1_C: bin/default/source4/heimdal/lib/hx509/asn1_pkcs10_asn1.x -> bin/default/source4/heimdal/lib/hx509/asn1_pkcs10_asn1.c
[ 375/3781] HEIMDAL_PKCS10_ASN1_H: bin/default/source4/heimdal/lib/hx509/pkcs10_asn1.hx -> bin/default/source4/heimdal/lib/hx509/pkcs10_asn1.h
[ 376/3781] HEIMDAL_PKCS10_ASN1_PRIV_H: bin/default/source4/heimdal/lib/hx509/pkcs10_asn1-priv.hx -> bin/default/source4/heimdal/lib/hx509/pkcs10_asn1-priv.h
[ 377/3781] Generating lib/param/param_proto.h
[ 378/3781] Generating source4/librpc/rpc/dcerpc_proto.h
[ 379/3781] Generating source4/dsdb/samdb/ldb_modules/util_proto.h
[ 380/3781] Generating source4/dsdb/samdb/ldb_modules/ridalloc.h
[ 381/3781] Generating source4/dsdb/samdb/ldb_modules/partition_proto.h
[ 382/3781] Generating source4/dsdb/samdb/samdb_proto.h
[ 383/3781] Generating source4/dsdb/common/proto.h
[ 384/3781] Generating source4/dsdb/schema/proto.h
[ 385/3781] Generating source4/dsdb/repl/drepl_service_proto.h
[ 386/3781] Generating source4/dsdb/kcc/kcc_service_proto.h
[ 387/3781] Generating source4/smbd/service_proto.h
[ 388/3781] Generating source4/smbd/process_model_proto.h
[ 389/3781] Generating source4/libnet/libnet_proto.h
[ 390/3781] Generating source4/auth/gensec/gensec_proto.h
[ 391/3781] Generating source4/auth/gensec/schannel_proto.h
[ 392/3781] Generating source4/auth/kerberos/proto.h
[ 393/3781] Generating source4/auth/kerberos/kerberos_util.h
[ 394/3781] Generating source4/auth/kerberos/kerberos_srv_keytab.h
[ 395/3781] Generating source4/auth/ntlm/auth_proto.h
[ 396/3781] Generating source4/auth/session_proto.h
[ 397/3781] Generating source4/auth/unix_token_proto.h
[ 398/3781] Generating source4/auth/system_session_proto.h
[ 399/3781] Generating source4/auth/auth_sam.h
[ 400/3781] Generating auth/auth_sam_reply.h
[ 401/3781] Generating auth/gensec/gensec_toplevel_proto.h
[ 402/3781] Generating auth/gensec/spnego_proto.h
[ 403/3781] Generating auth/credentials/credentials_proto.h
[ 404/3781] Generating source4/lib/socket/netif_proto.h
[ 405/3781] Generating lib/ldb-samba/ldif_handlers_proto.h
[ 406/3781] Generating source4/lib/registry/tools/common.h
[ 407/3781] Generating source4/lib/registry/tests/proto.h
[ 408/3781] Generating source4/lib/cmdline/credentials.h
[ 409/3781] Generating source4/lib/cmdline/popt_credentials.h
[ 410/3781] Generating lib/util/unix_privs.h
[ 411/3781] Generating lib/crypto/test_proto.h
[ 412/3781] Generating source4/smb_server/service_smb_proto.h
[ 413/3781] Generating source4/smb_server/smb_server_proto.h
[ 414/3781] Generating source4/smb_server/smb/smb_proto.h
[ 415/3781] Generating source4/smb_server/smb2/smb2_proto.h
[ 416/3781] Generating source4/rpc_server/common/share.h
[ 417/3781] Generating source4/rpc_server/common/proto.h
[ 418/3781] Generating source4/rpc_server/dcerpc_server_proto.h
[ 419/3781] Generating source4/rpc_server/srvsvc/proto.h
[ 420/3781] Generating source4/rpc_server/samr/proto.h
[ 421/3781] Generating source4/rpc_server/lsa/proto.h
[ 422/3781] Generating source4/rpc_server/backupkey/proto.h
[ 423/3781] Generating source4/rpc_server/service_rpc.h
[ 424/3781] Generating source4/ldap_server/proto.h
[ 425/3781] Generating source4/winbind/wb_proto.h
[ 426/3781] Generating source4/winbind/wb_helper.h
[ 427/3781] Generating source4/winbind/idmap_proto.h
[ 428/3781] Generating source4/nbt_server/wins/winsdb_proto.h
[ 429/3781] Generating source4/nbt_server/wins/winsserver_proto.h
[ 430/3781] Generating source4/nbt_server/dgram/proto.h
[ 431/3781] Generating source4/nbt_server/nbt_server_proto.h
[ 432/3781] Generating source4/wrepl_server/wrepl_server_proto.h
[ 433/3781] Generating source4/cldap_server/proto.h
[ 434/3781] Generating source4/ntvfs/ntvfs_proto.h
[ 435/3781] Generating source4/ntvfs/posix/vfs_acl_proto.h
[ 436/3781] Generating source4/ntvfs/posix/vfs_posix_proto.h
[ 437/3781] Generating source4/ntvfs/posix/posix_eadb_proto.h
[ 438/3781] Generating source4/ntvfs/common/proto.h
[ 439/3781] Generating source4/ntvfs/simple/proto.h
[ 440/3781] Generating source4/ntvfs/cifs_posix_cli/proto.h
[ 441/3781] Generating source4/ntvfs/ipc/proto.h
[ 442/3781] Generating source4/ntptr/ntptr_proto.h
[ 443/3781] Generating source4/torture/basic/proto.h
[ 444/3781] Generating source4/torture/raw/proto.h
[ 445/3781] Generating source4/torture/smb2/proto.h
[ 446/3781] Generating source4/torture/winbind/proto.h
[ 447/3781] Generating source4/torture/libnetapi/proto.h
[ 448/3781] Generating source4/torture/libsmbclient/proto.h
[ 449/3781] Generating source4/torture/ndr/proto.h
[ 450/3781] Generating source4/torture/rpc/proto.h
[ 451/3781] Generating source4/torture/drs/proto.h
[ 452/3781] Generating source4/torture/rap/proto.h
[ 453/3781] Generating source4/torture/dfs/proto.h
[ 454/3781] Generating source4/torture/auth/proto.h
[ 455/3781] Generating source4/torture/local/proto.h
[ 456/3781] Generating source4/torture/nbench/proto.h
[ 457/3781] Generating source4/torture/unix/proto.h
[ 458/3781] Generating source4/torture/ldap/proto.h
[ 459/3781] Generating source4/torture/nbt/proto.h
[ 460/3781] Generating source4/torture/libnet/proto.h
[ 461/3781] Generating source4/torture/ntp/proto.h
[ 462/3781] Generating source4/libcli/ldap/ldap_proto.h
[ 463/3781] Generating source4/libcli/util/clilsa.h
[ 464/3781] Generating source4/libcli/composite/proto.h
[ 465/3781] Generating source4/libcli/wrepl/winsrepl_proto.h
[ 466/3781] Generating source4/libcli/resolve/proto.h
[ 467/3781] Generating source4/libcli/resolve/lp_proto.h
[ 468/3781] Generating source4/libcli/finddcs_proto.h
[ 469/3781] Generating source4/libcli/raw/raw_proto.h
[ 470/3781] Generating source4/libcli/smb2/smb2_proto.h
[ 471/3781] Generating source4/libcli/rap/proto.h
[ 472/3781] Generating libcli/nbt/nbtname.h
[ 473/3781] Generating ../heimdal/kdc/kdc-protos.h
[ 474/3781] Generating ../heimdal/kdc/kdc-private.h
[ 475/3781] Generating ../heimdal/lib/ntlm/heimntlm-protos.h
[ 476/3781] Generating ../heimdal/lib/hdb/hdb-protos.h
[ 477/3781] Generating ../heimdal/lib/hdb/hdb-private.h
[ 478/3781] Generating ../heimdal/lib/gssapi/spnego/spnego-private.h
[ 479/3781] Generating ../heimdal/lib/gssapi/krb5/gsskrb5-private.h
[ 480/3781] Generating ../heimdal/lib/krb5/krb5-private.h
[ 481/3781] Generating ../heimdal/lib/krb5/krb5-protos.h
[ 482/3781] Generating ../heimdal/lib/hx509/hx509-protos.h
[ 483/3781] Generating ../heimdal/lib/hx509/hx509-private.h
[ 484/3781] Generating file_server/file_server_proto.h
[ 485/3781] Generating HEADER_lib/talloc//talloc.h
[ 486/3781] Generating HEADER_lib/talloc//pytalloc.h
[ 487/3781] Generating HEADER_lib/tevent//tevent.h
[ 488/3781] Generating HEADER_lib/tdb//tdb.h
[ 489/3781] Generating HEADER_lib/ldb//pyldb.h
[ 490/3781] Generating HEADER_lib/ldb//ldb.h
[ 491/3781] Generating HEADER_lib/ldb//ldb_errors.h
[ 492/3781] Generating HEADER_lib/ldb//ldb_module.h
[ 493/3781] Generating HEADER_lib/ldb//ldb_handlers.h
[ 494/3781] Generating HEADER_lib/ldb//ldb_version.h
[ 495/3781] Generating HEADER_lib/param//param.h
[ 496/3781] Generating HEADER_dynconfig/samba/version.h
[ 497/3781] Generating HEADER_lib/util/charset//charset.h
[ 498/3781] Generating HEADER_source4/param//share.h
[ 499/3781] Generating HEADER_source4/librpc/gen_ndr/ndr_samr_c.h
[ 500/3781] Generating HEADER_source4/librpc/gen_ndr/ndr_atsvc_c.h
[ 501/3781] Generating HEADER_source4/librpc//dcerpc.h
[ 502/3781] Generating HEADER_source4/librpc/gen_ndr/mgmt.h
[ 503/3781] Generating HEADER_source4/librpc/gen_ndr/ndr_mgmt.h
[ 504/3781] Generating HEADER_source4/librpc/gen_ndr/ndr_mgmt_c.h
[ 505/3781] Generating HEADER_source4/librpc/gen_ndr/epmapper.h
[ 506/3781] Generating HEADER_source4/librpc/gen_ndr/ndr_epmapper.h
[ 507/3781] Generating HEADER_source4/librpc/gen_ndr/ndr_epmapper_c.h
[ 508/3781] Generating HEADER_source4/auth/samba/session.h
[ 509/3781] Generating HEADER_auth/gensec//gensec.h
[ 510/3781] Generating HEADER_auth/credentials//credentials.h
[ 511/3781] Generating HEADER_nsswitch/libwbclient//wbclient.h
[ 512/3781] Generating HEADER_lib/ldb-samba//ldb_wrap.h
[ 513/3781] Generating HEADER_source4/lib/registry//registry.h
[ 514/3781] Generating HEADER_lib/util/util/debug.h
[ 515/3781] Generating HEADER_lib/util/util/attr.h
[ 516/3781] Generating HEADER_lib/util/util/byteorder.h
[ 517/3781] Generating HEADER_lib/util/util/data_blob.h
[ 518/3781] Generating HEADER_lib/util/util/memory.h
[ 519/3781] Generating HEADER_lib/util/util/safe_string.h
[ 520/3781] Generating HEADER_lib/util/util/time.h
[ 521/3781] Generating HEADER_lib/util/util/talloc_stack.h
[ 522/3781] Generating HEADER_lib/util/util/xfile.h
[ 523/3781] Generating HEADER_lib/util/./dlinklist.h
[ 524/3781] Generating HEADER_lib/util/./samba_util.h
[ 525/3781] Generating HEADER_lib/util/util/string_wrappers.h
[ 526/3781] Generating HEADER_lib/util/util/tevent_ntstatus.h
[ 527/3781] Generating HEADER_lib/util/util/tevent_unix.h
[ 528/3781] Generating HEADER_lib/util/util/tevent_werror.h
[ 529/3781] Generating HEADER_lib/util//util_ldb.h
[ 530/3781] Generating HEADER_lib/tdr//tdr.h
[ 531/3781] Generating HEADER_lib/tsocket//tsocket.h
[ 532/3781] Generating HEADER_lib/tsocket//tsocket_internal.h
[ 533/3781] Generating HEADER_lib/torture//torture.h
[ 534/3781] Generating HEADER_source4/rpc_server//dcerpc_server.h
[ 535/3781] Generating HEADER_librpc/gen_ndr/auth.h
[ 536/3781] Generating HEADER_librpc/gen_ndr/server_id.h
[ 537/3781] Generating HEADER_librpc/gen_ndr/security.h
[ 538/3781] Generating HEADER_librpc/gen_ndr/ndr_dcerpc.h
[ 539/3781] Generating HEADER_librpc/gen_ndr/dcerpc.h
[ 540/3781] Generating HEADER_librpc/gen_ndr/ndr_drsuapi.h
[ 541/3781] Generating HEADER_librpc/gen_ndr/drsuapi.h
[ 542/3781] Generating HEADER_librpc/ndr/ndr_drsuapi.h
[ 543/3781] Generating HEADER_librpc/gen_ndr/ndr_drsblobs.h
[ 544/3781] Generating HEADER_librpc/gen_ndr/drsblobs.h
[ 545/3781] Generating HEADER_librpc/ndr/ndr_drsblobs.h
[ 546/3781] Generating HEADER_librpc/gen_ndr/krb5pac.h
[ 547/3781] Generating HEADER_librpc/gen_ndr/ndr_krb5pac.h
[ 548/3781] Generating HEADER_librpc/gen_ndr/samr.h
[ 549/3781] Generating HEADER_librpc/gen_ndr/ndr_samr.h
[ 550/3781] Generating HEADER_librpc/gen_ndr/lsa.h
[ 551/3781] Generating HEADER_librpc/gen_ndr/netlogon.h
[ 552/3781] Generating HEADER_librpc/gen_ndr/atsvc.h
[ 553/3781] Generating HEADER_librpc/gen_ndr/ndr_atsvc.h
[ 554/3781] Generating HEADER_librpc/gen_ndr/ndr_svcctl.h
[ 555/3781] Generating HEADER_librpc/gen_ndr/svcctl.h
[ 556/3781] Generating HEADER_librpc/gen_ndr/nbt.h
[ 557/3781] Generating HEADER_librpc/gen_ndr/ndr_nbt.h
[ 558/3781] Generating HEADER_librpc/ndr/ndr_nbt.h
[ 559/3781] Generating HEADER_librpc/gen_ndr/ndr_svcctl_c.h
[ 560/3781] Generating HEADER_librpc/ndr/ndr_svcctl.h
[ 561/3781] Generating HEADER_librpc/gen_ndr/misc.h
[ 562/3781] Generating HEADER_librpc/gen_ndr/ndr_misc.h
[ 563/3781] Generating HEADER_librpc//ndr.h
[ 564/3781] Generating HEADER_librpc//rpc_common.h
[ 565/3781] Generating HEADER_source4/libcli/ldap//ldap-util.h
[ 566/3781] Generating HEADER_source4/libcli//smb_composite.h
[ 567/3781] Generating HEADER_source4/libcli//smb_cli.h
[ 568/3781] Generating HEADER_source4/libcli//smb_request.h
[ 569/3781] Generating HEADER_source4/libcli//smb_raw_signing.h
[ 570/3781] Generating HEADER_source4/libcli//smb_cliraw.h
[ 571/3781] Generating HEADER_source4/libcli//smb_raw_interfaces.h
[ 572/3781] Generating HEADER_source4/libcli//smb_raw.h
[ 573/3781] Generating HEADER_source4/libcli//smb_raw_trans2.h
[ 574/3781] Generating HEADER_source4/libcli/smb2//smb2.h
[ 575/3781] Generating HEADER_libcli/smb//read_smb.h
[ 576/3781] Generating HEADER_libcli/smb//smb_common.h
[ 577/3781] Generating HEADER_libcli/smb//smb2_constants.h
[ 578/3781] Generating HEADER_libcli/smb//smb_constants.h
[ 579/3781] Generating HEADER_libcli/smb//smb_signing.h
[ 580/3781] Generating HEADER_libcli/smb//smb_seal.h
[ 581/3781] Generating HEADER_libcli/smb//smb2_create_blob.h
[ 582/3781] Generating HEADER_libcli/smb//smb2_signing.h
[ 583/3781] Generating HEADER_libcli/smb//smb_util.h
[ 584/3781] Generating HEADER_libcli/smb//smb_unix_ext.h
[ 585/3781] Generating HEADER_libcli/util/core/error.h
[ 586/3781] Generating HEADER_libcli/util/core/ntstatus.h
[ 587/3781] Generating HEADER_libcli/util/core/doserr.h
[ 588/3781] Generating HEADER_libcli/util/core/werror.h
[ 589/3781] Generating HEADER_libcli/ldap//ldap_message.h
[ 590/3781] Generating HEADER_libcli/ldap//ldap_errors.h
[ 591/3781] Generating HEADER_libcli/ldap//ldap_ndr.h
[ 592/3781] Generating HEADER_libcli/auth//domain_credentials.h
[ 593/3781] Generating HEADER_source4/lib/policy//policy.h
[ 594/3781] Generating HEADER_libds/common//roles.h
[ 595/3781] Generating HEADER_source3//netapi.h
[ 596/3781] Generating HEADER_source3//smb_share_modes.h
[ 597/3781] Generating HEADER_source3//passdb.h
[ 598/3781] Generating HEADER_source3//machine_sid.h
[ 599/3781] Generating HEADER_source3//lookup_sid.h
[ 600/3781] Generating HEADER_source3//smbldap.h
[ 601/3781] Generating HEADER_source3//smb_ldap.h
[ 602/3781] Generating HEADER_source3//smbconf.h
[ 603/3781] Generating HEADER_source3/libsmb//libsmbclient.h
[ 604/3781] GEN_NDR_TABLES: librpc/tables.pl bin/default/librpc/gen_ndr/ndr_srvsvc.h bin/default/librpc/gen_ndr/ndr_orpc.h bin/default/librpc/gen_ndr/ndr_named_pipe_auth.h bin/default/librpc/gen_ndr/ndr_efs.h bin/default/librpc/gen_ndr/ndr_drsblobs.h bin/default/librpc/gen_ndr/ndr_printcap.h bin/default/librpc/gen_ndr/ndr_scerpc.h bin/default/librpc/gen_ndr/ndr_server_id.h bin/default/librpc/gen_ndr/ndr_rot.h bin/default/librpc/gen_ndr/ndr_dnsp.h bin/default/librpc/gen_ndr/ndr_svcctl.h bin/default/librpc/gen_ndr/ndr_smb_acl.h bin/default/librpc/gen_ndr/ndr_browser.h bin/default/librpc/gen_ndr/ndr_file_id.h bin/default/librpc/gen_ndr/ndr_ntlmssp.h bin/default/source3/librpc/gen_ndr/ndr_messaging.h bin/default/librpc/gen_ndr/ndr_initshutdown.h bin/default/librpc/gen_ndr/ndr_ntsvcs.h bin/default/librpc/gen_ndr/ndr_trkwks.h bin/default/source4/librpc/gen_ndr/ndr_nfs4acl.h bin/default/librpc/gen_ndr/ndr_notify.h bin/default/librpc/gen_ndr/ndr_frsrpc.h bin/default/librpc/gen_ndr/ndr_schannel.h bin/default/librpc/gen_ndr/ndr_dfsblobs.h bin/default/librpc/gen_ndr/ndr_netlogon.h bin/default/librpc/gen_ndr/ndr_dsbackup.h bin/default/librpc/gen_ndr/ndr_oxidresolver.h bin/default/source3/librpc/gen_ndr/ndr_open_files.h bin/default/librpc/gen_ndr/ndr_eventlog.h bin/default/librpc/gen_ndr/ndr_dcom.h bin/default/source3/librpc/gen_ndr/ndr_libnet_join.h bin/default/librpc/gen_ndr/ndr_keysvc.h bin/default/librpc/gen_ndr/ndr_wzcsvc.h bin/default/librpc/gen_ndr/ndr_frsapi.h bin/default/source3/librpc/gen_ndr/ndr_smbXsrv.h bin/default/librpc/gen_ndr/ndr_eventlog6.h bin/default/librpc/gen_ndr/ndr_audiosrv.h bin/default/librpc/gen_ndr/ndr_misc.h bin/default/source4/librpc/gen_ndr/ndr_opendb.h bin/default/source3/librpc/gen_ndr/ndr_libnetapi.h bin/default/librpc/gen_ndr/ndr_dfs.h bin/default/librpc/gen_ndr/ndr_wmi.h bin/default/source4/librpc/gen_ndr/ndr_winbind.h bin/default/librpc/gen_ndr/ndr_frstrans.h bin/default/librpc/gen_ndr/ndr_auth.h bin/default/librpc/gen_ndr/ndr_preg.h bin/default/librpc/gen_ndr/ndr_ntprinting.h bin/default/librpc/gen_ndr/ndr_w32time.h bin/default/librpc/gen_ndr/ndr_backupkey.h bin/default/librpc/gen_ndr/ndr_dns.h bin/default/librpc/gen_ndr/ndr_remact.h bin/default/librpc/gen_ndr/ndr_samr.h bin/default/source3/librpc/gen_ndr/ndr_secrets.h bin/default/librpc/gen_ndr/ndr_winreg.h bin/default/librpc/gen_ndr/ndr_msgsvc.h bin/default/librpc/gen_ndr/ndr_dssetup.h bin/default/librpc/gen_ndr/ndr_echo.h bin/default/librpc/gen_ndr/ndr_spoolss.h bin/default/source4/librpc/gen_ndr/ndr_irpc.h bin/default/librpc/gen_ndr/ndr_idmap.h bin/default/librpc/gen_ndr/ndr_dcerpc.h bin/default/librpc/gen_ndr/ndr_dnsserver.h bin/default/librpc/gen_ndr/ndr_fsrvp.h bin/default/librpc/gen_ndr/ndr_lsa.h bin/default/librpc/gen_ndr/ndr_ioctl.h bin/default/source4/librpc/gen_ndr/ndr_winsrepl.h bin/default/source4/librpc/gen_ndr/ndr_winstation.h bin/default/librpc/gen_ndr/ndr_unixinfo.h bin/default/librpc/gen_ndr/ndr_rap.h bin/default/librpc/gen_ndr/ndr_drsuapi.h bin/default/librpc/gen_ndr/ndr_mgmt.h bin/default/librpc/gen_ndr/ndr_atsvc.h bin/default/librpc/gen_ndr/ndr_security.h bin/default/source3/librpc/gen_ndr/ndr_perfcount.h bin/default/source4/librpc/gen_ndr/ndr_ntp_signd.h bin/default/librpc/gen_ndr/ndr_epmapper.h bin/default/librpc/gen_ndr/ndr_policyagent.h bin/default/librpc/gen_ndr/ndr_krb5pac.h bin/default/source4/librpc/gen_ndr/ndr_sasl_helpers.h bin/default/librpc/gen_ndr/ndr_xattr.h bin/default/librpc/gen_ndr/ndr_nbt.h bin/default/librpc/gen_ndr/ndr_dbgidl.h bin/default/source3/librpc/gen_ndr/ndr_wbint.h bin/default/source4/librpc/gen_ndr/ndr_winsif.h bin/default/librpc/gen_ndr/ndr_wkssvc.h -> bin/default/source4/librpc/gen_ndr/tables.c
[ 605/3781] Generating test_headers.h
[ 606/3781] Compiling lib/replace/test/testsuite.c
[ 607/3781] Compiling lib/replace/test/strptime.c
[ 608/3781] Compiling lib/replace/test/os2_delete.c
[ 609/3781] Compiling lib/replace/test/getifaddrs.c
[ 610/3781] Compiling lib/socket/interfaces.c
[ 611/3781] Compiling lib/talloc/talloc.c
[ 612/3781] Compiling lib/talloc/pytalloc_util.c
[ 613/3781] Compiling lib/talloc/pytalloc.c
[ 614/3781] Compiling lib/tevent/tevent.c
[ 615/3781] Compiling lib/tevent/tevent_debug.c
[ 616/3781] Compiling lib/tevent/tevent_fd.c
[ 617/3781] Compiling lib/tevent/tevent_immediate.c
[ 618/3781] Compiling lib/tevent/tevent_queue.c
[ 619/3781] Compiling lib/tevent/tevent_req.c
[ 620/3781] Compiling lib/tevent/tevent_select.c
[ 621/3781] Compiling lib/tevent/tevent_poll.c
[ 622/3781] Compiling lib/tevent/tevent_signal.c
[ 623/3781] Compiling lib/tevent/tevent_standard.c
[ 624/3781] Compiling lib/tevent/tevent_timed.c
[ 625/3781] Compiling lib/tevent/tevent_util.c
[ 626/3781] Compiling lib/tevent/tevent_wakeup.c
[ 627/3781] Compiling lib/tevent/tevent_epoll.c
[ 628/3781] Compiling lib/tevent/pytevent.c
../lib/tevent/pytevent.c: In function âpy_tevent_context_newâ:
../lib/tevent/pytevent.c:639:2: warning: passing argument 4 of âPyArg_ParseTupleAndKeywordsâ from incompatible pointer type [enabled by default]
/usr/include/python2.7/modsupport.h:28:17: note: expected âchar **â but argument is of type âconst char * const*â
[ 629/3781] Compiling lib/addns/dnsquery.c
[ 630/3781] Compiling lib/addns/dnsrecord.c
[ 631/3781] Compiling lib/addns/dnsutils.c
[ 632/3781] Compiling lib/addns/dnssock.c
[ 633/3781] Compiling lib/addns/dnsgss.c
[ 634/3781] Compiling lib/addns/dnsmarshall.c
[ 635/3781] Compiling lib/addns/error.c
[ 636/3781] Compiling lib/ccan/hash/hash.c
[ 637/3781] Compiling lib/ccan/ilog/ilog.c
[ 638/3781] Compiling lib/ccan/read_write_all/read_write_all.c
[ 639/3781] Compiling lib/ccan/str/debug.c
[ 640/3781] Compiling lib/ccan/str/str.c
[ 641/3781] Compiling lib/ccan/tally/tally.c
[ 642/3781] Compiling lib/ccan/likely/likely.c
[ 643/3781] Compiling lib/ccan/err/err.c
[ 644/3781] Compiling lib/tdb/common/check.c
[ 645/3781] Compiling lib/tdb/common/error.c
[ 646/3781] Compiling lib/tdb/common/tdb.c
[ 647/3781] Compiling lib/tdb/common/traverse.c
[ 648/3781] Compiling lib/tdb/common/freelistcheck.c
[ 649/3781] Compiling lib/tdb/common/lock.c
[ 650/3781] Compiling lib/tdb/common/dump.c
[ 651/3781] Compiling lib/tdb/common/freelist.c
[ 652/3781] Compiling lib/tdb/common/io.c
[ 653/3781] Compiling lib/tdb/common/open.c
[ 654/3781] Compiling lib/tdb/common/transaction.c
[ 655/3781] Compiling lib/tdb/common/hash.c
[ 656/3781] Compiling lib/tdb/common/summary.c
[ 657/3781] Compiling lib/tdb/common/rescue.c
[ 658/3781] Compiling lib/tdb/tools/tdbtorture.c
[ 659/3781] Compiling lib/tdb/tools/tdbrestore.c
[ 660/3781] Compiling lib/tdb/tools/tdbdump.c
../lib/tdb/tools/tdbdump.c: In function âdump_tdbâ:
../lib/tdb/tools/tdbdump.c:113:3: warning: passing argument 3 of âtdb_rescueâ discards âconstâ qualifier from pointer target type [enabled by default]
default/include/public/tdb.h:835:5: note: expected âvoid *â but argument is of type âconst char *â
[ 661/3781] Compiling lib/tdb/tools/tdbbackup.c
[ 662/3781] Compiling lib/tdb/tools/tdbtool.c
[ 663/3781] Compiling lib/tdb/test/external-agent.c
[ 664/3781] Compiling lib/tdb/test/lock-tracking.c
[ 665/3781] Compiling lib/tdb/test/logging.c
[ 666/3781] Compiling lib/tdb/test/run-3G-file.c
[ 667/3781] Compiling lib/tdb/test/run-bad-tdb-header.c
[ 668/3781] Compiling lib/tdb/test/run.c
[ 669/3781] Compiling lib/tdb/test/run-check.c
[ 670/3781] Compiling lib/tdb/test/run-corrupt.c
[ 671/3781] Compiling lib/tdb/test/run-die-during-transaction.c
[ 672/3781] Compiling lib/tdb/test/run-endian.c
[ 673/3781] Compiling lib/tdb/test/run-incompatible.c
[ 674/3781] Compiling lib/tdb/test/run-nested-transactions.c
[ 675/3781] Compiling lib/tdb/test/run-nested-traverse.c
[ 676/3781] Compiling lib/tdb/test/run-no-lock-during-traverse.c
[ 677/3781] Compiling lib/tdb/test/run-oldhash.c
[ 678/3781] Compiling lib/tdb/test/run-open-during-transaction.c
[ 679/3781] Compiling lib/tdb/test/run-readonly-check.c
[ 680/3781] Compiling lib/tdb/test/run-rescue.c
[ 681/3781] Compiling lib/tdb/test/run-rescue-find_entry.c
[ 682/3781] Compiling lib/tdb/test/run-rwlock-check.c
[ 683/3781] Compiling lib/tdb/test/run-summary.c
[ 684/3781] Compiling lib/tdb/test/run-transaction-expand.c
[ 685/3781] Compiling lib/tdb/test/run-traverse-in-transaction.c
[ 686/3781] Compiling lib/tdb/test/run-wronghash-fail.c
[ 687/3781] Compiling lib/tdb/test/run-zero-append.c
[ 688/3781] Compiling lib/tdb/pytdb.c
[ 689/3781] Compiling lib/tdb_compat/tdb_compat.c
[ 690/3781] Compiling lib/ldb/pyldb_util.c
[ 691/3781] Compiling lib/ldb/common/ldb_modules.c
[ 692/3781] Compiling lib/ldb/common/ldb_ldif.c
[ 693/3781] Compiling lib/ldb/common/ldb_parse.c
[ 694/3781] Compiling lib/ldb/common/ldb_msg.c
[ 695/3781] Compiling lib/ldb/common/ldb_utf8.c
[ 696/3781] Compiling lib/ldb/common/ldb_debug.c
[ 697/3781] Compiling lib/ldb/common/ldb_dn.c
[ 698/3781] Compiling lib/ldb/common/ldb_match.c
[ 699/3781] Compiling lib/ldb/common/ldb_options.c
[ 700/3781] Compiling lib/ldb/common/ldb_pack.c
[ 701/3781] Compiling lib/ldb/common/ldb_attributes.c
[ 702/3781] Compiling lib/ldb/common/attrib_handlers.c
[ 703/3781] Compiling lib/ldb/common/ldb_controls.c
[ 704/3781] Compiling lib/ldb/common/qsort.c
[ 705/3781] Compiling lib/ldb/ldb_map/ldb_map.c
../lib/ldb/ldb_map/ldb_map.c: In function âmap_search_base_reqâ:
../lib/ldb/ldb_map/ldb_map.c:895:6: warning: passing argument 6 of âldb_build_search_req_exâ discards âconstâ qualifier from pointer target type [enabled by default]
../lib/ldb/include/ldb.h:1158:5: note: expected âstruct ldb_parse_tree *â but argument is of type âconst struct ldb_parse_tree *â
[ 706/3781] Compiling lib/ldb/ldb_map/ldb_map_inbound.c
[ 707/3781] Compiling lib/ldb/ldb_map/ldb_map_outbound.c
[ 708/3781] Compiling lib/ldb/pyldb.c
[ 709/3781] Compiling lib/ldb/modules/paged_results.c
[ 710/3781] Compiling lib/ldb/modules/asq.c
[ 711/3781] Compiling lib/ldb/modules/sort.c
[ 712/3781] Compiling lib/ldb/modules/paged_searches.c
[ 713/3781] Compiling lib/ldb/modules/rdn_name.c
[ 714/3781] Compiling lib/ldb/tests/sample_module.c
../lib/ldb/tests/sample_module.c: In function âsample_addâ:
../lib/ldb/tests/sample_module.c:33:2: warning: passing argument 1 of âldb_msg_add_fmtâ discards âconstâ qualifier from pointer target type [enabled by default]
default/include/public/ldb.h:1921:5: note: expected âstruct ldb_message *â but argument is of type âconst struct ldb_message *â
[ 715/3781] Compiling lib/ldb/modules/skel.c
[ 716/3781] Compiling lib/ldb/ldb_tdb/ldb_tdb.c
../lib/ldb/ldb_tdb/ldb_tdb.c: In function âltdb_storeâ:
../lib/ldb/ldb_tdb/ldb_tdb.c:268:43: warning: passing argument 1 of âldb_pack_dataâ from incompatible pointer type [enabled by default]
../lib/ldb/include/ldb_private.h:201:5: note: expected âstruct ldb_context *â but argument is of type âstruct ldb_module *â
[ 717/3781] Compiling lib/ldb/ldb_tdb/ldb_search.c
[ 718/3781] Compiling lib/ldb/ldb_tdb/ldb_index.c
[ 719/3781] Compiling lib/ldb/ldb_tdb/ldb_cache.c
[ 720/3781] Compiling lib/ldb/ldb_tdb/ldb_tdb_wrap.c
[ 721/3781] Compiling lib/ldb/common/ldb.c
../lib/ldb/common/ldb.c: In function âldb_initâ:
../lib/ldb/common/ldb.c:116:3: warning: âtevent_loop_allow_nestingâ is deprecated (declared at default/include/public/tevent.h:1609) [-Wdeprecated-declarations]
[ 722/3781] Compiling lib/ldb/tools/ldbadd.c
[ 723/3781] Compiling lib/ldb/tools/ldbsearch.c
[ 724/3781] Compiling lib/ldb/tools/ldbdel.c
[ 725/3781] Compiling lib/ldb/tools/ldbmodify.c
[ 726/3781] Compiling lib/ldb/tools/ldbedit.c
[ 727/3781] Compiling lib/ldb/tools/ldbrename.c
[ 728/3781] Compiling lib/ldb/tools/ldbtest.c
[ 729/3781] Compiling lib/ldb/tools/ldbdump.c
[ 730/3781] Compiling lib/ldb/tools/ldbutil.c
[ 731/3781] Compiling lib/ldb/tools/cmdline.c
[ 732/3781] Compiling lib/param/loadparm_server_role.c
[ 733/3781] Compiling lib/param/loadparm.c
In file included from ../lib/param/loadparm.c:322:0:
../lib/param/param_functions.c:66:8: warning: âvisibilityâ attribute ignored [-Wattributes]
../lib/param/param_functions.c:78:8: warning: âvisibilityâ attribute ignored [-Wattributes]
[ 734/3781] Compiling lib/param/generic.c
[ 735/3781] Compiling lib/param/util.c
[ 736/3781] Compiling dynconfig/dynconfig.c
[ 737/3781] Compiling lib/util/charset/iconv.c
[ 738/3781] Compiling lib/util/charset/codepoints.c
[ 739/3781] Compiling lib/util/charset/convert_string.c
[ 740/3781] Compiling lib/util/charset/util_str.c
[ 741/3781] Compiling lib/util/charset/util_unistr_w.c
[ 742/3781] Compiling lib/util/charset/pull_push.c
[ 743/3781] Compiling lib/util/charset/util_unistr.c
[ 744/3781] Compiling lib/util/charset/weird.c
[ 745/3781] Compiling lib/util/charset/charset_macosxfs.c
[ 746/3781] Compiling python/modules.c
[ 747/3781] Compiling python/pyglue.c
[ 748/3781] Compiling source4/param/provision.c
[ 749/3781] Compiling source4/param/pyparam.c
[ 750/3781] Compiling source4/param/share.c
[ 751/3781] Compiling source4/param/share_classic.c
[ 752/3781] Compiling source4/param/share_ldb.c
[ 753/3781] Compiling source4/param/secrets.c
[ 754/3781] Compiling source4/param/pyparam.c
[ 755/3781] Compiling source4/param/loadparm.c
[ 756/3781] Compiling source4/param/pyparam_util.c
[ 757/3781] Compiling librpc/tools/ndrdump.c
[ 758/3781] Compiling default/source4/librpc/gen_ndr/ndr_winstation.c
[ 759/3781] Compiling default/source4/librpc/gen_ndr/ndr_irpc.c
[ 760/3781] Compiling default/source4/librpc/gen_ndr/ndr_sasl_helpers.c
[ 761/3781] Compiling default/source4/librpc/gen_ndr/ndr_nfs4acl.c
[ 762/3781] Compiling default/source4/librpc/gen_ndr/ndr_winsif.c
default/source4/librpc/gen_ndr/ndr_winsif.c: In function ândr_pull_winsif_RecordActionâ:
default/source4/librpc/gen_ndr/ndr_winsif.c:232:4: warning: passing argument 3 of ândr_pull_wrepl_nbt_nameâ from incompatible pointer type [enabled by default]
../source4/../libcli/nbt/libnbt.h:336:1: note: expected âconst struct nbt_name **â but argument is of type âstruct nbt_name **â
default/source4/librpc/gen_ndr/ndr_winsif.c: In function ândr_pull_winsif_WinsGetDbRecsByNameâ:
default/source4/librpc/gen_ndr/ndr_winsif.c:2581:4: warning: passing argument 3 of ândr_pull_wrepl_nbt_nameâ from incompatible pointer type [enabled by default]
../source4/../libcli/nbt/libnbt.h:336:1: note: expected âconst struct nbt_name **â but argument is of type âstruct nbt_name **â
[ 763/3781] Compiling default/source4/librpc/gen_ndr/ndr_opendb.c
[ 764/3781] Compiling default/source4/librpc/gen_ndr/ndr_ntp_signd.c
[ 765/3781] Compiling default/source4/librpc/gen_ndr/ndr_winsrepl.c
default/source4/librpc/gen_ndr/ndr_winsrepl.c: In function ândr_pull_wrepl_wins_nameâ:
default/source4/librpc/gen_ndr/ndr_winsrepl.c:301:3: warning: passing argument 3 of ândr_pull_wrepl_nbt_nameâ from incompatible pointer type [enabled by default]
../source4/../libcli/nbt/libnbt.h:336:1: note: expected âconst struct nbt_name **â but argument is of type âstruct nbt_name **â
[ 766/3781] Compiling default/source4/librpc/gen_ndr/ndr_winbind.c
[ 767/3781] Compiling librpc/ndr/ndr_table.c
[ 768/3781] Compiling default/source4/librpc/gen_ndr/tables.c
[ 769/3781] Compiling default/source4/librpc/gen_ndr/ndr_irpc_c.c
[ 770/3781] Compiling default/source4/librpc/gen_ndr/ndr_winbind_c.c
[ 771/3781] Compiling default/source4/librpc/gen_ndr/ndr_winsif_c.c
[ 772/3781] Compiling source4/librpc/rpc/dcerpc.c
../source4/librpc/rpc/dcerpc.c: In function âdcerpc_pipe_binding_handleâ:
../source4/librpc/rpc/dcerpc.c:588:2: warning: âdcerpc_binding_handle_set_sync_evâ is deprecated (declared at ../source4/../librpc/rpc/rpc_common.h:251) [-Wdeprecated-declarations]
[ 773/3781] Compiling source4/librpc/rpc/dcerpc_auth.c
[ 774/3781] Compiling source4/librpc/rpc/dcerpc_schannel.c
[ 775/3781] Compiling source4/librpc/rpc/dcerpc_util.c
[ 776/3781] Compiling source4/librpc/rpc/dcerpc_smb.c
[ 777/3781] Compiling source4/librpc/rpc/dcerpc_smb2.c
[ 778/3781] Compiling source4/librpc/rpc/dcerpc_sock.c
[ 779/3781] Compiling source4/librpc/rpc/dcerpc_connect.c
[ 780/3781] Compiling source4/librpc/rpc/dcerpc_secondary.c
[ 781/3781] Compiling source4/librpc/rpc/pyrpc_util.c
[ 782/3781] Compiling source4/librpc/rpc/pyrpc.c
[ 783/3781] Compiling default/librpc/gen_ndr/py_srvsvc.c
[ 784/3781] Compiling default/librpc/gen_ndr/py_echo.c
[ 785/3781] Compiling default/librpc/gen_ndr/py_dns.c
[ 786/3781] Compiling default/librpc/gen_ndr/py_auth.c
[ 787/3781] Compiling default/librpc/gen_ndr/py_krb5pac.c
[ 788/3781] Compiling default/librpc/gen_ndr/py_winreg.c
default/librpc/gen_ndr/py_winreg.c: In function âunpack_py_winreg_EnumValue_args_outâ:
default/librpc/gen_ndr/py_winreg.c:1387:40: warning: comparison between pointer and integer [enabled by default]
default/librpc/gen_ndr/py_winreg.c: In function âunpack_py_winreg_QueryValue_args_outâ:
default/librpc/gen_ndr/py_winreg.c:1861:38: warning: comparison between pointer and integer [enabled by default]
[ 789/3781] Compiling default/librpc/gen_ndr/py_misc.c
[ 790/3781] Compiling default/librpc/gen_ndr/py_initshutdown.c
[ 791/3781] Compiling default/librpc/gen_ndr/py_epmapper.c
[ 792/3781] Compiling default/librpc/gen_ndr/py_mgmt.c
[ 793/3781] Compiling default/librpc/gen_ndr/py_atsvc.c
[ 794/3781] Compiling default/librpc/gen_ndr/py_nbt.c
[ 795/3781] Compiling default/librpc/gen_ndr/py_samr.c
[ 796/3781] Compiling default/librpc/gen_ndr/py_svcctl.c
[ 797/3781] Compiling default/librpc/gen_ndr/py_lsa.c
[ 798/3781] Compiling default/librpc/gen_ndr/py_wkssvc.c
[ 799/3781] Compiling default/librpc/gen_ndr/py_dfs.c
[ 800/3781] Compiling default/librpc/gen_ndr/py_unixinfo.c
[ 801/3781] Compiling default/source4/librpc/gen_ndr/py_irpc.c
[ 802/3781] Compiling default/librpc/gen_ndr/py_server_id.c
default/librpc/gen_ndr/py_server_id.c: In function âinitserver_idâ:
default/librpc/gen_ndr/py_server_id.c:215:2: warning: overflow in implicit constant conversion [-Woverflow]
[ 803/3781] Compiling default/source4/librpc/gen_ndr/py_winbind.c
[ 804/3781] Compiling default/librpc/gen_ndr/py_idmap.c
[ 805/3781] Compiling default/librpc/gen_ndr/py_drsuapi.c
[ 806/3781] Compiling default/librpc/gen_ndr/py_security.c
[ 807/3781] Compiling default/librpc/gen_ndr/py_drsblobs.c
default/librpc/gen_ndr/py_drsblobs.c: In function âpy_package_PrimaryKerberosString_set_stringâ:
default/librpc/gen_ndr/py_drsblobs.c:4549:2: warning: passing argument 2 of âtalloc_unlinkâ discards âconstâ qualifier from pointer target type [enabled by default]
default/include/public/talloc.h:979:5: note: expected âvoid *â but argument is of type âconst char *â
[ 808/3781] Compiling default/librpc/gen_ndr/py_dnsp.c
[ 809/3781] Compiling default/librpc/gen_ndr/py_xattr.c
[ 810/3781] Compiling default/librpc/gen_ndr/py_idmap.c
[ 811/3781] Compiling default/librpc/gen_ndr/py_netlogon.c
[ 812/3781] Compiling default/librpc/gen_ndr/py_dnsserver.c
[ 813/3781] Compiling default/librpc/gen_ndr/py_smb_acl.c
[ 814/3781] Compiling source4/dsdb/samdb/ldb_modules/util.c
[ 815/3781] Compiling source4/dsdb/samdb/ldb_modules/acl_util.c
[ 816/3781] Compiling source4/dsdb/samdb/ldb_modules/schema_util.c
[ 817/3781] Compiling source4/dsdb/samdb/ldb_modules/ridalloc.c
../source4/dsdb/samdb/ldb_modules/ridalloc.c: In function âridalloc_create_own_rid_setâ:
../source4/dsdb/samdb/ldb_modules/ridalloc.c:418:16: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
[ 818/3781] Compiling source4/dsdb/samdb/ldb_modules/samba_dsdb.c
[ 819/3781] Compiling source4/dsdb/samdb/ldb_modules/samba_secrets.c
[ 820/3781] Compiling source4/dsdb/samdb/ldb_modules/objectguid.c
[ 821/3781] Compiling source4/dsdb/samdb/ldb_modules/repl_meta_data.c
[ 822/3781] Compiling source4/dsdb/samdb/ldb_modules/schema_load.c
[ 823/3781] Compiling source4/dsdb/samdb/ldb_modules/schema_data.c
[ 824/3781] Compiling source4/dsdb/samdb/ldb_modules/samldb.c
[ 825/3781] Compiling source4/dsdb/samdb/ldb_modules/samba3sam.c
[ 826/3781] Compiling source4/dsdb/samdb/ldb_modules/samba3sid.c
[ 827/3781] Compiling source4/dsdb/samdb/ldb_modules/simple_ldap_map.c
[ 828/3781] Compiling source4/dsdb/samdb/ldb_modules/rootdse.c
[ 829/3781] Compiling source4/dsdb/samdb/ldb_modules/password_hash.c
[ 830/3781] Compiling source4/dsdb/samdb/ldb_modules/local_password.c
[ 831/3781] Compiling source4/dsdb/samdb/ldb_modules/extended_dn_in.c
[ 832/3781] Compiling source4/dsdb/samdb/ldb_modules/extended_dn_out.c
[ 833/3781] Compiling source4/dsdb/samdb/ldb_modules/extended_dn_store.c
[ 834/3781] Compiling source4/dsdb/samdb/ldb_modules/show_deleted.c
[ 835/3781] Compiling source4/dsdb/samdb/ldb_modules/partition.c
[ 836/3781] Compiling source4/dsdb/samdb/ldb_modules/partition_init.c
[ 837/3781] Compiling source4/dsdb/samdb/ldb_modules/partition_metadata.c
[ 838/3781] Compiling source4/dsdb/samdb/ldb_modules/new_partition.c
[ 839/3781] Compiling source4/dsdb/samdb/ldb_modules/update_keytab.c
[ 840/3781] Compiling source4/dsdb/samdb/ldb_modules/secrets_tdb_sync.c
[ 841/3781] Compiling source4/dsdb/samdb/ldb_modules/objectclass.c
[ 842/3781] Compiling source4/dsdb/samdb/ldb_modules/objectclass_attrs.c
a[ 843/3781] Compiling source4/dsdb/samdb/ldb_modules/subtree_rename.c
pt[ 844/3781] Compiling source4/dsdb/samdb/ldb_modules/subtree_delete.c
-g[ 845/3781] Compiling source4/dsdb/samdb/ldb_modules/linked_attributes.c
et[ 846/3781] Compiling source4/dsdb/samdb/ldb_modules/ranged_results.c
[ 847/3781] Compiling source4/dsdb/samdb/ldb_modules/anr.c
[ 848/3781] Compiling source4/dsdb/samdb/ldb_modules/instancetype.c
[ 849/3781] Compiling source4/dsdb/samdb/ldb_modules/operational.c
[ 850/3781] Compiling source4/dsdb/samdb/ldb_modules/descriptor.c
 [ 851/3781] Compiling source4/dsdb/samdb/ldb_modules/resolve_oids.c
[ 852/3781] Compiling source4/dsdb/samdb/ldb_modules/acl.c
u[ 853/3781] Compiling source4/dsdb/samdb/ldb_modules/lazy_commit.c
pd[ 854/3781] Compiling source4/dsdb/samdb/ldb_modules/acl_read.c
at[ 855/3781] Compiling source4/dsdb/samdb/ldb_modules/simple_dn.c
e[ 856/3781] Compiling source4/dsdb/samdb/ldb_modules/dirsync.c
[ 857/3781] Compiling source4/dsdb/samdb/samdb.c
[ 858/3781] Compiling source4/dsdb/samdb/samdb_privilege.c
[ 859/3781] Compiling source4/dsdb/samdb/cracknames.c
[ 860/3781] Compiling source4/dsdb/repl/replicated_objects.c
[ 861/3781] Compiling source4/dsdb/common/util.c
[ 862/3781] Compiling source4/dsdb/common/util_groups.c
[ 863/3781] Compiling source4/dsdb/common/util_samr.c
[ 864/3781] Compiling source4/dsdb/common/dsdb_dn.c
[ 865/3781] Compiling source4/dsdb/common/dsdb_access.c
[ 866/3781] Compiling source4/dsdb/schema/schema_init.c
[ 867/3781] Compiling source4/dsdb/schema/schema_set.c
[ 868/3781] Compiling source4/dsdb/schema/schema_query.c
[ 869/3781] Compiling source4/dsdb/schema/schema_syntax.c
[ 870/3781] Compiling source4/dsdb/schema/schema_description.c
[ 871/3781] Compiling source4/dsdb/schema/schema_convert_to_ol.c
[ 872/3781] Compiling source4/dsdb/schema/schema_inferiors.c
[ 873/3781] Compiling source4/dsdb/schema/schema_prefixmap.c
[ 874/3781] Compiling source4/dsdb/schema/schema_info_attr.c
[ 875/3781] Compiling source4/dsdb/schema/schema_filtered.c
[ 876/3781] Compiling source4/dsdb/schema/dsdb_dn.c
[ 877/3781] Compiling source4/dsdb/repl/drepl_service.c
[ 878/3781] Compiling source4/dsdb/repl/drepl_periodic.c
[ 879/3781] Compiling source4/dsdb/repl/drepl_partitions.c
[ 880/3781] Compiling source4/dsdb/repl/drepl_out_pull.c
[ 881/3781] Compiling source4/dsdb/repl/drepl_out_helpers.c
[ 882/3781] Compiling source4/dsdb/repl/drepl_notify.c
[ 883/3781] Compiling source4/dsdb/repl/drepl_ridalloc.c
[ 884/3781] Compiling source4/dsdb/repl/drepl_extended.c
[ 885/3781] Compiling source4/dsdb/repl/drepl_fsmo.c
[ 886/3781] Compiling source4/dsdb/repl/drepl_secret.c
[ 887/3781] Compiling source4/dsdb/repl/drepl_replica.c
[ 888/3781] Compiling source4/dsdb/kcc/kcc_service.c
[ 889/3781] Compiling source4/dsdb/kcc/kcc_connection.c
[ 890/3781] Compiling source4/dsdb/kcc/kcc_topology.c
[ 891/3781] Compiling source4/dsdb/kcc/kcc_deleted.c
[ 892/3781] Compiling source4/dsdb/kcc/kcc_periodic.c
[ 893/3781] Compiling source4/dsdb/kcc/kcc_drs_replica_info.c
[ 894/3781] Compiling source4/dsdb/dns/dns_update.c
[ 895/3781] Compiling source4/dsdb/pydsdb.c
[ 896/3781] Compiling source4/smbd/service.c
[ 897/3781] Compiling source4/smbd/service_stream.c
[ 898/3781] Compiling source4/smbd/service_named_pipe.c
[ 899/3781] Compiling source4/smbd/service_task.c
[ 900/3781] Compiling source4/smbd/process_model.c
[ 901/3781] Compiling source4/smbd/server.c
[ 902/3781] Compiling source4/smbd/process_single.c
[ 903/3781] Compiling source4/smbd/process_standard.c
[ 904/3781] Compiling source4/smbd/process_prefork.c
[ 905/3781] Compiling source4/smbd/process_onefork.c
[ 906/3781] Compiling source4/cluster/cluster.c
[ 907/3781] Compiling source4/cluster/local.c
[ 908/3781] Compiling source4/libnet/libnet.c
[ 909/3781] Compiling source4/libnet/libnet_passwd.c
[ 910/3781] Compiling source4/libnet/libnet_time.c
[ 911/3781] Compiling source4/libnet/libnet_rpc.c
[ 912/3781] Compiling source4/libnet/libnet_join.c
[ 913/3781] Compiling source4/libnet/libnet_site.c
[ 914/3781] Compiling source4/libnet/libnet_become_dc.c
[ 915/3781] Compiling source4/libnet/libnet_unbecome_dc.c
[ 916/3781] Compiling source4/libnet/libnet_vampire.c
[ 917/3781] Compiling source4/libnet/libnet_samdump.c
[ 918/3781] Compiling source4/libnet/libnet_samsync_ldb.c
[ 919/3781] Compiling source4/libnet/libnet_user.c
[ 920/3781] Compiling source4/libnet/libnet_group.c
[ 921/3781] Compiling source4/libnet/libnet_share.c
[ 922/3781] Compiling source4/libnet/libnet_lookup.c
[ 923/3781] Compiling source4/libnet/libnet_domain.c
[ 924/3781] Compiling source4/libnet/userinfo.c
[ 925/3781] Compiling source4/libnet/groupinfo.c
[ 926/3781] Compiling source4/libnet/userman.c
[ 927/3781] Compiling source4/libnet/groupman.c
[ 928/3781] Compiling source4/libnet/prereq_domain.c
[ 929/3781] Compiling source4/libnet/libnet_samsync.c
[ 930/3781] Compiling source4/libnet/py_net.c
[ 931/3781] Compiling source4/libnet/py_net_dckeytab.c
[ 932/3781] Compiling source4/libnet/libnet_export_keytab.c
[ 933/3781] Compiling source4/auth/gensec/socket.c
[ 934/3781] Compiling source4/auth/gensec/gensec_tstream.c
[ 935/3781] Compiling source4/auth/gensec/gensec_krb5.c
[ 936/3781] Compiling source4/auth/gensec/gensec_krb5_util.c
[ 937/3781] Compiling source4/auth/gensec/gensec_gssapi.c
../source4/auth/gensec/gensec_gssapi.c: In function âgensec_gssapi_updateâ:
../source4/auth/gensec/gensec_gssapi.c:458:4: warning: âgsskrb5_set_send_to_kdcâ is deprecated (declared at ../source4/heimdal/lib/gssapi/gssapi/gssapi_krb5.h:123) [-Wdeprecated-declarations]
../source4/auth/gensec/gensec_gssapi.c:485:4: warning: âgsskrb5_set_send_to_kdcâ is deprecated (declared at ../source4/heimdal/lib/gssapi/gssapi/gssapi_krb5.h:123) [-Wdeprecated-declarations]
[ 938/3781] Compiling source4/auth/gensec/schannel.c
[ 939/3781] Compiling source4/auth/gensec/pygensec.c
[ 940/3781] Compiling source4/auth/kerberos/krb5_init_context.c
[ 941/3781] Compiling source4/auth/kerberos/kerberos_pac.c
In file included from ../source4/auth/kerberos/kerberos_pac.c:33:0:
default/source4/auth/kerberos/kerberos_util.h:20:5: warning: âenum credentials_obtainedâ declared inside parameter list [enabled by default]
default/source4/auth/kerberos/kerberos_util.h:20:5: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
[ 942/3781] Compiling source4/auth/kerberos/kerberos_util.c
[ 943/3781] Compiling source4/auth/kerberos/srv_keytab.c
[ 944/3781] Compiling source4/auth/ntlm/auth_sam.c
[ 945/3781] Compiling source4/auth/ntlm/auth_anonymous.c
[ 946/3781] Compiling source4/auth/ntlm/auth_winbind.c
[ 947/3781] Compiling source4/auth/ntlm/auth_developer.c
[ 948/3781] Compiling source4/auth/ntlm/auth_unix.c
[ 949/3781] Compiling source4/auth/ntlm/auth.c
[ 950/3781] Compiling source4/auth/ntlm/auth_util.c
[ 951/3781] Compiling source4/auth/ntlm/auth_simple.c
[ 952/3781] Compiling source4/auth/ntlm/auth_server_service.c
[ 953/3781] Compiling source4/auth/session.c
[ 954/3781] Compiling source4/auth/unix_token.c
[ 955/3781] Compiling source4/auth/samba_server_gensec.c
[ 956/3781] Compiling source4/auth/system_session.c
[ 957/3781] Compiling source4/auth/sam.c
[ 958/3781] Compiling source4/auth/pyauth.c
[ 959/3781] Compiling auth/auth_sam_reply.c
[ 960/3781] Compiling auth/gensec/gensec.c
[ 961/3781] Compiling auth/gensec/gensec_start.c
[ 962/3781] Compiling auth/gensec/gensec_util.c
[ 963/3781] Compiling auth/gensec/spnego.c
[ 964/3781] Compiling auth/ntlmssp/gensec_ntlmssp.c
[ 965/3781] Compiling auth/ntlmssp/ntlmssp.c
[ 966/3781] Compiling auth/ntlmssp/ntlmssp_util.c
[ 967/3781] Compiling auth/ntlmssp/ntlmssp_ndr.c
[ 968/3781] Compiling auth/ntlmssp/ntlmssp_client.c
[ 969/3781] Compiling auth/ntlmssp/ntlmssp_server.c
[ 970/3781] Compiling auth/ntlmssp/ntlmssp_sign.c
[ 971/3781] Compiling auth/ntlmssp/gensec_ntlmssp_server.c
[ 972/3781] Compiling auth/credentials/credentials.c
[ 973/3781] Compiling auth/credentials/credentials_krb5.c
[ 974/3781] Compiling auth/credentials/credentials_secrets.c
[ 975/3781] Compiling auth/credentials/credentials_ntlm.c
[ 976/3781] Compiling auth/credentials/pycredentials.c
[ 977/3781] Compiling auth/kerberos/gssapi_pac.c
[ 978/3781] Compiling auth/kerberos/kerberos_pac.c
[ 979/3781] Compiling nsswitch/wb_common.c
[ 980/3781] Compiling nsswitch/nsstest.c
[ 981/3781] Compiling nsswitch/winbind_nss_linux.c
[ 982/3781] Compiling nsswitch/winbind_nss_linux.c
[ 983/3781] Compiling nsswitch/pam_winbind.c
[ 984/3781] Compiling nsswitch/winbind_krb5_locator.c
[ 985/3781] Compiling nsswitch/wb_reqtrans.c
[ 986/3781] Compiling nsswitch/wbinfo.c
[ 987/3781] Compiling nsswitch/libwbclient/wbc_guid.c
[ 988/3781] Compiling nsswitch/libwbclient/wbc_idmap.c
[ 989/3781] Compiling nsswitch/libwbclient/wbclient.c
[ 990/3781] Compiling nsswitch/libwbclient/wbc_pam.c
[ 991/3781] Compiling nsswitch/libwbclient/wbc_pwd.c
[ 992/3781] Compiling nsswitch/libwbclient/wbc_sid.c
[ 993/3781] Compiling nsswitch/libwbclient/wbc_util.c
[ 994/3781] Compiling source4/lib/samba3/smbpasswd.c
[ 995/3781] Compiling source4/lib/socket/interface.c
[ 996/3781] Compiling source4/lib/socket/socket_ip.c
[ 997/3781] Compiling source4/lib/socket/socket_unix.c
[ 998/3781] Compiling source4/lib/socket/socket.c
[ 999/3781] Compiling source4/lib/socket/access.c
[1000/3781] Compiling source4/lib/socket/connect_multi.c
[1001/3781] Compiling source4/lib/socket/connect.c
[1002/3781] Compiling lib/ldb-samba/ldif_handlers.c
[1003/3781] Compiling lib/ldb-samba/ldb_wrap.c
../lib/ldb-samba/ldb_wrap.c:40:0: warning: "DBGC_CLASS" redefined [enabled by default]
../source4/../lib/util/debug.h:91:0: note: this is the location of the previous definition
[1004/3781] Compiling lib/ldb-samba/pyldb.c
[1005/3781] Compiling lib/ldb-samba/samba_extensions.c
[1006/3781] Compiling lib/ldb-samba/ldb_ildap.c
[1007/3781] Compiling source4/lib/tls/tls.c
../source4/lib/tls/tls.c: In function âtls_init_serverâ:
../source4/lib/tls/tls.c:522:2: warning: âgnutls_transport_set_lowatâ is deprecated (declared at /usr/include/gnutls/compat.h:351) [-Wdeprecated-declarations]
../source4/lib/tls/tls.c: In function âtls_init_clientâ:
../source4/lib/tls/tls.c:584:2: warning: âgnutls_certificate_type_set_priorityâ is deprecated (declared at /usr/include/gnutls/compat.h:347) [-Wdeprecated-declarations]
../source4/lib/tls/tls.c:593:2: warning: âgnutls_transport_set_lowatâ is deprecated (declared at /usr/include/gnutls/compat.h:351) [-Wdeprecated-declarations]
[1008/3781] Compiling source4/lib/tls/tlscert.c
[1009/3781] Compiling source4/lib/tls/tls_tstream.c
../source4/lib/tls/tls_tstream.c: In function â_tstream_tls_connect_sendâ:
../source4/lib/tls/tls_tstream.c:1016:2: warning: âgnutls_certificate_type_set_priorityâ is deprecated (declared at /usr/include/gnutls/compat.h:347) [-Wdeprecated-declarations]
../source4/lib/tls/tls_tstream.c:1033:2: warning: âgnutls_transport_set_lowatâ is deprecated (declared at /usr/include/gnutls/compat.h:351) [-Wdeprecated-declarations]
../source4/lib/tls/tls_tstream.c: In function â_tstream_tls_accept_sendâ:
../source4/lib/tls/tls_tstream.c:1284:2: warning: âgnutls_transport_set_lowatâ is deprecated (declared at /usr/include/gnutls/compat.h:351) [-Wdeprecated-declarations]
[1010/3781] Compiling default/source4/lib/registry/tdr_regf.c
[1011/3781] Compiling source4/lib/registry/interface.c
[1012/3781] Compiling source4/lib/registry/util.c
[1013/3781] Compiling source4/lib/registry/samba.c
[1014/3781] Compiling source4/lib/registry/patchfile_dotreg.c
[1015/3781] Compiling source4/lib/registry/patchfile_preg.c
[1016/3781] Compiling source4/lib/registry/patchfile.c
[1017/3781] Compiling source4/lib/registry/regf.c
[1018/3781] Compiling source4/lib/registry/hive.c
[1019/3781] Compiling source4/lib/registry/local.c
[1020/3781] Compiling source4/lib/registry/ldb.c
[1021/3781] Compiling source4/lib/registry/rpc.c
[1022/3781] Compiling source4/lib/registry/tools/common.c
[1023/3781] Compiling source4/lib/registry/tools/regdiff.c
[1024/3781] Compiling source4/lib/registry/tools/regpatch.c
[1025/3781] Compiling source4/lib/registry/tools/regshell.c
[1026/3781] Compiling source4/lib/registry/tools/regtree.c
[1027/3781] Compiling source4/lib/registry/tests/generic.c
[1028/3781] Compiling source4/lib/registry/tests/hive.c
[1029/3781] Compiling source4/lib/registry/tests/diff.c
[1030/3781] Compiling source4/lib/registry/tests/registry.c
[1031/3781] Compiling source4/lib/registry/pyregistry.c
[1032/3781] Compiling source4/lib/messaging/messaging.c
../source4/lib/messaging/messaging.c: In function âirpc_binding_handleâ:
../source4/lib/messaging/messaging.c:1397:2: warning: âdcerpc_binding_handle_set_sync_evâ is deprecated (declared at ../source4/../librpc/rpc/rpc_common.h:251) [-Wdeprecated-declarations]
[1033/3781] Compiling source4/lib/messaging/pymessaging.c
[1034/3781] Compiling source4/lib/events/tevent_s4.c
../source4/lib/events/tevent_s4.c: In function âs4_event_context_initâ:
../source4/lib/events/tevent_s4.c:71:3: warning: âtevent_loop_allow_nestingâ is deprecated (declared at default/include/public/tevent.h:1609) [-Wdeprecated-declarations]
[1035/3781] Compiling source4/lib/cmdline/credentials.c
[1036/3781] Compiling source4/lib/cmdline/popt_common.c
[1037/3781] Compiling source4/lib/cmdline/popt_credentials.c
[1038/3781] Compiling lib/iniparser_build/iniparser.c
[1039/3781] Compiling lib/iniparser_build/dictionary.c
[1040/3781] Compiling lib/iniparser_build/strlib.c
[1041/3781] Compiling source4/lib/stream/packet.c
[1042/3781] Compiling lib/util/talloc_stack.c
[1043/3781] Compiling lib/util/smb_threads.c
[1044/3781] Compiling lib/util/xfile.c
[1045/3781] Compiling lib/util/data_blob.c
[1046/3781] Compiling lib/util/util_file.c
[1047/3781] Compiling lib/util/time.c
[1048/3781] Compiling lib/util/rbtree.c
[1049/3781] Compiling lib/util/rfc1738.c
[1050/3781] Compiling lib/util/select.c
[1051/3781] Compiling lib/util/genrand.c
[1052/3781] Compiling lib/util/fsusage.c
[1053/3781] Compiling lib/util/blocking.c
[1054/3781] Compiling lib/util/become_daemon.c
[1055/3781] Compiling lib/util/signal.c
[1056/3781] Compiling lib/util/system.c
[1057/3781] Compiling lib/util/params.c
[1058/3781] Compiling lib/util/util.c
[1059/3781] Compiling lib/util/util_id.c
[1060/3781] Compiling lib/util/util_net.c
[1061/3781] Compiling lib/util/util_strlist.c
[1062/3781] Compiling lib/util/util_paths.c
[1063/3781] Compiling lib/util/idtree.c
[1064/3781] Compiling lib/util/debug.c
[1065/3781] Compiling lib/util/fault.c
../lib/util/fault.c: In function âsmb_panicâ:
../lib/util/fault.c:163:1: warning: ânoreturnâ function does return [enabled by default]
[1066/3781] Compiling lib/util/base64.c
[1067/3781] Compiling lib/util/util_str.c
[1068/3781] Compiling lib/util/util_str_common.c
[1069/3781] Compiling lib/util/substitute.c
[1070/3781] Compiling lib/util/ms_fnmatch.c
[1071/3781] Compiling lib/util/server_id.c
[1072/3781] Compiling lib/util/dprintf.c
[1073/3781] Compiling lib/util/parmlist.c
[1074/3781] Compiling lib/util/bitmap.c
[1075/3781] Compiling lib/util/pidfile.c
[1076/3781] Compiling lib/util/util_process.c
[1077/3781] Compiling lib/util/modules.c
[1078/3781] Compiling lib/util/asn1.c
[1079/3781] Compiling lib/util/unix_privs.c
[1080/3781] Compiling lib/util/util_tdb.c
[1081/3781] Compiling lib/util/tevent_unix.c
[1082/3781] Compiling lib/util/tevent_ntstatus.c
[1083/3781] Compiling lib/util/tevent_werror.c
[1084/3781] Compiling lib/util/setid.c
[1085/3781] Compiling lib/util/util_ldb.c
[1086/3781] Compiling lib/util/util_runcmd.c
[1087/3781] Compiling lib/util/util_pw.c
[1088/3781] Compiling lib/tdb_wrap/tdb_wrap.c
[1089/3781] Compiling lib/tdr/tdr.c
[1090/3781] Compiling lib/tsocket/tsocket.c
[1091/3781] Compiling lib/tsocket/tsocket_helpers.c
[1092/3781] Compiling lib/tsocket/tsocket_bsd.c
[1093/3781] Compiling lib/crypto/crc32.c
[1094/3781] Compiling lib/crypto/hmacmd5.c
[1095/3781] Compiling lib/crypto/md4.c
[1096/3781] Compiling lib/crypto/arcfour.c
[1097/3781] Compiling lib/crypto/sha256.c
[1098/3781] Compiling lib/crypto/hmacsha256.c
[1099/3781] Compiling lib/crypto/aes.c
[1100/3781] Compiling lib/crypto/rijndael-alg-fst.c
[1101/3781] Compiling lib/crypto/aes_cmac_128.c
[1102/3781] Compiling lib/crypto/aes_ccm_128.c
[1103/3781] Compiling lib/crypto/md4test.c
[1104/3781] Compiling lib/crypto/md5test.c
[1105/3781] Compiling lib/crypto/hmacmd5test.c
[1106/3781] Compiling lib/crypto/aes_cmac_128_test.c
[1107/3781] Compiling lib/torture/torture.c
[1108/3781] Compiling lib/torture/subunit.c
[1109/3781] Compiling source4/lib/com/tables.c
[1110/3781] Compiling source4/lib/com/rot.c
[1111/3781] Compiling source4/lib/com/main.c
../source4/lib/com/main.c: In function âcom_create_objectâ:
../source4/lib/com/main.c:67:2: warning: passing argument 1 of âfactory->vtable->Releaseâ from incompatible pointer type [enabled by default]
../source4/lib/com/main.c:67:2: note: expected âstruct IUnknown *â but argument is of type âstruct IClassFactory *â
[1112/3781] Compiling source4/lib/com/classes/simple.c
../source4/lib/com/classes/simple.c:95:2: warning: initialization from incompatible pointer type [enabled by default]
../source4/lib/com/classes/simple.c:95:2: warning: (near initialization for âsimple_classobject_vtable.CreateInstanceâ) [enabled by default]
../source4/lib/com/classes/simple.c:106:2: warning: initialization from incompatible pointer type [enabled by default]
../source4/lib/com/classes/simple.c:106:2: warning: (near initialization for âsimple_IStream_vtable.Readâ) [enabled by default]
../source4/lib/com/classes/simple.c:108:1: warning: initialization from incompatible pointer type [enabled by default]
../source4/lib/com/classes/simple.c:108:1: warning: (near initialization for âsimple_IStream_vtable.Writeâ) [enabled by default]
[1113/3781] Compiling source4/lib/com/pycom.c
[1114/3781] Compiling source4/dns_server/dns_server.c
[1115/3781] Compiling source4/dns_server/dns_query.c
[1116/3781] Compiling source4/dns_server/dns_update.c
[1117/3781] Compiling source4/dns_server/dns_utils.c
[1118/3781] Compiling source4/dns_server/dns_crypto.c
[1119/3781] Compiling source4/dns_server/dlz_bind9.c
[1120/3781] Compiling source4/dns_server/dlz_bind9.c
[1121/3781] Compiling source4/dns_server/dlz_bind9.c
[1122/3781] Compiling source4/echo_server/echo_server.c
[1123/3781] Compiling source4/smb_server/service_smb.c
[1124/3781] Compiling source4/smb_server/handle.c
[1125/3781] Compiling source4/smb_server/tcon.c
[1126/3781] Compiling source4/smb_server/session.c
[1127/3781] Compiling source4/smb_server/blob.c
[1128/3781] Compiling source4/smb_server/management.c
[1129/3781] Compiling source4/smb_server/smb_server.c
[1130/3781] Compiling source4/smb_server/smb/receive.c
[1131/3781] Compiling source4/smb_server/smb/negprot.c
[1132/3781] Compiling source4/smb_server/smb/nttrans.c
[1133/3781] Compiling source4/smb_server/smb/reply.c
[1134/3781] Compiling source4/smb_server/smb/request.c
[1135/3781] Compiling source4/smb_server/smb/search.c
[1136/3781] Compiling source4/smb_server/smb/service.c
[1137/3781] Compiling source4/smb_server/smb/sesssetup.c
[1138/3781] Compiling source4/smb_server/smb/srvtime.c
[1139/3781] Compiling source4/smb_server/smb/trans2.c
[1140/3781] Compiling source4/smb_server/smb/signing.c
[1141/3781] Compiling source4/smb_server/smb2/receive.c
[1142/3781] Compiling source4/smb_server/smb2/negprot.c
[1143/3781] Compiling source4/smb_server/smb2/sesssetup.c
[1144/3781] Compiling source4/smb_server/smb2/tcon.c
[1145/3781] Compiling source4/smb_server/smb2/fileio.c
[1146/3781] Compiling source4/smb_server/smb2/fileinfo.c
[1147/3781] Compiling source4/smb_server/smb2/find.c
[1148/3781] Compiling source4/smb_server/smb2/keepalive.c
[1149/3781] Compiling source4/rpc_server/common/server_info.c
[1150/3781] Compiling source4/rpc_server/common/share_info.c
[1151/3781] Compiling source4/rpc_server/common/forward.c
[1152/3781] Compiling source4/rpc_server/common/reply.c
[1153/3781] Compiling source4/rpc_server/dcesrv_auth.c
[1154/3781] Compiling source4/rpc_server/common/loadparm.c
[1155/3781] Compiling source4/rpc_server/dcerpc_server.c
[1156/3781] Compiling source4/rpc_server/dcesrv_mgmt.c
[1157/3781] Compiling source4/rpc_server/handles.c
[1158/3781] Compiling source4/rpc_server/echo/rpc_echo.c
[1159/3781] Compiling source4/rpc_server/epmapper/rpc_epmapper.c
[1160/3781] Compiling source4/rpc_server/remote/dcesrv_remote.c
[1161/3781] Compiling source4/rpc_server/srvsvc/dcesrv_srvsvc.c
[1162/3781] Compiling source4/rpc_server/srvsvc/srvsvc_ntvfs.c
[1163/3781] Compiling source4/rpc_server/wkssvc/dcesrv_wkssvc.c
[1164/3781] Compiling source4/rpc_server/unixinfo/dcesrv_unixinfo.c
[1165/3781] Compiling source4/rpc_server/samr/dcesrv_samr.c
[1166/3781] Compiling source4/rpc_server/samr/samr_password.c
[1167/3781] Compiling source4/rpc_server/winreg/rpc_winreg.c
[1168/3781] Compiling source4/rpc_server/netlogon/dcerpc_netlogon.c
[1169/3781] Compiling source4/rpc_server/lsa/dcesrv_lsa.c
[1170/3781] Compiling source4/rpc_server/lsa/lsa_init.c
[1171/3781] Compiling source4/rpc_server/lsa/lsa_lookup.c
[1172/3781] Compiling source4/rpc_server/backupkey/dcesrv_backupkey.c
[1173/3781] Compiling source4/rpc_server/spoolss/dcesrv_spoolss.c
[1174/3781] Compiling source4/rpc_server/drsuapi/dcesrv_drsuapi.c
[1175/3781] Compiling source4/rpc_server/drsuapi/updaterefs.c
[1176/3781] Compiling source4/rpc_server/drsuapi/getncchanges.c
[1177/3781] Compiling source4/rpc_server/drsuapi/addentry.c
[1178/3781] Compiling source4/rpc_server/drsuapi/writespn.c
../source4/rpc_server/drsuapi/writespn.c: In function âwritespn_check_spnâ:
../source4/rpc_server/drsuapi/writespn.c:123:12: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
[1179/3781] Compiling source4/rpc_server/drsuapi/drsutil.c
[1180/3781] Compiling source4/rpc_server/browser/dcesrv_browser.c
[1181/3781] Compiling source4/rpc_server/eventlog/dcesrv_eventlog6.c
[1182/3781] Compiling source4/rpc_server/dnsserver/dcerpc_dnsserver.c
[1183/3781] Compiling source4/rpc_server/dnsserver/dnsutils.c
[1184/3781] Compiling source4/rpc_server/dnsserver/dnsdata.c
[1185/3781] Compiling source4/rpc_server/dnsserver/dnsdb.c
[1186/3781] Compiling source4/rpc_server/service_rpc.c
[1187/3781] Compiling source4/ldap_server/ldap_server.c
[1188/3781] Compiling source4/ldap_server/ldap_backend.c
[1189/3781] Compiling source4/ldap_server/ldap_bind.c
[1190/3781] Compiling source4/ldap_server/ldap_extended.c
[1191/3781] Compiling source4/web_server/wsgi.c
[1192/3781] Compiling source4/web_server/web_server.c
[1193/3781] Compiling source4/winbind/wb_server.c
[1194/3781] Compiling source4/winbind/wb_irpc.c
[1195/3781] Compiling source4/winbind/wb_samba3_protocol.c
[1196/3781] Compiling source4/winbind/wb_samba3_cmd.c
[1197/3781] Compiling source4/winbind/wb_init_domain.c
[1198/3781] Compiling source4/winbind/wb_dom_info.c
[1199/3781] Compiling source4/winbind/wb_dom_info_trusted.c
[1200/3781] Compiling source4/winbind/wb_sid2domain.c
[1201/3781] Compiling source4/winbind/wb_name2domain.c
[1202/3781] Compiling source4/winbind/wb_sids2xids.c
[1203/3781] Compiling source4/winbind/wb_xids2sids.c
[1204/3781] Compiling source4/winbind/wb_gid2sid.c
[1205/3781] Compiling source4/winbind/wb_sid2uid.c
[1206/3781] Compiling source4/winbind/wb_sid2gid.c
[1207/3781] Compiling source4/winbind/wb_uid2sid.c
[1208/3781] Compiling source4/winbind/wb_connect_lsa.c
[1209/3781] Compiling source4/winbind/wb_connect_sam.c
[1210/3781] Compiling source4/winbind/wb_cmd_lookupname.c
[1211/3781] Compiling source4/winbind/wb_cmd_lookupsid.c
[1212/3781] Compiling source4/winbind/wb_cmd_getdcname.c
[1213/3781] Compiling source4/winbind/wb_cmd_getgrnam.c
[1214/3781] Compiling source4/winbind/wb_cmd_getgrgid.c
[1215/3781] Compiling source4/winbind/wb_cmd_getpwnam.c
[1216/3781] Compiling source4/winbind/wb_cmd_getpwuid.c
[1217/3781] Compiling source4/winbind/wb_cmd_userdomgroups.c
[1218/3781] Compiling source4/winbind/wb_cmd_usersids.c
[1219/3781] Compiling source4/winbind/wb_cmd_list_groups.c
[1220/3781] Compiling source4/winbind/wb_cmd_list_trustdom.c
[1221/3781] Compiling source4/winbind/wb_cmd_list_users.c
[1222/3781] Compiling source4/winbind/wb_cmd_setpwent.c
[1223/3781] Compiling source4/winbind/wb_cmd_getpwent.c
[1224/3781] Compiling source4/winbind/wb_cmd_getgrent.c
[1225/3781] Compiling source4/winbind/wb_cmd_setgrent.c
[1226/3781] Compiling source4/winbind/wb_cmd_getgroups.c
[1227/3781] Compiling source4/winbind/wb_pam_auth.c
[1228/3781] Compiling source4/winbind/wb_sam_logon.c
[1229/3781] Compiling source4/winbind/wb_update_rodc_dns.c
[1230/3781] Compiling source4/winbind/wb_async_helpers.c
[1231/3781] Compiling source4/winbind/wb_utils.c
[1232/3781] Compiling source4/winbind/idmap.c
[1233/3781] Compiling source4/nbt_server/wins/winsdb.c
[1234/3781] Compiling source4/nbt_server/wins/wins_hook.c
[1235/3781] Compiling source4/nbt_server/wins/wins_ldb.c
[1236/3781] Compiling source4/nbt_server/wins/winsserver.c
[1237/3781] Compiling source4/nbt_server/wins/winsclient.c
[1238/3781] Compiling source4/nbt_server/wins/winswack.c
[1239/3781] Compiling source4/nbt_server/wins/wins_dns_proxy.c
[1240/3781] Compiling source4/nbt_server/dgram/request.c
[1241/3781] Compiling source4/nbt_server/dgram/netlogon.c
[1242/3781] Compiling source4/nbt_server/dgram/browse.c
[1243/3781] Compiling source4/nbt_server/interfaces.c
[1244/3781] Compiling source4/nbt_server/register.c
[1245/3781] Compiling source4/nbt_server/query.c
[1246/3781] Compiling source4/nbt_server/nodestatus.c
[1247/3781] Compiling source4/nbt_server/defense.c
[1248/3781] Compiling source4/nbt_server/packet.c
[1249/3781] Compiling source4/nbt_server/irpc.c
[1250/3781] Compiling source4/nbt_server/nbt_server.c
[1251/3781] Compiling source4/wrepl_server/wrepl_server.c
[1252/3781] Compiling source4/wrepl_server/wrepl_in_connection.c
[1253/3781] Compiling source4/wrepl_server/wrepl_in_call.c
[1254/3781] Compiling source4/wrepl_server/wrepl_apply_records.c
[1255/3781] Compiling source4/wrepl_server/wrepl_periodic.c
[1256/3781] Compiling source4/wrepl_server/wrepl_scavenging.c
[1257/3781] Compiling source4/wrepl_server/wrepl_out_pull.c
[1258/3781] Compiling source4/wrepl_server/wrepl_out_push.c
[1259/3781] Compiling source4/wrepl_server/wrepl_out_helpers.c
[1260/3781] Compiling source4/cldap_server/cldap_server.c
[1261/3781] Compiling source4/cldap_server/netlogon.c
[1262/3781] Compiling source4/cldap_server/rootdse.c
[1263/3781] Compiling source4/ntp_signd/ntp_signd.c
[1264/3781] Compiling source4/utils/ntlm_auth.c
[1265/3781] Compiling source4/utils/oLschema2ldif.c
[1266/3781] Compiling source4/ntvfs/ntvfs_base.c
[1267/3781] Compiling source4/ntvfs/ntvfs_generic.c
[1268/3781] Compiling source4/ntvfs/ntvfs_interface.c
[1269/3781] Compiling source4/ntvfs/ntvfs_util.c
[1270/3781] Compiling source4/ntvfs/posix/pvfs_acl.c
[1271/3781] Compiling source4/ntvfs/posix/pvfs_acl_xattr.c
[1272/3781] Compiling source4/ntvfs/posix/pvfs_acl_nfs4.c
[1273/3781] Compiling source4/ntvfs/posix/vfs_posix.c
[1274/3781] Compiling source4/ntvfs/posix/pvfs_util.c
[1275/3781] Compiling source4/ntvfs/posix/pvfs_search.c
[1276/3781] Compiling source4/ntvfs/posix/pvfs_dirlist.c
[1277/3781] Compiling source4/ntvfs/posix/pvfs_fileinfo.c
[1278/3781] Compiling source4/ntvfs/posix/pvfs_unlink.c
[1279/3781] Compiling source4/ntvfs/posix/pvfs_mkdir.c
[1280/3781] Compiling source4/ntvfs/posix/pvfs_open.c
[1281/3781] Compiling source4/ntvfs/posix/pvfs_read.c
[1282/3781] Compiling source4/ntvfs/posix/pvfs_flush.c
[1283/3781] Compiling source4/ntvfs/posix/pvfs_write.c
[1284/3781] Compiling source4/ntvfs/posix/pvfs_fsinfo.c
[1285/3781] Compiling source4/ntvfs/posix/pvfs_qfileinfo.c
[1286/3781] Compiling source4/ntvfs/posix/pvfs_setfileinfo.c
[1287/3781] Compiling source4/ntvfs/posix/pvfs_rename.c
[1288/3781] Compiling source4/ntvfs/posix/pvfs_resolve.c
[1289/3781] Compiling source4/ntvfs/posix/pvfs_shortname.c
[1290/3781] Compiling source4/ntvfs/posix/pvfs_lock.c
[1291/3781] Compiling source4/ntvfs/posix/pvfs_oplock.c
[1292/3781] Compiling source4/ntvfs/posix/pvfs_wait.c
[1293/3781] Compiling source4/ntvfs/posix/pvfs_seek.c
[1294/3781] Compiling source4/ntvfs/posix/pvfs_ioctl.c
[1295/3781] Compiling source4/ntvfs/posix/pvfs_xattr.c
[1296/3781] Compiling source4/ntvfs/posix/pvfs_streams.c
[1297/3781] Compiling source4/ntvfs/posix/pvfs_notify.c
[1298/3781] Compiling source4/ntvfs/posix/pvfs_sys.c
[1299/3781] Compiling source4/ntvfs/posix/xattr_system.c
[1300/3781] Compiling source4/ntvfs/posix/python/pyxattr_native.c
[1301/3781] Compiling source4/ntvfs/posix/posix_eadb.c
[1302/3781] Compiling source4/ntvfs/posix/python/pyposix_eadb.c
[1303/3781] Compiling source4/ntvfs/posix/python/pyxattr_tdb.c
[1304/3781] Compiling source4/ntvfs/common/init.c
[1305/3781] Compiling source4/ntvfs/common/brlock.c
[1306/3781] Compiling source4/ntvfs/common/brlock_tdb.c
[1307/3781] Compiling source4/ntvfs/common/opendb.c
[1308/3781] Compiling source4/ntvfs/common/opendb_tdb.c
[1309/3781] Compiling source4/ntvfs/common/notify.c
[1310/3781] Compiling source4/ntvfs/unixuid/vfs_unixuid.c
../source4/ntvfs/unixuid/vfs_unixuid.c: In function âunixuid_connectâ:
../source4/ntvfs/unixuid/vfs_unixuid.c:257:2: warning: âtevent_loop_set_nesting_hookâ is deprecated (declared at default/include/public/tevent.h:1610) [-Wdeprecated-declarations]
[1311/3781] Compiling source4/ntvfs/sysdep/inotify.c
[1312/3781] Compiling source4/ntvfs/sysdep/sys_notify.c
[1313/3781] Compiling source4/ntvfs/sysdep/sys_lease_linux.c
[1314/3781] Compiling source4/ntvfs/sysdep/sys_lease.c
[1315/3781] Compiling source4/ntvfs/cifs/vfs_cifs.c
[1316/3781] Compiling source4/ntvfs/smb2/vfs_smb2.c
[1317/3781] Compiling source4/ntvfs/simple/vfs_simple.c
[1318/3781] Compiling source4/ntvfs/simple/svfs_util.c
[1319/3781] Compiling source4/ntvfs/cifs_posix_cli/vfs_cifs_posix.c
[1320/3781] Compiling source4/ntvfs/cifs_posix_cli/svfs_util.c
[1321/3781] Compiling source4/ntvfs/print/vfs_print.c
[1322/3781] Compiling source4/ntvfs/ipc/vfs_ipc.c
[1323/3781] Compiling source4/ntvfs/ipc/ipc_rap.c
[1324/3781] Compiling source4/ntvfs/ipc/rap_server.c
[1325/3781] Compiling source4/ntvfs/nbench/vfs_nbench.c
[1326/3781] Compiling source4/ntptr/simple_ldb/ntptr_simple_ldb.c
[1327/3781] Compiling source4/ntptr/ntptr_base.c
[1328/3781] Compiling source4/ntptr/ntptr_interface.c
[1329/3781] Compiling source4/torture/util_smb.c
[1330/3781] Compiling source4/torture/basic/base.c
[1331/3781] Compiling source4/torture/basic/misc.c
[1332/3781] Compiling source4/torture/basic/scanner.c
[1333/3781] Compiling source4/torture/basic/utable.c
[1334/3781] Compiling source4/torture/basic/charset.c
[1335/3781] Compiling source4/torture/basic/mangle_test.c
[1336/3781] Compiling source4/torture/basic/denytest.c
[1337/3781] Compiling source4/torture/basic/aliases.c
[1338/3781] Compiling source4/torture/basic/locking.c
[1339/3781] Compiling source4/torture/basic/secleak.c
[1340/3781] Compiling source4/torture/basic/rename.c
[1341/3781] Compiling source4/torture/basic/dir.c
[1342/3781] Compiling source4/torture/basic/delete.c
[1343/3781] Compiling source4/torture/basic/unlink.c
[1344/3781] Compiling source4/torture/basic/disconnect.c
[1345/3781] Compiling source4/torture/basic/delaywrite.c
[1346/3781] Compiling source4/torture/basic/attr.c
[1347/3781] Compiling source4/torture/basic/properties.c
[1348/3781] Compiling source4/torture/raw/qfsinfo.c
[1349/3781] Compiling source4/torture/raw/qfileinfo.c
[1350/3781] Compiling source4/torture/raw/setfileinfo.c
[1351/3781] Compiling source4/torture/raw/search.c
[1352/3781] Compiling source4/torture/raw/close.c
[1353/3781] Compiling source4/torture/raw/open.c
[1354/3781] Compiling source4/torture/raw/mkdir.c
[1355/3781] Compiling source4/torture/raw/oplock.c
[1356/3781] Compiling source4/torture/raw/notify.c
[1357/3781] Compiling source4/torture/raw/mux.c
[1358/3781] Compiling source4/torture/raw/ioctl.c
[1359/3781] Compiling source4/torture/raw/chkpath.c
[1360/3781] Compiling source4/torture/raw/unlink.c
[1361/3781] Compiling source4/torture/raw/read.c
[1362/3781] Compiling source4/torture/raw/context.c
[1363/3781] Compiling source4/torture/raw/session.c
[1364/3781] Compiling source4/torture/raw/write.c
[1365/3781] Compiling source4/torture/raw/lock.c
[1366/3781] Compiling source4/torture/raw/pingpong.c
[1367/3781] Compiling source4/torture/raw/lockbench.c
[1368/3781] Compiling source4/torture/raw/lookuprate.c
[1369/3781] Compiling source4/torture/raw/tconrate.c
[1370/3781] Compiling source4/torture/raw/openbench.c
[1371/3781] Compiling source4/torture/raw/rename.c
[1372/3781] Compiling source4/torture/raw/eas.c
[1373/3781] Compiling source4/torture/raw/streams.c
[1374/3781] Compiling source4/torture/raw/acls.c
[1375/3781] Compiling source4/torture/raw/seek.c
[1376/3781] Compiling source4/torture/raw/samba3hide.c
[1377/3781] Compiling source4/torture/raw/samba3misc.c
[1378/3781] Compiling source4/torture/raw/composite.c
[1379/3781] Compiling source4/torture/raw/raw.c
[1380/3781] Compiling source4/torture/raw/offline.c
[1381/3781] Compiling source4/torture/smb2/connect.c
[1382/3781] Compiling source4/torture/smb2/scan.c
[1383/3781] Compiling source4/torture/smb2/util.c
[1384/3781] Compiling source4/torture/smb2/getinfo.c
[1385/3781] Compiling source4/torture/smb2/setinfo.c
[1386/3781] Compiling source4/torture/smb2/lock.c
[1387/3781] Compiling source4/torture/smb2/notify.c
[1388/3781] Compiling source4/torture/smb2/smb2.c
[1389/3781] Compiling source4/torture/smb2/durable_open.c
../source4/torture/smb2/durable_open.c: In function âtest_durable_open_alloc_sizeâ:
../source4/torture/smb2/durable_open.c:1595:2: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
../source4/torture/smb2/durable_open.c:1595:2: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
[1390/3781] Compiling source4/torture/smb2/durable_v2_open.c
[1391/3781] Compiling source4/torture/smb2/oplock.c
[1392/3781] Compiling source4/torture/smb2/dir.c
[1393/3781] Compiling source4/torture/smb2/lease.c
[1394/3781] Compiling source4/torture/smb2/create.c
[1395/3781] Compiling source4/torture/smb2/acls.c
[1396/3781] Compiling source4/torture/smb2/read.c
[1397/3781] Compiling source4/torture/smb2/compound.c
[1398/3781] Compiling source4/torture/smb2/streams.c
[1399/3781] Compiling source4/torture/smb2/ioctl.c
[1400/3781] Compiling source4/torture/smb2/rename.c
[1401/3781] Compiling source4/torture/smb2/session.c
[1402/3781] Compiling source4/torture/winbind/winbind.c
[1403/3781] Compiling source4/torture/winbind/struct_based.c
[1404/3781] Compiling nsswitch/libwbclient/tests/wbclient.c
[1405/3781] Compiling source4/torture/libnetapi/libnetapi.c
[1406/3781] Compiling source4/torture/libnetapi/libnetapi_user.c
[1407/3781] Compiling source4/torture/libnetapi/libnetapi_group.c
[1408/3781] Compiling source4/torture/libnetapi/libnetapi_server.c
[1409/3781] Compiling source4/torture/libsmbclient/libsmbclient.c
[1410/3781] Compiling source4/torture/ndr/ndr.c
[1411/3781] Compiling source4/torture/ndr/winreg.c
[1412/3781] Compiling source4/torture/ndr/atsvc.c
[1413/3781] Compiling source4/torture/ndr/lsa.c
[1414/3781] Compiling source4/torture/ndr/epmap.c
[1415/3781] Compiling source4/torture/ndr/dfs.c
[1416/3781] Compiling source4/torture/ndr/netlogon.c
[1417/3781] Compiling source4/torture/ndr/drsuapi.c
[1418/3781] Compiling source4/torture/ndr/spoolss.c
[1419/3781] Compiling source4/torture/ndr/ntprinting.c
[1420/3781] Compiling source4/torture/ndr/samr.c
[1421/3781] Compiling source4/torture/ndr/dfsblob.c
[1422/3781] Compiling source4/torture/ndr/drsblobs.c
[1423/3781] Compiling source4/torture/ndr/nbt.c
[1424/3781] Compiling source4/torture/ndr/ntlmssp.c
[1425/3781] Compiling source4/torture/ndr/string.c
[1426/3781] Compiling source4/torture/ndr/backupkey.c
[1427/3781] Compiling source4/torture/rpc/join.c
[1428/3781] Compiling source4/torture/rpc/lsa.c
[1429/3781] Compiling source4/torture/rpc/forest_trust.c
[1430/3781] Compiling source4/torture/rpc/lsa_lookup.c
[1431/3781] Compiling source4/torture/rpc/session_key.c
[1432/3781] Compiling source4/torture/rpc/echo.c
[1433/3781] Compiling source4/torture/rpc/dfs.c
[1434/3781] Compiling source4/torture/rpc/drsuapi.c
[1435/3781] Compiling source4/torture/rpc/drsuapi_cracknames.c
[1436/3781] Compiling source4/torture/rpc/dsgetinfo.c
[1437/3781] Compiling source4/torture/rpc/spoolss.c
[1438/3781] Compiling source4/torture/rpc/spoolss_access.c
[1439/3781] Compiling source4/torture/rpc/unixinfo.c
[1440/3781] Compiling source4/torture/rpc/samr.c
[1441/3781] Compiling source4/torture/rpc/samr_accessmask.c
[1442/3781] Compiling source4/torture/rpc/samr_priv.c
[1443/3781] Compiling source4/torture/rpc/wkssvc.c
[1444/3781] Compiling source4/torture/rpc/srvsvc.c
[1445/3781] Compiling source4/torture/rpc/svcctl.c
[1446/3781] Compiling source4/torture/rpc/atsvc.c
[1447/3781] Compiling source4/torture/rpc/eventlog.c
[1448/3781] Compiling source4/torture/rpc/epmapper.c
[1449/3781] Compiling source4/torture/rpc/winreg.c
[1450/3781] Compiling source4/torture/rpc/initshutdown.c
[1451/3781] Compiling source4/torture/rpc/oxidresolve.c
[1452/3781] Compiling source4/torture/rpc/remact.c
[1453/3781] Compiling source4/torture/rpc/mgmt.c
[1454/3781] Compiling source4/torture/rpc/scanner.c
[1455/3781] Compiling source4/torture/rpc/autoidl.c
[1456/3781] Compiling source4/torture/rpc/countcalls.c
[1457/3781] Compiling source4/torture/rpc/testjoin.c
[1458/3781] Compiling source4/torture/rpc/schannel.c
[1459/3781] Compiling source4/torture/rpc/netlogon.c
[1460/3781] Compiling source4/torture/rpc/remote_pac.c
[1461/3781] Compiling source4/torture/rpc/samlogon.c
[1462/3781] Compiling source4/torture/rpc/samsync.c
[1463/3781] Compiling source4/torture/rpc/multi_bind.c
[1464/3781] Compiling source4/torture/rpc/dssetup.c
[1465/3781] Compiling source4/torture/rpc/alter_context.c
[1466/3781] Compiling source4/torture/rpc/bench.c
[1467/3781] Compiling source4/torture/rpc/samba3rpc.c
[1468/3781] Compiling source4/torture/rpc/rpc.c
[1469/3781] Compiling source4/torture/rpc/async_bind.c
[1470/3781] Compiling source4/torture/rpc/handles.c
[1471/3781] Compiling source4/torture/rpc/frsapi.c
[1472/3781] Compiling source4/torture/rpc/object_uuid.c
[1473/3781] Compiling source4/torture/rpc/ntsvcs.c
[1474/3781] Compiling source4/torture/rpc/browser.c
[1475/3781] Compiling source4/torture/rpc/bind.c
[1476/3781] Compiling source4/torture/rpc/fsrvp.c
[1477/3781] Compiling source4/torture/rpc/backupkey.c
[1478/3781] Compiling source4/torture/rpc/spoolss_notify.c
[1479/3781] Compiling source4/torture/rpc/spoolss_win.c
[1480/3781] Compiling source4/torture/drs/drs_init.c
[1481/3781] Compiling source4/torture/drs/drs_util.c
[1482/3781] Compiling source4/torture/drs/unit/prefixmap_tests.c
[1483/3781] Compiling source4/torture/drs/unit/schemainfo_tests.c
[1484/3781] Compiling source4/torture/drs/rpc/dssync.c
[1485/3781] Compiling source4/torture/drs/rpc/msds_intid.c
[1486/3781] Compiling source4/torture/dns/dlz_bind9.c
[1487/3781] Compiling source4/torture/dns/internal_dns.c
[1488/3781] Compiling source4/torture/rap/rap.c
[1489/3781] Compiling source4/torture/rap/rpc.c
[1490/3781] Compiling source4/torture/rap/printing.c
[1491/3781] Compiling source4/torture/rap/sam.c
[1492/3781] Compiling source4/torture/dfs/domaindfs.c
[1493/3781] Compiling source4/torture/dfs/common.c
[1494/3781] Compiling source4/torture/auth/ntlmssp.c
[1495/3781] Compiling source4/torture/auth/pac.c
[1496/3781] Compiling source4/torture/auth/smbencrypt.c
[1497/3781] Compiling lib/util/charset/tests/iconv.c
[1498/3781] Compiling lib/talloc/testsuite.c
[1499/3781] Compiling source4/lib/messaging/tests/messaging.c
[1500/3781] Compiling source4/lib/messaging/tests/irpc.c
[1501/3781] Compiling source4/librpc/tests/binding_string.c
[1502/3781] Compiling lib/util/tests/idtree.c
[1503/3781] Compiling lib/util/tests/dlinklist.c
[1504/3781] Compiling source4/lib/socket/testsuite.c
[1505/3781] Compiling source4/libcli/resolve/testsuite.c
[1506/3781] Compiling lib/util/tests/strlist.c
[1507/3781] Compiling lib/util/tests/parmlist.c
[1508/3781] Compiling lib/util/tests/str.c
[1509/3781] Compiling lib/util/tests/time.c
[1510/3781] Compiling lib/util/tests/asn1_tests.c
[1511/3781] Compiling lib/util/tests/data_blob.c
[1512/3781] Compiling lib/util/tests/file.c
[1513/3781] Compiling lib/util/tests/genrand.c
[1514/3781] Compiling lib/compression/testsuite.c
[1515/3781] Compiling lib/util/charset/tests/charset.c
[1516/3781] Compiling lib/util/charset/tests/convert_string.c
[1517/3781] Compiling source4/libcli/security/tests/sddl.c
[1518/3781] Compiling lib/tdr/testsuite.c
[1519/3781] Compiling lib/tevent/testsuite.c
[1520/3781] Compiling source4/param/tests/share.c
[1521/3781] Compiling source4/param/tests/loadparm.c
[1522/3781] Compiling auth/credentials/tests/simple.c
[1523/3781] Compiling source4/torture/local/local.c
[1524/3781] Compiling source4/torture/local/dbspeed.c
[1525/3781] Compiling source4/torture/local/torture.c
[1526/3781] Compiling source4/torture/ldb/ldb.c
[1527/3781] Compiling source4/dsdb/common/tests/dsdb_dn.c
[1528/3781] Compiling source4/dsdb/schema/tests/schema_syntax.c
[1529/3781] Compiling lib/util/tests/anonymous_shared.c
[1530/3781] Compiling source4/torture/nbench/nbio.c
[1531/3781] Compiling source4/torture/nbench/nbench.c
[1532/3781] Compiling source4/torture/unix/unix.c
[1533/3781] Compiling source4/torture/unix/whoami.c
[1534/3781] Compiling source4/torture/unix/unix_info2.c
[1535/3781] Compiling source4/torture/ldap/common.c
[1536/3781] Compiling source4/torture/ldap/basic.c
[1537/3781] Compiling source4/torture/ldap/schema.c
[1538/3781] Compiling source4/torture/ldap/uptodatevector.c
[1539/3781] Compiling source4/torture/ldap/cldap.c
[1540/3781] Compiling source4/torture/ldap/cldapbench.c
[1541/3781] Compiling source4/torture/ldap/ldap_sort.c
[1542/3781] Compiling source4/torture/ldap/nested_search.c
[1543/3781] Compiling source4/torture/nbt/query.c
[1544/3781] Compiling source4/torture/nbt/register.c
[1545/3781] Compiling source4/torture/nbt/wins.c
[1546/3781] Compiling source4/torture/nbt/winsbench.c
[1547/3781] Compiling source4/torture/nbt/winsreplication.c
[1548/3781] Compiling source4/torture/nbt/dgram.c
[1549/3781] Compiling source4/torture/nbt/nbt.c
[1550/3781] Compiling source4/torture/libnet/libnet.c
[1551/3781] Compiling source4/torture/libnet/utils.c
[1552/3781] Compiling source4/torture/libnet/userinfo.c
[1553/3781] Compiling source4/torture/libnet/userman.c
[1554/3781] Compiling source4/torture/libnet/groupinfo.c
[1555/3781] Compiling source4/torture/libnet/groupman.c
[1556/3781] Compiling source4/torture/libnet/domain.c
[1557/3781] Compiling source4/torture/libnet/libnet_lookup.c
[1558/3781] Compiling source4/torture/libnet/libnet_user.c
[1559/3781] Compiling source4/torture/libnet/libnet_group.c
[1560/3781] Compiling source4/torture/libnet/libnet_share.c
[1561/3781] Compiling source4/torture/libnet/libnet_rpc.c
[1562/3781] Compiling source4/torture/libnet/libnet_domain.c
[1563/3781] Compiling source4/torture/libnet/libnet_BecomeDC.c
[1564/3781] Compiling source4/torture/ntp/ntp_signd.c
[1565/3781] Compiling source4/torture/smbtorture.c
[1566/3781] Compiling source4/torture/torture.c
[1567/3781] Compiling source4/torture/shell.c
[1568/3781] Compiling source4/torture/gentest.c
[1569/3781] Compiling source4/torture/masktest.c
[1570/3781] Compiling source4/torture/locktest.c
[1571/3781] Compiling lib/compression/lzxpress.c
[1572/3781] Compiling default/librpc/gen_ndr/ndr_audiosrv.c
[1573/3781] Compiling default/librpc/gen_ndr/ndr_auth.c
[1574/3781] Compiling librpc/ndr/ndr_auth.c
[1575/3781] Compiling default/librpc/gen_ndr/ndr_atsvc.c
[1576/3781] Compiling default/librpc/gen_ndr/ndr_named_pipe_auth.c
[1577/3781] Compiling default/librpc/gen_ndr/ndr_dnsserver.c
[1578/3781] Compiling librpc/ndr/ndr_dnsserver.c
[1579/3781] Compiling default/librpc/gen_ndr/ndr_dns.c
[1580/3781] Compiling librpc/ndr/ndr_dns.c
[1581/3781] Compiling default/librpc/gen_ndr/ndr_dsbackup.c
[1582/3781] Compiling default/librpc/gen_ndr/ndr_dfs.c
[1583/3781] Compiling default/librpc/gen_ndr/ndr_winreg.c
[1584/3781] Compiling default/librpc/gen_ndr/ndr_efs.c
[1585/3781] Compiling default/librpc/gen_ndr/ndr_rot.c
[1586/3781] Compiling librpc/ndr/ndr_frsrpc.c
[1587/3781] Compiling default/librpc/gen_ndr/ndr_frsrpc.c
[1588/3781] Compiling default/librpc/gen_ndr/ndr_frsapi.c
[1589/3781] Compiling default/librpc/gen_ndr/ndr_frstrans.c
[1590/3781] Compiling default/librpc/gen_ndr/ndr_dfsblobs.c
[1591/3781] Compiling default/librpc/gen_ndr/ndr_policyagent.c
[1592/3781] Compiling default/librpc/gen_ndr/ndr_unixinfo.c
[1593/3781] Compiling default/librpc/gen_ndr/ndr_spoolss.c
[1594/3781] Compiling librpc/ndr/ndr_spoolss_buf.c
[1595/3781] Compiling default/librpc/gen_ndr/ndr_printcap.c
[1596/3781] Compiling default/librpc/gen_ndr/ndr_epmapper.c
[1597/3781] Compiling default/librpc/gen_ndr/ndr_dbgidl.c
[1598/3781] Compiling default/librpc/gen_ndr/ndr_dssetup.c
[1599/3781] Compiling default/librpc/gen_ndr/ndr_msgsvc.c
[1600/3781] Compiling default/librpc/gen_ndr/ndr_mgmt.c
[1601/3781] Compiling librpc/ndr/ndr_orpc.c
[1602/3781] Compiling default/librpc/gen_ndr/ndr_orpc.c
[1603/3781] Compiling default/librpc/gen_ndr/ndr_oxidresolver.c
[1604/3781] Compiling default/librpc/gen_ndr/ndr_remact.c
[1605/3781] Compiling default/librpc/gen_ndr/ndr_dcom.c
[1606/3781] Compiling librpc/ndr/ndr_wmi.c
[1607/3781] Compiling default/librpc/gen_ndr/ndr_wmi.c
[1608/3781] Compiling default/librpc/gen_ndr/ndr_wzcsvc.c
[1609/3781] Compiling default/librpc/gen_ndr/ndr_browser.c
[1610/3781] Compiling default/librpc/gen_ndr/ndr_w32time.c
[1611/3781] Compiling default/librpc/gen_ndr/ndr_scerpc.c
[1612/3781] Compiling default/librpc/gen_ndr/ndr_server_id.c
[1613/3781] Compiling default/librpc/gen_ndr/ndr_trkwks.c
[1614/3781] Compiling default/librpc/gen_ndr/ndr_keysvc.c
[1615/3781] Compiling default/librpc/gen_ndr/ndr_rap.c
[1616/3781] Compiling librpc/ndr/ndr_rap.c
[1617/3781] Compiling default/librpc/gen_ndr/ndr_idmap.c
[1618/3781] Compiling default/librpc/gen_ndr/ndr_notify.c
[1619/3781] Compiling librpc/ndr/ndr_ntlmssp.c
[1620/3781] Compiling default/librpc/gen_ndr/ndr_ntlmssp.c
[1621/3781] Compiling default/librpc/gen_ndr/ndr_dnsp.c
[1622/3781] Compiling librpc/ndr/ndr_dnsp.c
[1623/3781] Compiling default/librpc/gen_ndr/ndr_ntprinting.c
[1624/3781] Compiling librpc/ndr/ndr_ntprinting.c
[1625/3781] Compiling default/librpc/gen_ndr/ndr_samr.c
[1626/3781] Compiling default/librpc/gen_ndr/ndr_lsa.c
[1627/3781] Compiling default/librpc/gen_ndr/ndr_security.c
[1628/3781] Compiling librpc/ndr/ndr_sec_helper.c
[1629/3781] Compiling default/librpc/gen_ndr/ndr_smb_acl.c
[1630/3781] Compiling default/librpc/gen_ndr/ndr_svcctl.c
[1631/3781] Compiling librpc/ndr/ndr_svcctl.c
[1632/3781] Compiling default/librpc/gen_ndr/ndr_srvsvc.c
[1633/3781] Compiling default/librpc/gen_ndr/ndr_netlogon.c
[1634/3781] Compiling librpc/ndr/ndr_netlogon.c
[1635/3781] Compiling default/librpc/gen_ndr/ndr_eventlog.c
[1636/3781] Compiling default/librpc/gen_ndr/ndr_ntsvcs.c
[1637/3781] Compiling default/librpc/gen_ndr/ndr_wkssvc.c
[1638/3781] Compiling default/librpc/gen_ndr/ndr_echo.c
[1639/3781] Compiling default/librpc/gen_ndr/ndr_initshutdown.c
[1640/3781] Compiling librpc/ndr/ndr_compression.c
[1641/3781] Compiling default/librpc/gen_ndr/ndr_fsrvp.c
[1642/3781] Compiling default/librpc/gen_ndr/ndr_dcerpc.c
[1643/3781] Compiling librpc/ndr/ndr_drsuapi.c
[1644/3781] Compiling default/librpc/gen_ndr/ndr_drsuapi.c
[1645/3781] Compiling librpc/ndr/ndr_drsblobs.c
[1646/3781] Compiling default/librpc/gen_ndr/ndr_drsblobs.c
[1647/3781] Compiling librpc/ndr/ndr_krb5pac.c
[1648/3781] Compiling default/librpc/gen_ndr/ndr_krb5pac.c
[1649/3781] Compiling default/librpc/gen_ndr/ndr_eventlog6.c
[1650/3781] Compiling librpc/ndr/ndr_xattr.c
[1651/3781] Compiling default/librpc/gen_ndr/ndr_xattr.c
[1652/3781] Compiling librpc/ndr/ndr_schannel.c
[1653/3781] Compiling default/librpc/gen_ndr/ndr_schannel.c
[1654/3781] Compiling default/librpc/gen_ndr/ndr_nbt.c
[1655/3781] Compiling librpc/ndr/ndr_nbt.c
[1656/3781] Compiling librpc/ndr/ndr_backupkey.c
[1657/3781] Compiling default/librpc/gen_ndr/ndr_backupkey.c
[1658/3781] Compiling default/librpc/gen_ndr/ndr_preg.c
[1659/3781] Compiling librpc/ndr/ndr_preg.c
[1660/3781] Compiling default/librpc/gen_ndr/ndr_file_id.c
[1661/3781] Compiling default/librpc/gen_ndr/ndr_xattr_c.c
[1662/3781] Compiling default/librpc/gen_ndr/ndr_idmap_c.c
[1663/3781] Compiling default/librpc/gen_ndr/ndr_smb_acl_c.c
[1664/3781] Compiling default/librpc/gen_ndr/ndr_rot_c.c
[1665/3781] Compiling default/librpc/gen_ndr/ndr_atsvc_c.c
[1666/3781] Compiling default/librpc/gen_ndr/ndr_audiosrv_c.c
[1667/3781] Compiling default/librpc/gen_ndr/ndr_dns_c.c
[1668/3781] Compiling default/librpc/gen_ndr/ndr_echo_c.c
[1669/3781] Compiling default/librpc/gen_ndr/ndr_dsbackup_c.c
[1670/3781] Compiling default/librpc/gen_ndr/ndr_efs_c.c
[1671/3781] Compiling default/librpc/gen_ndr/ndr_lsa_c.c
[1672/3781] Compiling default/librpc/gen_ndr/ndr_samr_c.c
[1673/3781] Compiling default/librpc/gen_ndr/ndr_dfs_c.c
[1674/3781] Compiling default/librpc/gen_ndr/ndr_frsapi_c.c
[1675/3781] Compiling default/librpc/gen_ndr/ndr_drsuapi_c.c
[1676/3781] Compiling default/librpc/gen_ndr/ndr_drsblobs_c.c
[1677/3781] Compiling default/librpc/gen_ndr/ndr_policyagent_c.c
[1678/3781] Compiling default/librpc/gen_ndr/ndr_unixinfo_c.c
[1679/3781] Compiling default/librpc/gen_ndr/ndr_browser_c.c
[1680/3781] Compiling default/librpc/gen_ndr/ndr_spoolss_c.c
[1681/3781] Compiling default/librpc/gen_ndr/ndr_nbt_c.c
[1682/3781] Compiling default/librpc/gen_ndr/ndr_wkssvc_c.c
[1683/3781] Compiling default/librpc/gen_ndr/ndr_srvsvc_c.c
[1684/3781] Compiling default/librpc/gen_ndr/ndr_svcctl_c.c
[1685/3781] Compiling default/librpc/gen_ndr/ndr_eventlog_c.c
[1686/3781] Compiling default/librpc/gen_ndr/ndr_epmapper_c.c
[1687/3781] Compiling default/librpc/gen_ndr/ndr_dbgidl_c.c
[1688/3781] Compiling default/librpc/gen_ndr/ndr_dssetup_c.c
[1689/3781] Compiling default/librpc/gen_ndr/ndr_msgsvc_c.c
[1690/3781] Compiling default/librpc/gen_ndr/ndr_winreg_c.c
[1691/3781] Compiling default/librpc/gen_ndr/ndr_initshutdown_c.c
[1692/3781] Compiling default/librpc/gen_ndr/ndr_mgmt_c.c
[1693/3781] Compiling default/librpc/gen_ndr/ndr_oxidresolver_c.c
[1694/3781] Compiling default/librpc/gen_ndr/ndr_remact_c.c
[1695/3781] Compiling default/librpc/gen_ndr/ndr_wzcsvc_c.c
[1696/3781] Compiling default/librpc/gen_ndr/ndr_w32time_c.c
[1697/3781] Compiling default/librpc/gen_ndr/ndr_scerpc_c.c
[1698/3781] Compiling default/librpc/gen_ndr/ndr_server_id_c.c
[1699/3781] Compiling default/librpc/gen_ndr/ndr_ntsvcs_c.c
[1700/3781] Compiling default/librpc/gen_ndr/ndr_netlogon_c.c
[1701/3781] Compiling default/librpc/gen_ndr/ndr_trkwks_c.c
[1702/3781] Compiling default/librpc/gen_ndr/ndr_keysvc_c.c
[1703/3781] Compiling default/librpc/gen_ndr/ndr_backupkey_c.c
[1704/3781] Compiling default/librpc/gen_ndr/ndr_dnsp_c.c
[1705/3781] Compiling default/librpc/gen_ndr/ndr_dnsserver_c.c
[1706/3781] Compiling default/librpc/gen_ndr/ndr_ioctl.c
[1707/3781] Compiling default/librpc/gen_ndr/ndr_fsrvp_c.c
[1708/3781] Compiling librpc/ndr/ndr_string.c
[1709/3781] Compiling librpc/ndr/ndr_basic.c
[1710/3781] Compiling librpc/ndr/uuid.c
[1711/3781] Compiling librpc/ndr/ndr.c
[1712/3781] Compiling librpc/ndr/ndr_misc.c
[1713/3781] Compiling default/librpc/gen_ndr/ndr_misc.c
[1714/3781] Compiling librpc/ndr/util.c
[1715/3781] Compiling librpc/rpc/dcerpc_error.c
[1716/3781] Compiling librpc/rpc/binding.c
[1717/3781] Compiling librpc/rpc/dcerpc_util.c
[1718/3781] Compiling librpc/rpc/binding_handle.c
[1719/3781] Compiling source4/client/client.c
[1720/3781] Compiling source4/client/cifsdd.c
[1721/3781] Compiling source4/client/cifsddio.c
[1722/3781] Compiling source4/libcli/ldap/ldap_client.c
[1723/3781] Compiling source4/libcli/ldap/ldap_bind.c
[1724/3781] Compiling source4/libcli/ldap/ldap_ildap.c
[1725/3781] Compiling source4/libcli/ldap/ldap_controls.c
[1726/3781] Compiling source4/libcli/wbclient/wbclient.c
[1727/3781] Compiling libcli/util/tstream.c
[1728/3781] Compiling source4/libcli/util/clilsa.c
[1729/3781] Compiling source4/libcli/composite/composite.c
[1730/3781] Compiling source4/libcli/smb_composite/loadfile.c
[1731/3781] Compiling source4/libcli/smb_composite/savefile.c
[1732/3781] Compiling source4/libcli/smb_composite/connect.c
[1733/3781] Compiling source4/libcli/smb_composite/sesssetup.c
[1734/3781] Compiling source4/libcli/smb_composite/fetchfile.c
[1735/3781] Compiling source4/libcli/smb_composite/appendacl.c
[1736/3781] Compiling source4/libcli/smb_composite/fsinfo.c
[1737/3781] Compiling source4/libcli/smb_composite/smb2.c
[1738/3781] Compiling source4/libcli/pysmb.c
[1739/3781] Compiling source4/libcli/dgram/dgramsocket.c
[1740/3781] Compiling source4/libcli/dgram/mailslot.c
[1741/3781] Compiling source4/libcli/dgram/netlogon.c
[1742/3781] Compiling source4/libcli/dgram/browse.c
[1743/3781] Compiling source4/libcli/wrepl/winsrepl.c
[1744/3781] Compiling source4/libcli/resolve/resolve.c
[1745/3781] Compiling source4/libcli/resolve/bcast.c
[1746/3781] Compiling source4/libcli/resolve/nbtlist.c
[1747/3781] Compiling source4/libcli/resolve/wins.c
[1748/3781] Compiling source4/libcli/resolve/dns_ex.c
[1749/3781] Compiling source4/libcli/resolve/file.c
[1750/3781] Compiling source4/libcli/resolve/host.c
[1751/3781] Compiling source4/libcli/resolve/resolve_lp.c
[1752/3781] Compiling source4/libcli/finddcs_cldap.c
[1753/3781] Compiling source4/libcli/clireadwrite.c
[1754/3781] Compiling source4/libcli/cliconnect.c
[1755/3781] Compiling source4/libcli/clifile.c
[1756/3781] Compiling source4/libcli/clilist.c
[1757/3781] Compiling source4/libcli/clitrans2.c
[1758/3781] Compiling source4/libcli/climessage.c
[1759/3781] Compiling source4/libcli/clideltree.c
[1760/3781] Compiling source4/libcli/raw/rawfile.c
[1761/3781] Compiling source4/libcli/raw/smb_signing.c
[1762/3781] Compiling source4/libcli/raw/clisocket.c
[1763/3781] Compiling source4/libcli/raw/clitransport.c
[1764/3781] Compiling source4/libcli/raw/clisession.c
[1765/3781] Compiling source4/libcli/raw/clitree.c
[1766/3781] Compiling source4/libcli/raw/clierror.c
[1767/3781] Compiling source4/libcli/raw/rawrequest.c
[1768/3781] Compiling source4/libcli/raw/rawreadwrite.c
[1769/3781] Compiling source4/libcli/raw/rawsearch.c
[1770/3781] Compiling source4/libcli/raw/rawsetfileinfo.c
[1771/3781] Compiling source4/libcli/raw/raweas.c
[1772/3781] Compiling source4/libcli/raw/rawtrans.c
[1773/3781] Compiling source4/libcli/raw/clioplock.c
[1774/3781] Compiling source4/libcli/raw/rawnegotiate.c
[1775/3781] Compiling source4/libcli/raw/rawfsinfo.c
[1776/3781] Compiling source4/libcli/raw/rawfileinfo.c
[1777/3781] Compiling source4/libcli/raw/rawnotify.c
[1778/3781] Compiling source4/libcli/raw/rawioctl.c
[1779/3781] Compiling source4/libcli/raw/rawacl.c
[1780/3781] Compiling source4/libcli/raw/rawdate.c
[1781/3781] Compiling source4/libcli/raw/rawlpq.c
[1782/3781] Compiling source4/libcli/raw/rawshadow.c
[1783/3781] Compiling source4/libcli/smb2/transport.c
[1784/3781] Compiling source4/libcli/smb2/request.c
[1785/3781] Compiling source4/libcli/smb2/session.c
[1786/3781] Compiling source4/libcli/smb2/tcon.c
[1787/3781] Compiling source4/libcli/smb2/create.c
[1788/3781] Compiling source4/libcli/smb2/close.c
[1789/3781] Compiling source4/libcli/smb2/connect.c
[1790/3781] Compiling source4/libcli/smb2/getinfo.c
[1791/3781] Compiling source4/libcli/smb2/write.c
[1792/3781] Compiling source4/libcli/smb2/read.c
[1793/3781] Compiling source4/libcli/smb2/setinfo.c
[1794/3781] Compiling source4/libcli/smb2/find.c
[1795/3781] Compiling source4/libcli/smb2/ioctl.c
[1796/3781] Compiling source4/libcli/smb2/logoff.c
[1797/3781] Compiling source4/libcli/smb2/tdis.c
[1798/3781] Compiling source4/libcli/smb2/flush.c
[1799/3781] Compiling source4/libcli/smb2/lock.c
[1800/3781] Compiling source4/libcli/smb2/notify.c
[1801/3781] Compiling source4/libcli/smb2/cancel.c
[1802/3781] Compiling source4/libcli/smb2/keepalive.c
[1803/3781] Compiling source4/libcli/smb2/break.c
[1804/3781] Compiling source4/libcli/smb2/util.c
[1805/3781] Compiling source4/libcli/smb2/signing.c
[1806/3781] Compiling source4/libcli/smb2/lease_break.c
[1807/3781] Compiling source4/libcli/rap/rap.c
[1808/3781] Compiling libcli/smb/read_smb.c
[1809/3781] Compiling libcli/smb/smb_signing.c
[1810/3781] Compiling libcli/smb/smb_seal.c
[1811/3781] Compiling libcli/smb/smb2_create_blob.c
[1812/3781] Compiling libcli/smb/smb2_signing.c
[1813/3781] Compiling libcli/smb/util.c
[1814/3781] Compiling libcli/smb/smbXcli_base.c
[1815/3781] Compiling libcli/smb/smb1cli_trans.c
[1816/3781] Compiling libcli/smb/smb2cli_session.c
[1817/3781] Compiling libcli/smb/smb2cli_create.c
[1818/3781] Compiling libcli/smb/smb2cli_close.c
[1819/3781] Compiling libcli/smb/smb2cli_read.c
[1820/3781] Compiling libcli/smb/smb2cli_write.c
[1821/3781] Compiling libcli/smb/smb2cli_flush.c
[1822/3781] Compiling libcli/smb/smb2cli_set_info.c
[1823/3781] Compiling libcli/smb/smb2cli_query_info.c
[1824/3781] Compiling libcli/smb/smb2cli_query_directory.c
[1825/3781] Compiling libcli/smb/smb2cli_ioctl.c
[1826/3781] Compiling libcli/util/doserr.c
[1827/3781] Compiling libcli/util/errormap.c
[1828/3781] Compiling libcli/util/nterr.c
[1829/3781] Compiling libcli/util/errmap_unix.c
[1830/3781] Compiling libcli/cldap/cldap.c
[1831/3781] Compiling lib/subunit/c/lib/child.c
[1832/3781] Compiling lib/smbconf/smbconf.c
[1833/3781] Compiling lib/smbconf/smbconf_txt.c
[1834/3781] Compiling lib/smbconf/smbconf_util.c
[1835/3781] Compiling lib/async_req/async_sock.c
[1836/3781] Compiling lib/dbwrap/dbwrap.c
[1837/3781] Compiling lib/dbwrap/dbwrap_util.c
[1838/3781] Compiling lib/dbwrap/dbwrap_rbt.c
[1839/3781] Compiling lib/dbwrap/dbwrap_cache.c
[1840/3781] Compiling lib/dbwrap/dbwrap_tdb.c
[1841/3781] Compiling lib/dbwrap/dbwrap_local_open.c
[1842/3781] Compiling libcli/security/dom_sid.c
[1843/3781] Compiling libcli/security/display_sec.c
[1844/3781] Compiling libcli/security/secace.c
[1845/3781] Compiling libcli/security/secacl.c
[1846/3781] Compiling libcli/security/security_descriptor.c
[1847/3781] Compiling libcli/security/sddl.c
[1848/3781] Compiling libcli/security/privileges.c
[1849/3781] Compiling libcli/security/security_token.c
[1850/3781] Compiling libcli/security/access_check.c
[1851/3781] Compiling libcli/security/object_tree.c
[1852/3781] Compiling libcli/security/create_descriptor.c
[1853/3781] Compiling libcli/security/util_sid.c
[1854/3781] Compiling libcli/security/session.c
[1855/3781] Compiling libcli/security/secdesc.c
[1856/3781] Compiling libcli/security/pysecurity.c
[1857/3781] Compiling libcli/ldap/ldap_message.c
[1858/3781] Compiling libcli/ldap/ldap_ndr.c
[1859/3781] Compiling libcli/nbt/nbtname.c
[1860/3781] Compiling libcli/nbt/lmhosts.c
[1861/3781] Compiling libcli/nbt/nbtsocket.c
[1862/3781] Compiling libcli/nbt/namequery.c
[1863/3781] Compiling libcli/nbt/nameregister.c
[1864/3781] Compiling libcli/nbt/namerefresh.c
[1865/3781] Compiling libcli/nbt/namerelease.c
[1866/3781] Compiling libcli/nbt/tools/nmblookup.c
[1867/3781] Compiling libcli/nbt/pynbt.c
[1868/3781] Compiling libcli/netlogon/netlogon.c
[1869/3781] Compiling libcli/auth/msrpc_parse.c
[1870/3781] Compiling libcli/auth/ntlm_check.c
[1871/3781] Compiling libcli/auth/credentials.c
[1872/3781] Compiling libcli/auth/session.c
[1873/3781] Compiling libcli/auth/smbencrypt.c
[1874/3781] Compiling libcli/auth/smbdes.c
[1875/3781] Compiling libcli/auth/schannel_state_tdb.c
[1876/3781] Compiling libcli/auth/schannel_sign.c
[1877/3781] Compiling libcli/auth/pam_errors.c
[1878/3781] Compiling libcli/auth/spnego_parse.c
[1879/3781] Compiling libcli/lsarpc/util_lsarpc.c
[1880/3781] Compiling libcli/drsuapi/repl_decrypt.c
[1881/3781] Compiling libcli/echo/echo.c
[1882/3781] Compiling libcli/echo/tests/echo.c
[1883/3781] Compiling libcli/dns/dns.c
[1884/3781] Compiling libcli/dns/dns_hosts_file.c
[1885/3781] Compiling libcli/samsync/decrypt.c
[1886/3781] Compiling libcli/registry/util_reg.c
[1887/3781] Compiling source4/lib/policy/gp_ldap.c
[1888/3781] Compiling source4/lib/policy/gp_filesys.c
[1889/3781] Compiling source4/lib/policy/gp_manage.c
[1890/3781] Compiling source4/lib/policy/gp_ini.c
[1891/3781] Compiling source4/lib/policy/pypolicy.c
[1892/3781] Compiling libcli/named_pipe_auth/npa_tstream.c
[1893/3781] Compiling source4/kdc/kdc.c
[1894/3781] Compiling source4/kdc/kpasswdd.c
[1895/3781] Compiling source4/kdc/proxy.c
[1896/3781] Compiling source4/kdc/hdb-samba4.c
[1897/3781] Compiling source4/kdc/hdb-samba4-plugin.c
[1898/3781] Compiling source4/kdc/wdc-samba4.c
[1899/3781] Compiling source4/kdc/pac-glue.c
[1900/3781] Compiling source4/kdc/db-glue.c
[1901/3781] Compiling source4/kdc/mit_samba.c
../source4/kdc/mit_samba.c: In function âmit_samba_context_initâ:
../source4/kdc/mit_samba.c:73:2: warning: âtevent_loop_allow_nestingâ is deprecated (declared at default/include/public/tevent.h:1609) [-Wdeprecated-declarations]
[1902/3781] Compiling source4/heimdal/lib/roken/base64.c
[1903/3781] Compiling source4/heimdal/lib/roken/ct.c
[1904/3781] Compiling source4/heimdal/lib/roken/hex.c
[1905/3781] Compiling source4/heimdal/lib/roken/bswap.c
[1906/3781] Compiling source4/heimdal/lib/roken/dumpdata.c
[1907/3781] Compiling source4/heimdal/lib/roken/emalloc.c
[1908/3781] Compiling source4/heimdal/lib/roken/ecalloc.c
[1909/3781] Compiling source4/heimdal/lib/roken/getarg.c
[1910/3781] Compiling source4/heimdal/lib/roken/get_window_size.c
[1911/3781] Compiling source4/heimdal/lib/roken/getdtablesize.c
[1912/3781] Compiling source4/heimdal/lib/roken/h_errno.c
[1913/3781] Compiling source4/heimdal/lib/roken/issuid.c
[1914/3781] Compiling source4/heimdal/lib/roken/net_read.c
[1915/3781] Compiling source4/heimdal/lib/roken/net_write.c
[1916/3781] Compiling source4/heimdal/lib/roken/parse_time.c
[1917/3781] Compiling source4/heimdal/lib/roken/parse_units.c
[1918/3781] Compiling source4/heimdal/lib/roken/vis.c
[1919/3781] Compiling source4/heimdal/lib/roken/strlwr.c
[1920/3781] Compiling source4/heimdal/lib/roken/strsep_copy.c
[1921/3781] Compiling source4/heimdal/lib/roken/strsep.c
[1922/3781] Compiling source4/heimdal/lib/roken/strupr.c
[1923/3781] Compiling source4/heimdal/lib/roken/strpool.c
[1924/3781] Compiling source4/heimdal/lib/roken/estrdup.c
[1925/3781] Compiling source4/heimdal/lib/roken/erealloc.c
[1926/3781] Compiling source4/heimdal/lib/roken/simple_exec.c
[1927/3781] Compiling source4/heimdal/lib/roken/strcollect.c
[1928/3781] Compiling source4/heimdal/lib/roken/rtbl.c
[1929/3781] Compiling source4/heimdal/lib/roken/rand.c
[1930/3781] Compiling source4/heimdal/lib/roken/cloexec.c
[1931/3781] Compiling source4/heimdal/lib/roken/xfree.c
[1932/3781] Compiling source4/heimdal_build/replace.c
[1933/3781] Compiling source4/heimdal/lib/roken/closefrom.c
[1934/3781] Compiling source4/heimdal/lib/roken/resolve.c
[1935/3781] Compiling source4/heimdal/lib/roken/socket.c
[1936/3781] Compiling source4/heimdal/lib/roken/roken_gethostby.c
[1937/3781] Compiling source4/heimdal/lib/roken/strerror_r.c
[1938/3781] Compiling source4/heimdal/lib/roken/rkpty.c
In file included from ../source4/heimdal/lib/roken/rkpty.c:54:0:
/usr/include/libutil.h:33:2: warning: #warning "Deprecated header, use <bsd/libutil.h> or libbsd-overlay.pc instead." [-Wcpp]
[1939/3781] Compiling default/source4/heimdal/lib/asn1/asn1_kx509_asn1.c
[1940/3781] Compiling default/source4/heimdal/lib/asn1/asn1_digest_asn1.c
[1941/3781] Compiling source4/heimdal/kdc/default_config.c
In file included from ../source4/heimdal/kdc/headers.h:84:0,
                 from ../source4/heimdal/kdc/kdc_locl.h:41,
                 from ../source4/heimdal/kdc/default_config.c:36:
/usr/include/libutil.h:33:2: warning: #warning "Deprecated header, use <bsd/libutil.h> or libbsd-overlay.pc instead." [-Wcpp]
[1942/3781] Compiling source4/heimdal/kdc/kerberos5.c
In file included from ../source4/heimdal/kdc/headers.h:84:0,
                 from ../source4/heimdal/kdc/kdc_locl.h:41,
                 from ../source4/heimdal/kdc/kerberos5.c:34:
/usr/include/libutil.h:33:2: warning: #warning "Deprecated header, use <bsd/libutil.h> or libbsd-overlay.pc instead." [-Wcpp]
[1943/3781] Compiling source4/heimdal/kdc/krb5tgs.c
In file included from ../source4/heimdal/kdc/headers.h:84:0,
                 from ../source4/heimdal/kdc/kdc_locl.h:41,
                 from ../source4/heimdal/kdc/krb5tgs.c:34:
/usr/include/libutil.h:33:2: warning: #warning "Deprecated header, use <bsd/libutil.h> or libbsd-overlay.pc instead." [-Wcpp]
[1944/3781] Compiling source4/heimdal/kdc/pkinit.c
In file included from ../source4/heimdal/kdc/headers.h:84:0,
                 from ../source4/heimdal/kdc/kdc_locl.h:41,
                 from ../source4/heimdal/kdc/pkinit.c:36:
/usr/include/libutil.h:33:2: warning: #warning "Deprecated header, use <bsd/libutil.h> or libbsd-overlay.pc instead." [-Wcpp]
[1945/3781] Compiling source4/heimdal/kdc/log.c
In file included from ../source4/heimdal/kdc/headers.h:84:0,
                 from ../source4/heimdal/kdc/kdc_locl.h:41,
                 from ../source4/heimdal/kdc/log.c:36:
/usr/include/libutil.h:33:2: warning: #warning "Deprecated header, use <bsd/libutil.h> or libbsd-overlay.pc instead." [-Wcpp]
[1946/3781] Compiling source4/heimdal/kdc/misc.c
In file included from ../source4/heimdal/kdc/headers.h:84:0,
                 from ../source4/heimdal/kdc/kdc_locl.h:41,
                 from ../source4/heimdal/kdc/misc.c:34:
/usr/include/libutil.h:33:2: warning: #warning "Deprecated header, use <bsd/libutil.h> or libbsd-overlay.pc instead." [-Wcpp]
[1947/3781] Compiling source4/heimdal/kdc/digest.c
In file included from ../source4/heimdal/kdc/headers.h:84:0,
                 from ../source4/heimdal/kdc/kdc_locl.h:41,
                 from ../source4/heimdal/kdc/digest.c:34:
/usr/include/libutil.h:33:2: warning: #warning "Deprecated header, use <bsd/libutil.h> or libbsd-overlay.pc instead." [-Wcpp]
[1948/3781] Compiling source4/heimdal/kdc/process.c
In file included from ../source4/heimdal/kdc/headers.h:84:0,
                 from ../source4/heimdal/kdc/kdc_locl.h:41,
                 from ../source4/heimdal/kdc/process.c:35:
/usr/include/libutil.h:33:2: warning: #warning "Deprecated header, use <bsd/libutil.h> or libbsd-overlay.pc instead." [-Wcpp]
[1949/3781] Compiling source4/heimdal/kdc/windc.c
In file included from ../source4/heimdal/kdc/headers.h:84:0,
                 from ../source4/heimdal/kdc/kdc_locl.h:41,
                 from ../source4/heimdal/kdc/windc.c:34:
/usr/include/libutil.h:33:2: warning: #warning "Deprecated header, use <bsd/libutil.h> or libbsd-overlay.pc instead." [-Wcpp]
[1950/3781] Compiling source4/heimdal/kdc/kx509.c
In file included from ../source4/heimdal/kdc/headers.h:84:0,
                 from ../source4/heimdal/kdc/kdc_locl.h:41,
                 from ../source4/heimdal/kdc/kx509.c:34:
/usr/include/libutil.h:33:2: warning: #warning "Deprecated header, use <bsd/libutil.h> or libbsd-overlay.pc instead." [-Wcpp]
[1951/3781] Compiling source4/heimdal/lib/ntlm/ntlm.c
[1952/3781] Compiling default/source4/heimdal/lib/asn1/asn1_hdb_asn1.c
[1953/3781] Compiling source4/heimdal/lib/hdb/keys.c
[1954/3781] Compiling source4/heimdal/lib/hdb/db.c
[1955/3781] Compiling source4/heimdal/lib/hdb/dbinfo.c
[1956/3781] Compiling source4/heimdal/lib/hdb/hdb.c
[1957/3781] Compiling source4/heimdal/lib/hdb/ext.c
[1958/3781] Compiling source4/heimdal/lib/hdb/keytab.c
[1959/3781] Compiling source4/heimdal/lib/hdb/hdb-keytab.c
[1960/3781] Compiling source4/heimdal/lib/hdb/mkey.c
[1961/3781] Compiling source4/heimdal/lib/hdb/ndbm.c
[1962/3781] Compiling default/source4/heimdal/lib/hdb/hdb_err.c
[1963/3781] Compiling source4/heimdal_build/hdb-glue.c
[1964/3781] Compiling default/source4/heimdal/lib/gssapi/asn1_gssapi_asn1.c
[1965/3781] Compiling default/source4/heimdal/lib/gssapi/asn1_spnego_asn1.c
[1966/3781] Compiling source4/heimdal/lib/gssapi/spnego/init_sec_context.c
[1967/3781] Compiling source4/heimdal/lib/gssapi/spnego/external.c
[1968/3781] Compiling source4/heimdal/lib/gssapi/spnego/compat.c
[1969/3781] Compiling source4/heimdal/lib/gssapi/spnego/context_stubs.c
[1970/3781] Compiling source4/heimdal/lib/gssapi/spnego/cred_stubs.c
[1971/3781] Compiling source4/heimdal/lib/gssapi/spnego/accept_sec_context.c
[1972/3781] Compiling source4/heimdal/lib/gssapi/krb5/copy_ccache.c
[1973/3781] Compiling source4/heimdal/lib/gssapi/krb5/delete_sec_context.c
[1974/3781] Compiling source4/heimdal/lib/gssapi/krb5/init_sec_context.c
[1975/3781] Compiling source4/heimdal/lib/gssapi/krb5/context_time.c
[1976/3781] Compiling source4/heimdal/lib/gssapi/krb5/init.c
[1977/3781] Compiling source4/heimdal/lib/gssapi/krb5/address_to_krb5addr.c
[1978/3781] Compiling source4/heimdal/lib/gssapi/krb5/get_mic.c
[1979/3781] Compiling source4/heimdal/lib/gssapi/krb5/inquire_context.c
[1980/3781] Compiling source4/heimdal/lib/gssapi/krb5/add_cred.c
[1981/3781] Compiling source4/heimdal/lib/gssapi/krb5/inquire_cred.c
[1982/3781] Compiling source4/heimdal/lib/gssapi/krb5/inquire_cred_by_oid.c
[1983/3781] Compiling source4/heimdal/lib/gssapi/krb5/inquire_cred_by_mech.c
[1984/3781] Compiling source4/heimdal/lib/gssapi/krb5/inquire_mechs_for_name.c
[1985/3781] Compiling source4/heimdal/lib/gssapi/krb5/inquire_names_for_mech.c
[1986/3781] Compiling source4/heimdal/lib/gssapi/krb5/indicate_mechs.c
[1987/3781] Compiling source4/heimdal/lib/gssapi/krb5/inquire_sec_context_by_oid.c
[1988/3781] Compiling source4/heimdal/lib/gssapi/krb5/export_sec_context.c
[1989/3781] Compiling source4/heimdal/lib/gssapi/krb5/import_sec_context.c
[1990/3781] Compiling source4/heimdal/lib/gssapi/krb5/duplicate_name.c
[1991/3781] Compiling source4/heimdal/lib/gssapi/krb5/import_name.c
[1992/3781] Compiling source4/heimdal/lib/gssapi/krb5/compare_name.c
[1993/3781] Compiling source4/heimdal/lib/gssapi/krb5/export_name.c
[1994/3781] Compiling source4/heimdal/lib/gssapi/krb5/canonicalize_name.c
[1995/3781] Compiling source4/heimdal/lib/gssapi/krb5/unwrap.c
[1996/3781] Compiling source4/heimdal/lib/gssapi/krb5/wrap.c
[1997/3781] Compiling source4/heimdal/lib/gssapi/krb5/release_name.c
[1998/3781] Compiling source4/heimdal/lib/gssapi/krb5/cfx.c
[1999/3781] Compiling source4/heimdal/lib/gssapi/krb5/8003.c
[2000/3781] Compiling source4/heimdal/lib/gssapi/krb5/arcfour.c
[2001/3781] Compiling source4/heimdal/lib/gssapi/krb5/encapsulate.c
[2002/3781] Compiling source4/heimdal/lib/gssapi/krb5/display_name.c
[2003/3781] Compiling source4/heimdal/lib/gssapi/krb5/sequence.c
[2004/3781] Compiling source4/heimdal/lib/gssapi/krb5/display_status.c
[2005/3781] Compiling source4/heimdal/lib/gssapi/krb5/release_buffer.c
[2006/3781] Compiling source4/heimdal/lib/gssapi/krb5/external.c
[2007/3781] Compiling source4/heimdal/lib/gssapi/krb5/compat.c
[2008/3781] Compiling source4/heimdal/lib/gssapi/krb5/creds.c
[2009/3781] Compiling source4/heimdal/lib/gssapi/krb5/acquire_cred.c
[2010/3781] Compiling source4/heimdal/lib/gssapi/krb5/release_cred.c
[2011/3781] Compiling source4/heimdal/lib/gssapi/krb5/store_cred.c
[2012/3781] Compiling source4/heimdal/lib/gssapi/krb5/set_cred_option.c
[2013/3781] Compiling source4/heimdal/lib/gssapi/krb5/decapsulate.c
[2014/3781] Compiling source4/heimdal/lib/gssapi/krb5/verify_mic.c
[2015/3781] Compiling source4/heimdal/lib/gssapi/krb5/accept_sec_context.c
[2016/3781] Compiling source4/heimdal/lib/gssapi/krb5/set_sec_context_option.c
[2017/3781] Compiling source4/heimdal/lib/gssapi/krb5/process_context_token.c
[2018/3781] Compiling source4/heimdal/lib/gssapi/krb5/prf.c
[2019/3781] Compiling source4/heimdal/lib/gssapi/krb5/aeap.c
[2020/3781] Compiling source4/heimdal/lib/gssapi/krb5/pname_to_uid.c
[2021/3781] Compiling source4/heimdal/lib/gssapi/krb5/authorize_localname.c
[2022/3781] Compiling source4/heimdal/lib/gssapi/mech/context.c
[2023/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_krb5.c
[2024/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_mech_switch.c
[2025/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_process_context_token.c
[2026/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_buffer_set.c
[2027/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_aeap.c
[2028/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_add_cred.c
[2029/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_cred.c
[2030/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_add_oid_set_member.c
[2031/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_compare_name.c
[2032/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_release_oid_set.c
[2033/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_create_empty_oid_set.c
[2034/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_decapsulate_token.c
[2035/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_inquire_cred_by_oid.c
[2036/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_canonicalize_name.c
[2037/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_inquire_sec_context_by_oid.c
[2038/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_inquire_names_for_mech.c
[2039/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_inquire_mechs_for_name.c
[2040/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_wrap_size_limit.c
[2041/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_names.c
[2042/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_verify.c
[2043/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_display_name.c
[2044/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_duplicate_oid.c
[2045/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_display_status.c
[2046/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_release_buffer.c
[2047/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_release_oid.c
[2048/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_test_oid_set_member.c
[2049/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_release_cred.c
[2050/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_set_sec_context_option.c
[2051/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_export_name.c
[2052/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_seal.c
[2053/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_acquire_cred.c
[2054/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_unseal.c
[2055/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_verify_mic.c
[2056/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_accept_sec_context.c
[2057/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_inquire_cred_by_mech.c
[2058/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_indicate_mechs.c
[2059/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_delete_sec_context.c
[2060/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_sign.c
[2061/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_utils.c
[2062/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_init_sec_context.c
[2063/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_oid_equal.c
[2064/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_oid.c
[2065/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_oid_to_str.c
[2066/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_mo.c
[2067/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_context_time.c
[2068/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_encapsulate_token.c
[2069/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_get_mic.c
[2070/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_import_sec_context.c
[2071/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_inquire_cred.c
[2072/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_wrap.c
[2073/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_import_name.c
[2074/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_duplicate_name.c
[2075/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_unwrap.c
[2076/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_export_sec_context.c
[2077/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_inquire_context.c
[2078/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_release_name.c
[2079/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_set_cred_option.c
[2080/3781] Compiling source4/heimdal/lib/gssapi/mech/gss_pseudo_random.c
[2081/3781] Compiling source4/heimdal_build/gssapi-glue.c
[2082/3781] Compiling source4/heimdal/lib/krb5/expand_path.c
[2083/3781] Compiling source4/heimdal/lib/krb5/plugin.c
[2084/3781] Compiling source4/heimdal/lib/krb5/context.c
[2085/3781] Compiling source4/heimdal/lib/krb5/acache.c
[2086/3781] Compiling source4/heimdal/lib/krb5/add_et_list.c
[2087/3781] Compiling source4/heimdal/lib/krb5/addr_families.c
[2088/3781] Compiling source4/heimdal/lib/krb5/appdefault.c
[2089/3781] Compiling source4/heimdal/lib/krb5/asn1_glue.c
[2090/3781] Compiling source4/heimdal/lib/krb5/auth_context.c
[2091/3781] Compiling source4/heimdal/lib/krb5/build_ap_req.c
[2092/3781] Compiling source4/heimdal/lib/krb5/build_auth.c
[2093/3781] Compiling source4/heimdal/lib/krb5/cache.c
[2094/3781] Compiling source4/heimdal/lib/krb5/changepw.c
[2095/3781] Compiling source4/heimdal/lib/krb5/codec.c
[2096/3781] Compiling source4/heimdal/lib/krb5/config_file.c
[2097/3781] Compiling source4/heimdal/lib/krb5/constants.c
[2098/3781] Compiling source4/heimdal/lib/krb5/convert_creds.c
[2099/3781] Compiling source4/heimdal/lib/krb5/copy_host_realm.c
[2100/3781] Compiling source4/heimdal/lib/krb5/crc.c
[2101/3781] Compiling source4/heimdal/lib/krb5/creds.c
[2102/3781] Compiling source4/heimdal/lib/krb5/crypto.c
[2103/3781] Compiling source4/heimdal/lib/krb5/crypto-aes.c
[2104/3781] Compiling source4/heimdal/lib/krb5/crypto-algs.c
[2105/3781] Compiling source4/heimdal/lib/krb5/crypto-arcfour.c
[2106/3781] Compiling source4/heimdal/lib/krb5/crypto-des3.c
[2107/3781] Compiling source4/heimdal/lib/krb5/crypto-des.c
[2108/3781] Compiling source4/heimdal/lib/krb5/crypto-des-common.c
[2109/3781] Compiling source4/heimdal/lib/krb5/crypto-evp.c
[2110/3781] Compiling source4/heimdal/lib/krb5/crypto-null.c
[2111/3781] Compiling source4/heimdal/lib/krb5/crypto-pk.c
[2112/3781] Compiling source4/heimdal/lib/krb5/crypto-rand.c
[2113/3781] Compiling source4/heimdal/lib/krb5/data.c
[2114/3781] Compiling source4/heimdal/lib/krb5/eai_to_heim_errno.c
[2115/3781] Compiling source4/heimdal/lib/krb5/error_string.c
[2116/3781] Compiling source4/heimdal/lib/krb5/expand_hostname.c
[2117/3781] Compiling source4/heimdal/lib/krb5/fcache.c
[2118/3781] Compiling source4/heimdal/lib/krb5/free.c
[2119/3781] Compiling source4/heimdal/lib/krb5/free_host_realm.c
[2120/3781] Compiling source4/heimdal/lib/krb5/generate_seq_number.c
[2121/3781] Compiling source4/heimdal/lib/krb5/generate_subkey.c
[2122/3781] Compiling source4/heimdal/lib/krb5/get_addrs.c
[2123/3781] Compiling source4/heimdal/lib/krb5/get_cred.c
[2124/3781] Compiling source4/heimdal/lib/krb5/get_default_principal.c
[2125/3781] Compiling source4/heimdal/lib/krb5/get_default_realm.c
[2126/3781] Compiling source4/heimdal/lib/krb5/get_for_creds.c
[2127/3781] Compiling source4/heimdal/lib/krb5/get_host_realm.c
[2128/3781] Compiling source4/heimdal/lib/krb5/get_in_tkt.c
../source4/heimdal/lib/krb5/get_in_tkt.c: In function âkrb5_get_in_tktâ:
../source4/heimdal/lib/krb5/get_in_tkt.c:545:5: warning: âkrb5_get_in_credâ is deprecated (declared at ../source4/heimdal/lib/krb5/get_in_tkt.c:364) [-Wdeprecated-declarations]
[2129/3781] Compiling source4/heimdal/lib/krb5/get_port.c
[2130/3781] Compiling source4/heimdal/lib/krb5/init_creds.c
[2131/3781] Compiling source4/heimdal/lib/krb5/init_creds_pw.c
[2132/3781] Compiling source4/heimdal/lib/krb5/kcm.c
[2133/3781] Compiling source4/heimdal/lib/krb5/keyblock.c
[2134/3781] Compiling source4/heimdal/lib/krb5/keytab.c
[2135/3781] Compiling source4/heimdal/lib/krb5/keytab_any.c
[2136/3781] Compiling source4/heimdal/lib/krb5/keytab_file.c
[2137/3781] Compiling source4/heimdal/lib/krb5/keytab_memory.c
[2138/3781] Compiling source4/heimdal/lib/krb5/keytab_keyfile.c
[2139/3781] Compiling source4/heimdal/lib/krb5/krbhst.c
[2140/3781] Compiling source4/heimdal/lib/krb5/log.c
[2141/3781] Compiling source4/heimdal/lib/krb5/mcache.c
[2142/3781] Compiling source4/heimdal/lib/krb5/misc.c
[2143/3781] Compiling source4/heimdal/lib/krb5/mk_error.c
[2144/3781] Compiling source4/heimdal/lib/krb5/mk_priv.c
[2145/3781] Compiling source4/heimdal/lib/krb5/mk_rep.c
[2146/3781] Compiling source4/heimdal/lib/krb5/mk_req.c
[2147/3781] Compiling source4/heimdal/lib/krb5/mk_req_ext.c
[2148/3781] Compiling source4/heimdal/lib/krb5/mit_glue.c
[2149/3781] Compiling source4/heimdal/lib/krb5/n-fold.c
[2150/3781] Compiling source4/heimdal/lib/krb5/padata.c
[2151/3781] Compiling source4/heimdal/lib/krb5/pkinit.c
[2152/3781] Compiling source4/heimdal/lib/krb5/principal.c
[2153/3781] Compiling source4/heimdal/lib/krb5/prog_setup.c
[2154/3781] Compiling source4/heimdal/lib/krb5/pac.c
[2155/3781] Compiling source4/heimdal/lib/krb5/pcache.c
[2156/3781] Compiling source4/heimdal/lib/krb5/prompter_posix.c
[2157/3781] Compiling source4/heimdal/lib/krb5/rd_cred.c
[2158/3781] Compiling source4/heimdal/lib/krb5/rd_error.c
[2159/3781] Compiling source4/heimdal/lib/krb5/rd_priv.c
[2160/3781] Compiling source4/heimdal/lib/krb5/rd_rep.c
[2161/3781] Compiling source4/heimdal/lib/krb5/rd_req.c
[2162/3781] Compiling source4/heimdal/lib/krb5/replay.c
[2163/3781] Compiling source4/heimdal/lib/krb5/salt.c
[2164/3781] Compiling source4/heimdal/lib/krb5/salt-aes.c
[2165/3781] Compiling source4/heimdal/lib/krb5/salt-arcfour.c
[2166/3781] Compiling source4/heimdal/lib/krb5/salt-des3.c
[2167/3781] Compiling source4/heimdal/lib/krb5/salt-des.c
[2168/3781] Compiling source4/heimdal/lib/krb5/send_to_kdc.c
[2169/3781] Compiling source4/heimdal/lib/krb5/set_default_realm.c
[2170/3781] Compiling source4/heimdal/lib/krb5/store.c
[2171/3781] Compiling source4/heimdal/lib/krb5/store-int.c
[2172/3781] Compiling source4/heimdal/lib/krb5/store_emem.c
[2173/3781] Compiling source4/heimdal/lib/krb5/store_fd.c
[2174/3781] Compiling source4/heimdal/lib/krb5/store_mem.c
[2175/3781] Compiling source4/heimdal/lib/krb5/ticket.c
[2176/3781] Compiling source4/heimdal/lib/krb5/time.c
[2177/3781] Compiling source4/heimdal/lib/krb5/transited.c
[2178/3781] Compiling source4/heimdal/lib/krb5/version.c
[2179/3781] Compiling source4/heimdal/lib/krb5/warn.c
[2180/3781] Compiling default/source4/heimdal/lib/krb5/krb5_err.c
[2181/3781] Compiling source4/heimdal/lib/krb5/aname_to_localname.c
[2182/3781] Compiling source4/heimdal/lib/krb5/kuserok.c
[2183/3781] Compiling default/source4/heimdal/lib/krb5/heim_err.c
[2184/3781] Compiling default/source4/heimdal/lib/krb5/k524_err.c
[2185/3781] Compiling default/source4/heimdal/lib/krb5/krb_err.c
[2186/3781] Compiling source4/heimdal_build/krb5-glue.c
[2187/3781] Compiling source4/heimdal/lib/asn1/der_get.c
[2188/3781] Compiling source4/heimdal/lib/asn1/der_put.c
[2189/3781] Compiling source4/heimdal/lib/asn1/der_free.c
[2190/3781] Compiling source4/heimdal/lib/asn1/der_format.c
[2191/3781] Compiling source4/heimdal/lib/asn1/der_length.c
[2192/3781] Compiling source4/heimdal/lib/asn1/der_copy.c
[2193/3781] Compiling source4/heimdal/lib/asn1/der_cmp.c
[2194/3781] Compiling source4/heimdal/lib/asn1/extra.c
[2195/3781] Compiling source4/heimdal/lib/asn1/timegm.c
[2196/3781] Compiling default/source4/heimdal/lib/asn1/asn1_err.c
[2197/3781] Compiling default/source4/heimdal/lib/asn1/asn1_rfc2459_asn1.c
[2198/3781] Compiling default/source4/heimdal/lib/asn1/asn1_krb5_asn1.c
[2199/3781] Compiling default/source4/heimdal/lib/asn1/asn1_pkinit_asn1.c
[2200/3781] Compiling default/source4/heimdal/lib/asn1/asn1_cms_asn1.c
[2201/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bncore.c
[2202/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_init.c
[2203/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_clear.c
[2204/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_exch.c
[2205/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_grow.c
[2206/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_shrink.c
[2207/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_clamp.c
[2208/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_zero.c
[2209/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_zero_multi.c
[2210/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_set.c
[2211/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_set_int.c
[2212/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_init_size.c
[2213/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_copy.c
[2214/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_init_copy.c
[2215/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_abs.c
[2216/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_neg.c
[2217/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_cmp_mag.c
[2218/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_cmp.c
[2219/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_cmp_d.c
[2220/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_rshd.c
[2221/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_lshd.c
[2222/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_mod_2d.c
[2223/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_div_2d.c
[2224/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_mul_2d.c
[2225/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_div_2.c
[2226/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_mul_2.c
[2227/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_s_mp_add.c
[2228/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_s_mp_sub.c
[2229/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_fast_s_mp_mul_digs.c
[2230/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_s_mp_mul_digs.c
[2231/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_fast_s_mp_mul_high_digs.c
[2232/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_s_mp_mul_high_digs.c
[2233/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_fast_s_mp_sqr.c
[2234/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_s_mp_sqr.c
[2235/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_add.c
[2236/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_sub.c
[2237/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_karatsuba_mul.c
[2238/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_mul.c
[2239/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_karatsuba_sqr.c
[2240/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_sqr.c
[2241/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_div.c
[2242/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_mod.c
[2243/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_add_d.c
[2244/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_sub_d.c
[2245/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_mul_d.c
[2246/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_div_d.c
[2247/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_mod_d.c
[2248/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_expt_d.c
[2249/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_addmod.c
[2250/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_submod.c
[2251/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_mulmod.c
[2252/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_sqrmod.c
[2253/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_gcd.c
[2254/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_lcm.c
[2255/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_fast_mp_invmod.c
[2256/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_invmod.c
[2257/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_reduce.c
[2258/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_montgomery_setup.c
[2259/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_fast_mp_montgomery_reduce.c
[2260/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_montgomery_reduce.c
[2261/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_exptmod_fast.c
[2262/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_exptmod.c
[2263/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_2expt.c
[2264/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_n_root.c
[2265/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_jacobi.c
[2266/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_reverse.c
[2267/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_count_bits.c
[2268/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_read_unsigned_bin.c
[2269/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_read_signed_bin.c
[2270/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_to_unsigned_bin.c
[2271/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_to_signed_bin.c
[2272/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_unsigned_bin_size.c
[2273/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_signed_bin_size.c
[2274/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_xor.c
[2275/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_and.c
[2276/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_or.c
[2277/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_rand.c
[2278/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_montgomery_calc_normalization.c
[2279/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_prime_is_divisible.c
[2280/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_prime_tab.c
[2281/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_prime_fermat.c
[2282/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_prime_miller_rabin.c
[2283/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_prime_is_prime.c
[2284/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_prime_next_prime.c
[2285/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_find_prime.c
[2286/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_isprime.c
[2287/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_dr_reduce.c
[2288/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_dr_is_modulus.c
[2289/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_dr_setup.c
[2290/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_reduce_setup.c
[2291/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_toom_mul.c
[2292/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_toom_sqr.c
[2293/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_div_3.c
[2294/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_s_mp_exptmod.c
[2295/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_reduce_2k.c
[2296/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_reduce_is_2k.c
[2297/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_reduce_2k_setup.c
[2298/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_reduce_2k_l.c
[2299/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_reduce_is_2k_l.c
[2300/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_reduce_2k_setup_l.c
[2301/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_radix_smap.c
[2302/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_read_radix.c
[2303/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_toradix.c
[2304/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_radix_size.c
[2305/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_fread.c
[2306/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_fwrite.c
[2307/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_cnt_lsb.c
[2308/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_error.c
[2309/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_init_multi.c
[2310/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_clear_multi.c
[2311/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_exteuclid.c
[2312/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_toradix_n.c
[2313/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_prime_random_ex.c
[2314/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_get_int.c
[2315/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_sqrt.c
[2316/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_is_square.c
[2317/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_init_set.c
[2318/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_init_set_int.c
[2319/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_invmod_slow.c
[2320/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_prime_rabin_miller_trials.c
[2321/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_to_signed_bin_n.c
[2322/3781] Compiling source4/heimdal/lib/hcrypto/libtommath/bn_mp_to_unsigned_bin_n.c
[2323/3781] Compiling source4/heimdal/lib/hcrypto/aes.c
[2324/3781] Compiling source4/heimdal/lib/hcrypto/bn.c
[2325/3781] Compiling source4/heimdal/lib/hcrypto/dh.c
[2326/3781] Compiling source4/heimdal/lib/hcrypto/dh-ltm.c
[2327/3781] Compiling source4/heimdal/lib/hcrypto/des.c
[2328/3781] Compiling source4/heimdal/lib/hcrypto/dsa.c
[2329/3781] Compiling source4/heimdal/lib/hcrypto/engine.c
[2330/3781] Compiling source4/heimdal/lib/hcrypto/md2.c
[2331/3781] Compiling source4/heimdal/lib/hcrypto/md4.c
[2332/3781] Compiling source4/heimdal/lib/hcrypto/md5.c
[2333/3781] Compiling source4/heimdal/lib/hcrypto/rsa.c
[2334/3781] Compiling source4/heimdal/lib/hcrypto/rsa-ltm.c
[2335/3781] Compiling source4/heimdal/lib/hcrypto/rc2.c
[2336/3781] Compiling source4/heimdal/lib/hcrypto/rc4.c
[2337/3781] Compiling source4/heimdal/lib/hcrypto/rijndael-alg-fst.c
[2338/3781] Compiling source4/heimdal/lib/hcrypto/rnd_keys.c
[2339/3781] Compiling source4/heimdal/lib/hcrypto/sha.c
[2340/3781] Compiling source4/heimdal/lib/hcrypto/sha256.c
[2341/3781] Compiling source4/heimdal/lib/hcrypto/sha512.c
[2342/3781] Compiling source4/heimdal/lib/hcrypto/ui.c
[2343/3781] Compiling source4/heimdal/lib/hcrypto/evp.c
[2344/3781] Compiling source4/heimdal/lib/hcrypto/evp-hcrypto.c
[2345/3781] Compiling source4/heimdal/lib/hcrypto/pkcs5.c
[2346/3781] Compiling source4/heimdal/lib/hcrypto/pkcs12.c
[2347/3781] Compiling source4/heimdal/lib/hcrypto/rand.c
[2348/3781] Compiling source4/heimdal/lib/hcrypto/rand-egd.c
[2349/3781] Compiling source4/heimdal/lib/hcrypto/rand-unix.c
[2350/3781] Compiling source4/heimdal/lib/hcrypto/rand-fortuna.c
[2351/3781] Compiling source4/heimdal/lib/hcrypto/rand-timer.c
[2352/3781] Compiling source4/heimdal/lib/hcrypto/hmac.c
[2353/3781] Compiling source4/heimdal/lib/hcrypto/camellia.c
[2354/3781] Compiling source4/heimdal/lib/hcrypto/camellia-ntt.c
[2355/3781] Compiling source4/heimdal/lib/hcrypto/common.c
[2356/3781] Compiling source4/heimdal/lib/hcrypto/validate.c
[2357/3781] Compiling source4/heimdal/base/array.c
[2358/3781] Compiling source4/heimdal/base/bool.c
[2359/3781] Compiling source4/heimdal/base/dict.c
[2360/3781] Compiling source4/heimdal/base/heimbase.c
[2361/3781] Compiling source4/heimdal/base/string.c
[2362/3781] Compiling source4/heimdal/base/number.c
[2363/3781] Compiling source4/heimdal/base/null.c
[2364/3781] Compiling default/source4/heimdal/lib/hx509/asn1_ocsp_asn1.c
[2365/3781] Compiling default/source4/heimdal/lib/asn1/asn1_pkcs8_asn1.c
[2366/3781] Compiling default/source4/heimdal/lib/asn1/asn1_pkcs9_asn1.c
[2367/3781] Compiling default/source4/heimdal/lib/asn1/asn1_pkcs12_asn1.c
[2368/3781] Compiling default/source4/heimdal/lib/hx509/asn1_pkcs10_asn1.c
[2369/3781] Compiling source4/heimdal/lib/hx509/ca.c
[2370/3781] Compiling source4/heimdal/lib/hx509/cert.c
[2371/3781] Compiling source4/heimdal/lib/hx509/cms.c
[2372/3781] Compiling source4/heimdal/lib/hx509/collector.c
[2373/3781] Compiling source4/heimdal/lib/hx509/crypto.c
[2374/3781] Compiling source4/heimdal/lib/hx509/error.c
[2375/3781] Compiling source4/heimdal/lib/hx509/env.c
[2376/3781] Compiling source4/heimdal/lib/hx509/file.c
[2377/3781] Compiling source4/heimdal/lib/hx509/keyset.c
[2378/3781] Compiling source4/heimdal/lib/hx509/ks_dir.c
[2379/3781] Compiling source4/heimdal/lib/hx509/ks_file.c
[2380/3781] Compiling source4/heimdal/lib/hx509/ks_keychain.c
[2381/3781] Compiling source4/heimdal/lib/hx509/ks_mem.c
[2382/3781] Compiling source4/heimdal/lib/hx509/ks_null.c
[2383/3781] Compiling source4/heimdal/lib/hx509/ks_p11.c
[2384/3781] Compiling source4/heimdal/lib/hx509/ks_p12.c
[2385/3781] Compiling source4/heimdal/lib/hx509/lock.c
[2386/3781] Compiling source4/heimdal/lib/hx509/name.c
[2387/3781] Compiling source4/heimdal/lib/hx509/peer.c
[2388/3781] Compiling source4/heimdal/lib/hx509/print.c
[2389/3781] Compiling source4/heimdal/lib/hx509/req.c
[2390/3781] Compiling source4/heimdal/lib/hx509/revoke.c
[2391/3781] Compiling source4/heimdal/lib/hx509/sel.c
[2392/3781] Compiling default/source4/heimdal/lib/hx509/hx509_err.c
[2393/3781] Compiling source4/heimdal/lib/hx509/sel-lex.c
[2394/3781] Compiling source4/heimdal/lib/hx509/sel-gram.c
[2395/3781] Compiling default/source4/heimdal/lib/wind/wind_err.c
[2396/3781] Compiling source4/heimdal/lib/wind/stringprep.c
[2397/3781] Compiling source4/heimdal/lib/wind/errorlist.c
[2398/3781] Compiling default/source4/heimdal/lib/wind/errorlist_table.c
[2399/3781] Compiling source4/heimdal/lib/wind/normalize.c
[2400/3781] Compiling default/source4/heimdal/lib/wind/normalize_table.c
[2401/3781] Compiling source4/heimdal/lib/wind/combining.c
[2402/3781] Compiling default/source4/heimdal/lib/wind/combining_table.c
[2403/3781] Compiling source4/heimdal/lib/wind/utf8.c
[2404/3781] Compiling source4/heimdal/lib/wind/bidi.c
[2405/3781] Compiling default/source4/heimdal/lib/wind/bidi_table.c
[2406/3781] Compiling source4/heimdal/lib/wind/ldap.c
[2407/3781] Compiling source4/heimdal/lib/wind/map.c
[2408/3781] Compiling default/source4/heimdal/lib/wind/map_table.c
[2409/3781] Compiling source4/heimdal/kuser/kinit.c
[2410/3781] Compiling source4/heimdal/kuser/kgetcred.c
[2411/3781] Compiling source4/heimdal/kpasswd/kpasswd.c
In file included from ../source4/heimdal/kpasswd/kpasswd_locl.h:96:0,
                 from ../source4/heimdal/kpasswd/kpasswd.c:34:
/usr/include/libutil.h:33:2: warning: #warning "Deprecated header, use <bsd/libutil.h> or libbsd-overlay.pc instead." [-Wcpp]
[2412/3781] Compiling libcli/smbreadline/smbreadline.c
[2413/3781] Compiling libds/common/flag_mapping.c
[2414/3781] Compiling source3/lib/netapi/netapi.c
[2415/3781] Compiling source3/lib/netapi/cm.c
[2416/3781] Compiling source3/lib/netapi/libnetapi.c
[2417/3781] Compiling source3/lib/netapi/joindomain.c
[2418/3781] Compiling source3/lib/netapi/serverinfo.c
[2419/3781] Compiling source3/lib/netapi/getdc.c
[2420/3781] Compiling source3/lib/netapi/user.c
[2421/3781] Compiling source3/lib/netapi/group.c
[2422/3781] Compiling source3/lib/netapi/localgroup.c
[2423/3781] Compiling source3/lib/netapi/samr.c
[2424/3781] Compiling source3/lib/netapi/sid.c
[2425/3781] Compiling source3/lib/netapi/share.c
[2426/3781] Compiling source3/lib/netapi/file.c
[2427/3781] Compiling source3/lib/netapi/shutdown.c
[2428/3781] Compiling source3/lib/netapi/netlogon.c
[2429/3781] Compiling source3/libsmb/smb_share_modes.c
[2430/3781] Compiling nsswitch/wins.c
[2431/3781] Compiling source3/librpc/crypto/gse_krb5.c
[2432/3781] Compiling source3/librpc/crypto/gse.c
[2433/3781] Compiling source3/rpc_client/cli_pipe.c
[2434/3781] Compiling source3/librpc/rpc/rpc_common.c
[2435/3781] Compiling source3/rpc_client/rpc_transport_np.c
[2436/3781] Compiling source3/rpc_client/rpc_transport_sock.c
[2437/3781] Compiling source3/rpc_client/rpc_transport_tstream.c
[2438/3781] Compiling source3/librpc/rpc/dcerpc_helpers.c
[2439/3781] Compiling libgpo/gpo_ldap.c
[2440/3781] Compiling libgpo/gpo_ini.c
[2441/3781] Compiling libgpo/gpo_util.c
[2442/3781] Compiling libgpo/gpo_fetch.c
[2443/3781] Compiling source3/libgpo/gpo_filesync.c
[2444/3781] Compiling libgpo/gpo_sec.c
[2445/3781] Compiling source3/libgpo/gpo_reg.c
[2446/3781] Compiling source3/lib/avahi.c
[2447/3781] Compiling source3/smbd/avahi_register.c
[2448/3781] Compiling source3/groupdb/mapping.c
[2449/3781] Compiling source3/groupdb/mapping_tdb.c
[2450/3781] Compiling source3/lib/tldap.c
[2451/3781] Compiling source3/lib/tldap_util.c
[2452/3781] Compiling source3/lib/util_tsock.c
[2453/3781] Compiling source3/passdb/pdb_get_set.c
[2454/3781] Compiling source3/passdb/passdb.c
[2455/3781] Compiling source3/lib/util_wellknown.c
[2456/3781] Compiling source3/lib/util_builtin.c
[2457/3781] Compiling source3/passdb/pdb_compat.c
[2458/3781] Compiling source3/lib/util_sid_passdb.c
[2459/3781] Compiling source3/lib/util_unixsids.c
[2460/3781] Compiling source3/passdb/lookup_sid.c
[2461/3781] Compiling source3/passdb/login_cache.c
[2462/3781] Compiling source3/passdb/account_pol.c
[2463/3781] Compiling source3/lib/privileges.c
[2464/3781] Compiling source3/lib/util_nscd.c
[2465/3781] Compiling source3/lib/winbind_util.c
[2466/3781] Compiling source3/passdb/pdb_util.c
[2467/3781] Compiling source3/passdb/pdb_interface.c
[2468/3781] Compiling source3/passdb/pdb_secrets.c
[2469/3781] Compiling source3/passdb/pdb_unixid.c
[2470/3781] Compiling source3/passdb/pdb_ldap_schema.c
[2471/3781] Compiling source3/passdb/pdb_ldap_util.c
[2472/3781] Compiling source3/lib/server_mutex.c
[2473/3781] Compiling source3/param/util.c
[2474/3781] Compiling source3/param/loadparm_ctx.c
[2475/3781] Compiling source3/param/loadparm.c
[2476/3781] Compiling source3/lib/sharesec.c
[2477/3781] Compiling source3/lib/ldap_debug_handler.c
[2478/3781] Compiling source3/lib/util_names.c
[2479/3781] Compiling source3/param/pyparam.c
[2480/3781] Compiling source3/param/service.c
[2481/3781] Compiling source3/registry/regfio.c
[2482/3781] Compiling source3/registry/reg_parse_prs.c
[2483/3781] Compiling source3/registry/reg_api_regf.c
[2484/3781] Compiling source3/registry/reg_api.c
[2485/3781] Compiling source3/registry/reg_dispatcher.c
[2486/3781] Compiling source3/registry/reg_cachehook.c
[2487/3781] Compiling source3/registry/reg_objects.c
[2488/3781] Compiling source3/registry/reg_util_internal.c
[2489/3781] Compiling source3/lib/util_nttoken.c
[2490/3781] Compiling source3/registry/reg_backend_db.c
[2491/3781] Compiling source3/registry/reg_parse_internal.c
[2492/3781] Compiling source3/lib/cbuf.c
[2493/3781] Compiling source3/lib/srprs.c
[2494/3781] Compiling source3/registry/reg_init_basic.c
[2495/3781] Compiling source3/registry/reg_backend_smbconf.c
[2496/3781] Compiling source3/registry/reg_init_smbconf.c
[2497/3781] Compiling source3/registry/reg_util_token.c
[2498/3781] Compiling source3/registry/reg_api_util.c
[2499/3781] Compiling source3/registry/reg_backend_printing.c
[2500/3781] Compiling source3/registry/reg_backend_shares.c
[2501/3781] Compiling source3/registry/reg_backend_netlogon_params.c
[2502/3781] Compiling source3/registry/reg_backend_prod_options.c
[2503/3781] Compiling source3/registry/reg_backend_tcpip_params.c
[2504/3781] Compiling source3/registry/reg_backend_hkpt_params.c
[2505/3781] Compiling source3/registry/reg_backend_current_version.c
[2506/3781] Compiling source3/registry/reg_backend_perflib.c
[2507/3781] Compiling source3/registry/reg_init_full.c
[2508/3781] Compiling source3/registry/reg_perfcount.c
[2509/3781] Compiling source3/lib/popt_common.c
[2510/3781] Compiling source3/lib/util_cmdline.c
[2511/3781] Compiling source3/libads/kerberos.c
../source3/libads/kerberos.c: In function âsmb_krb5_get_ntstatus_from_krb5_error_init_creds_optâ:
../source3/libads/kerberos.c:126:2: warning: âkrb5_get_init_creds_opt_get_errorâ is deprecated (declared at default/source4/heimdal/lib/krb5/krb5-protos.h:2004) [-Wdeprecated-declarations]
[2512/3781] Compiling source3/libads/ads_status.c
[2513/3781] Compiling source3/lib/system.c
[2514/3781] Compiling source3/lib/sendfile.c
[2515/3781] Compiling source3/lib/recvfile.c
[2516/3781] Compiling source3/lib/time.c
[2517/3781] Compiling source3/lib/util_sid.c
[2518/3781] Compiling source3/lib/util_file.c
[2519/3781] Compiling source3/lib/util.c
[2520/3781] Compiling source3/lib/util_sock.c
[2521/3781] Compiling source3/lib/util_transfer_file.c
[2522/3781] Compiling source3/lib/sock_exec.c
[2523/3781] Compiling source3/lib/messages.c
[2524/3781] Compiling source3/lib/messages_local.c
[2525/3781] Compiling source3/lib/messages_ctdbd.c
[2526/3781] Compiling source3/lib/ctdb_packet.c
[2527/3781] Compiling source3/lib/ctdbd_conn.c
[2528/3781] Compiling source3/lib/ctdb_conn.c
[2529/3781] Compiling source3/lib/msg_channel.c
[2530/3781] Compiling source3/lib/id_cache.c
[2531/3781] Compiling source3/lib/talloc_dict.c
[2532/3781] Compiling source3/lib/serverid.c
[2533/3781] Compiling source3/lib/addrchange.c
[2534/3781] Compiling source3/lib/dbwrap/dbwrap_open.c
[2535/3781] Compiling source3/lib/dbwrap/dbwrap_ctdb.c
[2536/3781] Compiling source3/lib/dbwrap/dbwrap_watch.c
[2537/3781] Compiling source3/lib/g_lock.c
[2538/3781] Compiling lib/util/debug_s3.c
[2539/3781] Compiling source3/lib/dumpcore.c
[2540/3781] Compiling source3/lib/interface.c
[2541/3781] Compiling source3/lib/username.c
[2542/3781] Compiling source3/lib/access.c
[2543/3781] Compiling source3/lib/smbrun.c
[2544/3781] Compiling source3/lib/wins_srv.c
[2545/3781] Compiling source3/lib/substitute.c
[2546/3781] Compiling source3/lib/substitute_generic.c
[2547/3781] Compiling source3/lib/ms_fnmatch.c
[2548/3781] Compiling source3/lib/tallocmsg.c
[2549/3781] Compiling source3/lib/dmallocmsg.c
[2550/3781] Compiling source3/intl/lang_tdb.c
[2551/3781] Compiling source3/lib/gencache.c
[2552/3781] Compiling source3/lib/events.c
[2553/3781] Compiling source3/lib/server_contexts.c
[2554/3781] Compiling source3/lib/server_prefork.c
[2555/3781] Compiling source3/lib/server_prefork_util.c
[2556/3781] Compiling source3/lib/ldap_escape.c
[2557/3781] Compiling source3/lib/fncall.c
[2558/3781] Compiling source3/libads/krb5_errs.c
[2559/3781] Compiling source3/lib/system_smbd.c
[2560/3781] Compiling source3/lib/audit.c
[2561/3781] Compiling source3/lib/tevent_wait.c
[2562/3781] Compiling source3/lib/idmap_cache.c
[2563/3781] Compiling source3/lib/smbd_shim.c
[2564/3781] Compiling source3/libsmb/ntlmssp.c
[2565/3781] Compiling source3/libsmb/ntlmssp_wrap.c
[2566/3781] Compiling source3/libsmb/auth_generic.c
../source3/libsmb/auth_generic.c: In function âauth_generic_client_prepareâ:
../source3/libsmb/auth_generic.c:90:35: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
../source3/libsmb/auth_generic.c:93:35: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
../source3/libsmb/auth_generic.c:95:35: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
[2567/3781] Compiling source3/libsmb/clientgen.c
[2568/3781] Compiling source3/libsmb/cliconnect.c
[2569/3781] Compiling source3/libsmb/clifile.c
[2570/3781] Compiling source3/libsmb/clispnego.c
[2571/3781] Compiling source3/libsmb/clirap.c
[2572/3781] Compiling source3/libsmb/clierror.c
[2573/3781] Compiling source3/libsmb/climessage.c
[2574/3781] Compiling source3/libsmb/clireadwrite.c
[2575/3781] Compiling source3/libsmb/clilist.c
[2576/3781] Compiling source3/libsmb/cliprint.c
[2577/3781] Compiling source3/libsmb/clitrans.c
[2578/3781] Compiling source3/libsmb/clisecdesc.c
[2579/3781] Compiling source3/libsmb/clidgram.c
[2580/3781] Compiling source3/libsmb/clistr.c
[2581/3781] Compiling source3/libsmb/cliquota.c
[2582/3781] Compiling source3/libsmb/clifsinfo.c
[2583/3781] Compiling source3/libsmb/clidfs.c
[2584/3781] Compiling source3/libsmb/clioplock.c
[2585/3781] Compiling source3/libsmb/clirap2.c
[2586/3781] Compiling source3/libsmb/async_smb.c
[2587/3781] Compiling source3/libsmb/smb2cli_tcon.c
[2588/3781] Compiling source3/libsmb/cli_np_tstream.c
[2589/3781] Compiling source3/libsmb/reparse_symlink.c
[2590/3781] Compiling source3/libsmb/clisymlink.c
[2591/3781] Compiling source3/libsmb/smbsock_connect.c
[2592/3781] Compiling source3/libads/cldap.c
[2593/3781] Compiling source3/passdb/secrets.c
[2594/3781] Compiling source3/passdb/machine_account_secrets.c
[2595/3781] Compiling source3/passdb/machine_sid.c
[2596/3781] Compiling source3/passdb/secrets_lsa.c
[2597/3781] Compiling source3/lib/smbldap.c
[2598/3781] Compiling source3/libads/ldap.c
[2599/3781] Compiling source3/libads/sasl.c
[2600/3781] Compiling source3/libads/sasl_wrapping.c
[2601/3781] Compiling source3/libads/krb5_setpw.c
../source3/libads/krb5_setpw.c: In function âads_krb5_chg_passwordâ:
../source3/libads/krb5_setpw.c:711:5: warning: âkrb5_get_init_creds_opt_initâ is deprecated (declared at default/source4/heimdal/lib/krb5/krb5-protos.h:2011) [-Wdeprecated-declarations]
[2602/3781] Compiling source3/libads/kerberos_util.c
[2603/3781] Compiling source3/libads/ldap_user.c
[2604/3781] Compiling source3/libads/ads_struct.c
[2605/3781] Compiling source3/libads/kerberos_keytab.c
[2606/3781] Compiling source3/libads/disp_sec.c
[2607/3781] Compiling source3/libads/ldap_utils.c
[2608/3781] Compiling source3/libads/ldap_schema.c
[2609/3781] Compiling source3/libads/util.c
[2610/3781] Compiling source3/libads/ndr.c
[2611/3781] Compiling source3/libads/authdata.c
../source3/libads/authdata.c: In function âkerberos_return_pacâ:
../source3/libads/authdata.c:241:35: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
[2612/3781] Compiling source3/libads/ldap_printer.c
[2613/3781] Compiling source3/lib/afs.c
[2614/3781] Compiling source3/lib/afs_settoken.c
[2615/3781] Compiling source3/lib/smbconf/smbconf_init.c
[2616/3781] Compiling source3/lib/smbconf/smbconf_reg.c
[2617/3781] Compiling source3/smbd/conn.c
[2618/3781] Compiling source3/smbd/server_reload.c
[2619/3781] Compiling source3/smbd/files.c
[2620/3781] Compiling source3/smbd/connection.c
[2621/3781] Compiling source3/smbd/utmp.c
[2622/3781] Compiling source3/smbd/session.c
[2623/3781] Compiling source3/smbd/dfree.c
[2624/3781] Compiling source3/smbd/dir.c
[2625/3781] Compiling source3/smbd/password.c
[2626/3781] Compiling source3/smbd/conn_msg.c
[2627/3781] Compiling source3/smbd/conn_idle.c
[2628/3781] Compiling source3/smbd/share_access.c
[2629/3781] Compiling source3/smbd/fileio.c
[2630/3781] Compiling source3/smbd/ipc.c
[2631/3781] Compiling source3/smbd/lanman.c
[2632/3781] Compiling source3/smbd/negprot.c
[2633/3781] Compiling source3/smbd/message.c
[2634/3781] Compiling source3/smbd/nttrans.c
[2635/3781] Compiling source3/smbd/pipes.c
[2636/3781] Compiling source3/smbd/reply.c
[2637/3781] Compiling source3/smbd/sesssetup.c
[2638/3781] Compiling source3/smbd/trans2.c
[2639/3781] Compiling source3/smbd/uid.c
[2640/3781] Compiling source3/smbd/dosmode.c
[2641/3781] Compiling source3/smbd/filename.c
[2642/3781] Compiling source3/smbd/open.c
[2643/3781] Compiling source3/smbd/close.c
[2644/3781] Compiling source3/smbd/blocking.c
[2645/3781] Compiling source3/smbd/sec_ctx.c
[2646/3781] Compiling source3/smbd/srvstr.c
[2647/3781] Compiling source3/smbd/vfs.c
[2648/3781] Compiling source3/smbd/perfcount.c
[2649/3781] Compiling source3/smbd/statcache.c
[2650/3781] Compiling source3/smbd/seal.c
[2651/3781] Compiling source3/smbd/posix_acls.c
[2652/3781] Compiling source3/lib/sysacls.c
[2653/3781] Compiling source3/smbd/process.c
[2654/3781] Compiling source3/smbd/service.c
[2655/3781] Compiling source3/smbd/error.c
[2656/3781] Compiling source3/printing/printspoolss.c
[2657/3781] Compiling source3/printing/spoolssd.c
[2658/3781] Compiling source3/lib/sysquotas.c
[2659/3781] Compiling source3/lib/sysquotas_linux.c
[2660/3781] Compiling source3/lib/sysquotas_xfs.c
[2661/3781] Compiling source3/lib/sysquotas_4A.c
[2662/3781] Compiling source3/lib/sysquotas_4B.c
[2663/3781] Compiling source3/lib/sysquotas_nfs.c
[2664/3781] Compiling source3/lib/background.c
[2665/3781] Compiling source3/lib/sessionid_tdb.c
[2666/3781] Compiling source3/lib/conn_tdb.c
[2667/3781] Compiling source3/smbd/fake_file.c
[2668/3781] Compiling source3/smbd/quotas.c
[2669/3781] Compiling source3/smbd/ntquotas.c
[2670/3781] Compiling source3/smbd/msdfs.c
[2671/3781] Compiling source3/smbd/aio.c
[2672/3781] Compiling source3/smbd/statvfs.c
[2673/3781] Compiling source3/smbd/dmapi.c
[2674/3781] Compiling source3/smbd/signing.c
[2675/3781] Compiling source3/smbd/file_access.c
[2676/3781] Compiling source3/smbd/dnsregister.c
[2677/3781] Compiling source3/smbd/globals.c
[2678/3781] Compiling source3/smbd/smb2_server.c
[2679/3781] Compiling source3/smbd/smb2_glue.c
[2680/3781] Compiling source3/smbd/smb2_negprot.c
[2681/3781] Compiling source3/smbd/smb2_sesssetup.c
[2682/3781] Compiling source3/smbd/smb2_tcon.c
[2683/3781] Compiling source3/smbd/smb2_create.c
[2684/3781] Compiling source3/smbd/smb2_close.c
[2685/3781] Compiling source3/smbd/smb2_flush.c
[2686/3781] Compiling source3/smbd/smb2_read.c
[2687/3781] Compiling source3/smbd/smb2_write.c
[2688/3781] Compiling source3/smbd/smb2_lock.c
[2689/3781] Compiling source3/smbd/smb2_ioctl.c
[2690/3781] Compiling source3/smbd/smb2_keepalive.c
[2691/3781] Compiling source3/smbd/smb2_find.c
[2692/3781] Compiling source3/smbd/smb2_notify.c
[2693/3781] Compiling source3/smbd/smb2_getinfo.c
[2694/3781] Compiling source3/smbd/smb2_setinfo.c
[2695/3781] Compiling source3/smbd/smb2_break.c
[2696/3781] Compiling source3/smbd/smbXsrv_version.c
[2697/3781] Compiling source3/smbd/smbXsrv_session.c
[2698/3781] Compiling source3/smbd/smbXsrv_tcon.c
[2699/3781] Compiling source3/smbd/smbXsrv_open.c
[2700/3781] Compiling source3/smbd/server_exit.c
[2701/3781] Compiling source3/smbd/durable.c
[2702/3781] Compiling source3/smbd/scavenger.c
../source3/smbd/scavenger.c: In function âscavenger_timerâ:
../source3/smbd/scavenger.c:482:3: warning: format â%luâ expects argument of type âlong unsigned intâ, but argument 3 has type âuint64_tâ [-Wformat]
../source3/smbd/scavenger.c:490:3: warning: format â%luâ expects argument of type âlong unsigned intâ, but argument 3 has type âuint64_tâ [-Wformat]
[2703/3781] Compiling source3/smbd/mangle.c
[2704/3781] Compiling source3/smbd/mangle_hash.c
[2705/3781] Compiling source3/smbd/mangle_hash2.c
[2706/3781] Compiling source3/smbd/oplock.c
[2707/3781] Compiling source3/smbd/oplock_irix.c
[2708/3781] Compiling source3/smbd/oplock_linux.c
[2709/3781] Compiling source3/smbd/notify.c
[2710/3781] Compiling source3/smbd/notify_inotify.c
[2711/3781] Compiling source3/smbd/notify_internal.c
[2712/3781] Compiling default/source3/smbd/build_options.c
[2713/3781] Compiling source3/locking/locking.c
[2714/3781] Compiling source3/locking/brlock.c
[2715/3781] Compiling source3/locking/posix.c
[2716/3781] Compiling source3/locking/share_mode_lock.c
[2717/3781] Compiling source3/profile/profile.c
[2718/3781] Compiling source3/printing/notify.c
[2719/3781] Compiling source3/printing/printing_db.c
[2720/3781] Compiling source3/printing/printing.c
[2721/3781] Compiling source3/printing/nt_printing.c
[2722/3781] Compiling source3/printing/nt_printing_tdb.c
[2723/3781] Compiling source3/printing/nt_printing_migrate_internal.c
[2724/3781] Compiling source3/printing/nt_printing_ads.c
[2725/3781] Compiling source3/printing/queue_process.c
[2726/3781] Compiling source3/printing/nt_printing_migrate.c
[2727/3781] Compiling source3/rpc_client/cli_winreg_spoolss.c
[2728/3781] Compiling source3/printing/nt_printing_os2.c
[2729/3781] Compiling source3/printing/pcap.c
[2730/3781] Compiling source3/printing/print_svid.c
[2731/3781] Compiling source3/printing/print_aix.c
[2732/3781] Compiling source3/printing/print_cups.c
[2733/3781] Compiling source3/printing/print_generic.c
[2734/3781] Compiling source3/printing/lpq_parse.c
[2735/3781] Compiling source3/printing/load.c
[2736/3781] Compiling source3/printing/print_standard.c
[2737/3781] Compiling source3/printing/print_iprint.c
[2738/3781] Compiling source3/printing/printer_list.c
[2739/3781] Compiling source3/utils/passwd_util.c
[2740/3781] Compiling source3/lib/filename_util.c
[2741/3781] Compiling source3/libnet/libnet_join.c
[2742/3781] Compiling source3/libnet/libnet_keytab.c
[2743/3781] Compiling source3/libnet/libnet_dssync.c
[2744/3781] Compiling source3/libnet/libnet_dssync_passdb.c
[2745/3781] Compiling source3/libnet/libnet_dssync_keytab.c
[2746/3781] Compiling source3/libnet/libnet_samsync.c
[2747/3781] Compiling source3/libnet/libnet_samsync_ldif.c
[2748/3781] Compiling source3/libnet/libnet_samsync_passdb.c
[2749/3781] Compiling source3/libnet/libnet_samsync_display.c
[2750/3781] Compiling source3/libnet/libnet_samsync_keytab.c
[2751/3781] Compiling source3/lib/eventlog/eventlog.c
[2752/3781] Compiling source3/libsmb/unexpected.c
[2753/3781] Compiling source3/libsmb/namecache.c
[2754/3781] Compiling source3/libsmb/nmblib.c
[2755/3781] Compiling source3/libsmb/namequery.c
[2756/3781] Compiling source3/libsmb/conncache.c
[2757/3781] Compiling source3/libads/sitename_cache.c
[2758/3781] Compiling source3/services/svc_spoolss.c
[2759/3781] Compiling source3/services/svc_rcinit.c
[2760/3781] Compiling source3/services/svc_winreg_glue.c
[2761/3781] Compiling source3/services/svc_netlogon.c
[2762/3781] Compiling source3/services/svc_winreg.c
[2763/3781] Compiling source3/services/svc_wins.c
[2764/3781] Compiling source3/auth/pampass.c
[2765/3781] Compiling source3/auth/pass_check.c
[2766/3781] Compiling source3/libsmb/passchange.c
[2767/3781] Compiling source3/lib/version.c
[2768/3781] Compiling source3/libsmb/samlogon_cache.c
[2769/3781] Compiling source3/libsmb/namequery_dc.c
[2770/3781] Compiling source3/libsmb/trustdom_cache.c
[2771/3781] Compiling source3/libsmb/dsgetdcname.c
[2772/3781] Compiling source3/libsmb/trusts_util.c
[2773/3781] Compiling source3/lib/util_tdb.c
[2774/3781] Compiling source3/lib/util_sec.c
[2775/3781] Compiling source3/lib/util_str.c
[2776/3781] Compiling source3/lib/adt_tree.c
[2777/3781] Compiling source3/lib/util_malloc.c
[2778/3781] Compiling source3/lib/memcache.c
[2779/3781] Compiling source3/lib/namearray.c
[2780/3781] Compiling source3/lib/file_id.c
[2781/3781] Compiling source3/lib/xattr_tdb.c
[2782/3781] Compiling source3/lib/charcnv.c
[2783/3781] Compiling source3/lib/fstring.c
[2784/3781] Compiling source3/libsmb/errormap.c
[2785/3781] Compiling source3/libsmb/smberr.c
[2786/3781] Compiling source3/lib/errmap_unix.c
[2787/3781] Compiling source3/rpc_client/cli_samr.c
[2788/3781] Compiling source3/rpc_client/cli_lsarpc.c
[2789/3781] Compiling source3/rpc_client/cli_netlogon.c
[2790/3781] Compiling source3/rpc_client/util_netlogon.c
[2791/3781] Compiling source3/rpc_client/cli_spoolss.c
[2792/3781] Compiling source3/rpc_client/init_spoolss.c
[2793/3781] Compiling source3/rpc_client/cli_winreg.c
[2794/3781] Compiling source3/rpc_client/cli_winreg_int.c
[2795/3781] Compiling source3/rpc_client/cli_pipe_schannel.c
[2796/3781] Compiling source3/rpc_client/init_lsa.c
[2797/3781] Compiling source3/rpc_client/init_netlogon.c
[2798/3781] Compiling source3/rpc_client/init_samr.c
[2799/3781] Compiling source3/smbd/server.c
[2800/3781] Compiling source3/nmbd/asyncdns.c
[2801/3781] Compiling source3/nmbd/nmbd.c
[2802/3781] Compiling source3/nmbd/nmbd_become_dmb.c
[2803/3781] Compiling source3/nmbd/nmbd_become_lmb.c
[2804/3781] Compiling source3/nmbd/nmbd_browserdb.c
[2805/3781] Compiling source3/nmbd/nmbd_browsesync.c
[2806/3781] Compiling source3/nmbd/nmbd_elections.c
[2807/3781] Compiling source3/nmbd/nmbd_incomingdgrams.c
[2808/3781] Compiling source3/nmbd/nmbd_incomingrequests.c
[2809/3781] Compiling source3/nmbd/nmbd_lmhosts.c
[2810/3781] Compiling source3/nmbd/nmbd_logonnames.c
[2811/3781] Compiling source3/nmbd/nmbd_mynames.c
[2812/3781] Compiling source3/nmbd/nmbd_namelistdb.c
[2813/3781] Compiling source3/nmbd/nmbd_namequery.c
[2814/3781] Compiling source3/nmbd/nmbd_nameregister.c
[2815/3781] Compiling source3/nmbd/nmbd_namerelease.c
[2816/3781] Compiling source3/nmbd/nmbd_nodestatus.c
[2817/3781] Compiling source3/nmbd/nmbd_packets.c
[2818/3781] Compiling source3/nmbd/nmbd_processlogon.c
[2819/3781] Compiling source3/nmbd/nmbd_responserecordsdb.c
[2820/3781] Compiling source3/nmbd/nmbd_sendannounce.c
[2821/3781] Compiling source3/nmbd/nmbd_serverlistdb.c
[2822/3781] Compiling source3/nmbd/nmbd_subnetdb.c
[2823/3781] Compiling source3/nmbd/nmbd_winsproxy.c
[2824/3781] Compiling source3/nmbd/nmbd_winsserver.c
[2825/3781] Compiling source3/nmbd/nmbd_workgroupdb.c
[2826/3781] Compiling source3/nmbd/nmbd_synclists.c
[2827/3781] Compiling source3/winbindd/winbindd.c
[2828/3781] Compiling source3/winbindd/winbindd_group.c
[2829/3781] Compiling source3/winbindd/winbindd_util.c
[2830/3781] Compiling source3/winbindd/winbindd_cache.c
../source3/winbindd/winbindd_cache.c: In function âresolve_username_to_aliasâ:
../source3/winbindd/winbindd_cache.c:1134:3: warning: passing argument 1 of âfreeâ discards âconstâ qualifier from pointer target type [enabled by default]
/usr/include/malloc.h:76:13: note: expected âvoid *â but argument is of type âconst char *â
../source3/winbindd/winbindd_cache.c: In function âresolve_alias_to_usernameâ:
../source3/winbindd/winbindd_cache.c:1212:3: warning: passing argument 1 of âfreeâ discards âconstâ qualifier from pointer target type [enabled by default]
/usr/include/malloc.h:76:13: note: expected âvoid *â but argument is of type âconst char *â
[2831/3781] Compiling source3/winbindd/winbindd_pam.c
[2832/3781] Compiling source3/winbindd/winbindd_misc.c
[2833/3781] Compiling source3/winbindd/winbindd_cm.c
[2834/3781] Compiling source3/winbindd/winbindd_wins_byip.c
[2835/3781] Compiling source3/winbindd/winbindd_wins_byname.c
[2836/3781] Compiling source3/winbindd/winbindd_msrpc.c
[2837/3781] Compiling source3/winbindd/winbindd_rpc.c
[2838/3781] Compiling source3/winbindd/winbindd_reconnect.c
[2839/3781] Compiling source3/winbindd/winbindd_ads.c
[2840/3781] Compiling source3/winbindd/winbindd_samr.c
[2841/3781] Compiling source3/winbindd/winbindd_dual.c
[2842/3781] Compiling source3/winbindd/winbindd_dual_ndr.c
[2843/3781] Compiling source3/winbindd/winbindd_dual_srv.c
[2844/3781] Compiling source3/winbindd/winbindd_async.c
[2845/3781] Compiling source3/winbindd/winbindd_creds.c
[2846/3781] Compiling source3/winbindd/winbindd_cred_cache.c
[2847/3781] Compiling source3/winbindd/winbindd_ccache_access.c
[2848/3781] Compiling source3/winbindd/winbindd_domain.c
[2849/3781] Compiling source3/winbindd/winbindd_idmap.c
[2850/3781] Compiling source3/winbindd/winbindd_locator.c
[2851/3781] Compiling source3/winbindd/winbindd_ndr.c
[2852/3781] Compiling source3/winbindd/wb_ping.c
[2853/3781] Compiling source3/winbindd/wb_lookupsid.c
[2854/3781] Compiling source3/winbindd/wb_lookupsids.c
[2855/3781] Compiling source3/winbindd/wb_lookupname.c
[2856/3781] Compiling source3/winbindd/wb_uid2sid.c
[2857/3781] Compiling source3/winbindd/wb_gid2sid.c
[2858/3781] Compiling source3/winbindd/wb_sids2xids.c
[2859/3781] Compiling source3/winbindd/wb_queryuser.c
[2860/3781] Compiling source3/winbindd/wb_lookupuseraliases.c
[2861/3781] Compiling source3/winbindd/wb_lookupusergroups.c
[2862/3781] Compiling source3/winbindd/wb_getpwsid.c
[2863/3781] Compiling source3/winbindd/wb_gettoken.c
[2864/3781] Compiling source3/winbindd/wb_seqnum.c
[2865/3781] Compiling source3/winbindd/wb_seqnums.c
[2866/3781] Compiling source3/winbindd/wb_group_members.c
[2867/3781] Compiling source3/winbindd/wb_getgrsid.c
../source3/winbindd/wb_getgrsid.c: In function âwb_getgrsid_sid2gid_doneâ:
../source3/winbindd/wb_getgrsid.c:170:12: warning: passing argument 3 of âadd_wbint_Principal_to_dictâ from incompatible pointer type [enabled by default]
../source3/winbindd/winbindd_proto.h:646:10: note: expected âconst char **â but argument is of type âchar **â
[2868/3781] Compiling source3/winbindd/wb_query_user_list.c
[2869/3781] Compiling source3/winbindd/wb_fill_pwent.c
[2870/3781] Compiling source3/winbindd/wb_next_pwent.c
[2871/3781] Compiling source3/winbindd/wb_next_grent.c
[2872/3781] Compiling source3/winbindd/wb_dsgetdcname.c
[2873/3781] Compiling source3/winbindd/winbindd_lookupsid.c
[2874/3781] Compiling source3/winbindd/winbindd_lookupsids.c
[2875/3781] Compiling source3/winbindd/winbindd_lookupname.c
[2876/3781] Compiling source3/winbindd/winbindd_sid_to_uid.c
[2877/3781] Compiling source3/winbindd/winbindd_sid_to_gid.c
[2878/3781] Compiling source3/winbindd/winbindd_uid_to_sid.c
[2879/3781] Compiling source3/winbindd/winbindd_gid_to_sid.c
[2880/3781] Compiling source3/winbindd/winbindd_sids_to_xids.c
[2881/3781] Compiling source3/winbindd/winbindd_allocate_uid.c
[2882/3781] Compiling source3/winbindd/winbindd_allocate_gid.c
[2883/3781] Compiling source3/winbindd/winbindd_getpwsid.c
[2884/3781] Compiling source3/winbindd/winbindd_getpwnam.c
[2885/3781] Compiling source3/winbindd/winbindd_getpwuid.c
[2886/3781] Compiling source3/winbindd/winbindd_getsidaliases.c
[2887/3781] Compiling source3/winbindd/winbindd_getuserdomgroups.c
[2888/3781] Compiling source3/winbindd/winbindd_getgroups.c
[2889/3781] Compiling source3/winbindd/winbindd_show_sequence.c
[2890/3781] Compiling source3/winbindd/winbindd_getgrgid.c
[2891/3781] Compiling source3/winbindd/winbindd_getgrnam.c
[2892/3781] Compiling source3/winbindd/winbindd_getusersids.c
[2893/3781] Compiling source3/winbindd/winbindd_lookuprids.c
[2894/3781] Compiling source3/winbindd/winbindd_setpwent.c
[2895/3781] Compiling source3/winbindd/winbindd_getpwent.c
[2896/3781] Compiling source3/winbindd/winbindd_endpwent.c
[2897/3781] Compiling source3/winbindd/winbindd_setgrent.c
[2898/3781] Compiling source3/winbindd/winbindd_getgrent.c
[2899/3781] Compiling source3/winbindd/winbindd_endgrent.c
[2900/3781] Compiling source3/winbindd/winbindd_dsgetdcname.c
[2901/3781] Compiling source3/winbindd/winbindd_getdcname.c
[2902/3781] Compiling source3/winbindd/winbindd_list_users.c
[2903/3781] Compiling source3/winbindd/winbindd_list_groups.c
[2904/3781] Compiling source3/winbindd/winbindd_check_machine_acct.c
[2905/3781] Compiling source3/winbindd/winbindd_change_machine_acct.c
[2906/3781] Compiling source3/winbindd/winbindd_ping_dc.c
[2907/3781] Compiling source3/winbindd/winbindd_pam_auth.c
[2908/3781] Compiling source3/winbindd/winbindd_pam_logoff.c
[2909/3781] Compiling source3/winbindd/winbindd_pam_chauthtok.c
[2910/3781] Compiling source3/winbindd/winbindd_pam_auth_crap.c
[2911/3781] Compiling source3/winbindd/winbindd_pam_chng_pswd_auth_crap.c
[2912/3781] Compiling source3/lib/tdb_validate.c
[2913/3781] Compiling source3/web/cgi.c
[2914/3781] Compiling source3/web/diagnose.c
[2915/3781] Compiling source3/web/startstop.c
[2916/3781] Compiling source3/web/statuspage.c
[2917/3781] Compiling source3/web/swat.c
[2918/3781] Compiling source3/web/neg_lang.c
[2919/3781] Compiling source3/rpcclient/rpcclient.c
[2920/3781] Compiling source3/rpcclient/cmd_lsarpc.c
[2921/3781] Compiling source3/rpcclient/cmd_samr.c
[2922/3781] Compiling source3/rpcclient/cmd_spoolss.c
[2923/3781] Compiling source3/rpcclient/cmd_netlogon.c
[2924/3781] Compiling source3/rpcclient/cmd_srvsvc.c
[2925/3781] Compiling source3/rpcclient/cmd_dfs.c
[2926/3781] Compiling source3/rpcclient/cmd_epmapper.c
[2927/3781] Compiling source3/rpcclient/cmd_dssetup.c
[2928/3781] Compiling source3/rpcclient/cmd_echo.c
[2929/3781] Compiling source3/rpcclient/cmd_shutdown.c
[2930/3781] Compiling source3/rpcclient/cmd_test.c
[2931/3781] Compiling source3/rpcclient/cmd_wkssvc.c
[2932/3781] Compiling source3/rpcclient/cmd_ntsvcs.c
[2933/3781] Compiling source3/rpcclient/cmd_drsuapi.c
[2934/3781] Compiling source3/rpcclient/cmd_eventlog.c
[2935/3781] Compiling source3/rpcclient/cmd_winreg.c
[2936/3781] Compiling source3/rpcclient/cmd_fss.c
[2937/3781] Compiling source3/client/client.c
[2938/3781] Compiling source3/client/clitar.c
[2939/3781] Compiling source3/client/dnsbrowse.c
[2940/3781] Compiling source3/utils/net.c
[2941/3781] Compiling source3/utils/net_ads.c
[2942/3781] Compiling source3/utils/net_help.c
[2943/3781] Compiling source3/utils/net_rap.c
[2944/3781] Compiling source3/utils/net_rpc.c
[2945/3781] Compiling source3/utils/net_rpc_samsync.c
[2946/3781] Compiling source3/utils/net_rpc_join.c
[2947/3781] Compiling source3/utils/net_time.c
[2948/3781] Compiling source3/utils/net_lookup.c
[2949/3781] Compiling source3/utils/net_cache.c
[2950/3781] Compiling source3/utils/net_groupmap.c
[2951/3781] Compiling source3/utils/net_idmap.c
[2952/3781] Compiling source3/utils/net_idmap_check.c
[2953/3781] Compiling source3/utils/interact.c
[2954/3781] Compiling source3/utils/net_status.c
[2955/3781] Compiling source3/utils/net_rpc_printer.c
[2956/3781] Compiling source3/utils/net_rpc_rights.c
[2957/3781] Compiling source3/utils/net_rpc_service.c
[2958/3781] Compiling source3/utils/net_rpc_registry.c
[2959/3781] Compiling source3/utils/net_usershare.c
[2960/3781] Compiling source3/utils/netlookup.c
[2961/3781] Compiling source3/utils/net_sam.c
[2962/3781] Compiling source3/utils/net_rpc_shell.c
[2963/3781] Compiling source3/utils/net_util.c
[2964/3781] Compiling source3/utils/net_rpc_sh_acct.c
[2965/3781] Compiling source3/utils/net_rpc_audit.c
[2966/3781] Compiling source3/utils/net_dns.c
[2967/3781] Compiling source3/utils/net_ads_gpo.c
[2968/3781] Compiling source3/utils/net_conf.c
[2969/3781] Compiling source3/utils/net_join.c
[2970/3781] Compiling source3/utils/net_user.c
[2971/3781] Compiling source3/utils/net_group.c
[2972/3781] Compiling source3/utils/net_file.c
[2973/3781] Compiling source3/utils/net_registry.c
[2974/3781] Compiling source3/utils/net_registry_check.c
[2975/3781] Compiling source3/utils/net_dom.c
[2976/3781] Compiling source3/utils/net_share.c
[2977/3781] Compiling source3/utils/net_g_lock.c
[2978/3781] Compiling source3/utils/net_serverid.c
[2979/3781] Compiling source3/utils/net_eventlog.c
[2980/3781] Compiling source3/utils/net_printing.c
[2981/3781] Compiling source3/utils/net_rpc_trust.c
[2982/3781] Compiling source3/utils/net_rpc_conf.c
[2983/3781] Compiling source3/registry/reg_parse.c
[2984/3781] Compiling source3/registry/reg_format.c
[2985/3781] Compiling source3/registry/reg_import.c
[2986/3781] Compiling source3/utils/net_registry_util.c
[2987/3781] Compiling source3/utils/net_help_common.c
[2988/3781] Compiling source3/utils/profiles.c
[2989/3781] Compiling source3/client/smbspool.c
[2990/3781] Compiling source3/utils/testparm.c
[2991/3781] Compiling source3/utils/smbta-util.c
[2992/3781] Compiling source3/utils/status.c
[2993/3781] Compiling source3/utils/status_profile.c
[2994/3781] Compiling source3/smbd/notify_internal.c
[2995/3781] Compiling source3/utils/smbcontrol.c
[2996/3781] Compiling source3/utils/smbtree.c
[2997/3781] Compiling source3/utils/smbpasswd.c
[2998/3781] Compiling source3/utils/pdbedit.c
[2999/3781] Compiling source3/utils/smbget.c
[3000/3781] Compiling source3/utils/nmblookup.c
[3001/3781] Compiling source3/torture/torture.c
[3002/3781] Compiling source3/torture/nbio.c
[3003/3781] Compiling source3/torture/scanner.c
[3004/3781] Compiling source3/torture/utable.c
[3005/3781] Compiling source3/torture/denytest.c
[3006/3781] Compiling source3/torture/mangle_test.c
[3007/3781] Compiling source3/torture/nbench.c
[3008/3781] Compiling source3/torture/test_async_echo.c
[3009/3781] Compiling source3/torture/test_addrchange.c
[3010/3781] Compiling source3/torture/test_posix_append.c
[3011/3781] Compiling source3/torture/test_nttrans_create.c
[3012/3781] Compiling source3/torture/test_nttrans_fsctl.c
[3013/3781] Compiling source3/torture/test_case_insensitive.c
[3014/3781] Compiling source3/torture/test_notify_online.c
[3015/3781] Compiling source3/torture/test_chain3.c
[3016/3781] Compiling source3/torture/test_smb2.c
[3017/3781] Compiling source3/torture/test_authinfo_structs.c
In file included from ../source3/torture/test_authinfo_structs.c:24:0:
../libcli/lsarpc/util_lsarpc.h:32:17: warning: âstruct trustAuthInOutBlobâ declared inside parameter list [enabled by default]
../libcli/lsarpc/util_lsarpc.h:32:17: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
[3018/3781] Compiling source3/torture/test_smbsock_any_connect.c
[3019/3781] Compiling source3/torture/test_cleanup.c
[3020/3781] Compiling source3/torture/test_ctdbconn.c
[3021/3781] Compiling source3/torture/test_msg.c
[3022/3781] Compiling source3/torture/test_notify.c
[3023/3781] Compiling source3/lib/tevent_barrier.c
[3024/3781] Compiling source3/torture/test_dbwrap_watch.c
[3025/3781] Compiling source3/torture/test_idmap_tdb_common.c
[3026/3781] Compiling source3/torture/t_strappend.c
[3027/3781] Compiling source3/torture/wbc_async.c
[3028/3781] Compiling source3/lib/smbconf/testsuite.c
[3029/3781] Compiling lib/replace/test/main.c
[3030/3781] Compiling source3/torture/msgtest.c
[3031/3781] Compiling source3/utils/smbcacls.c
[3032/3781] Compiling source3/utils/smbcquotas.c
[3033/3781] Compiling source3/utils/eventlogadm.c
[3034/3781] Compiling source3/utils/sharesec.c
[3035/3781] Compiling source3/torture/pdbtest.c
[3036/3781] Compiling source3/torture/cmd_vfs.c
[3037/3781] Compiling source3/torture/vfstest.c
../source3/torture/vfstest.c: In function âmainâ:
../source3/torture/vfstest.c:471:3: warning: initialization makes â__attribute__((noreturn))â qualified function pointer from unqualified [enabled by default]
../source3/torture/vfstest.c:472:3: warning: initialization makes â__attribute__((noreturn))â qualified function pointer from unqualified [enabled by default]
[3038/3781] Compiling source3/torture/vfstest_chain.c
[3039/3781] Compiling source3/utils/log2pcaphex.c
[3040/3781] Compiling source3/torture/locktest2.c
[3041/3781] Compiling source3/utils/debug2html.c
[3042/3781] Compiling source3/utils/debugparse.c
[3043/3781] Compiling source3/utils/smbfilter.c
[3044/3781] Compiling source3/lib/version_test.c
[3045/3781] Compiling source3/utils/ntlm_auth.c
../source3/utils/ntlm_auth.c: In function ântlm_auth_start_ntlmssp_serverâ:
../source3/utils/ntlm_auth.c:1094:35: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
../source3/utils/ntlm_auth.c:1097:35: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
../source3/utils/ntlm_auth.c:1099:35: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
[3046/3781] Compiling source3/utils/ntlm_auth_diagnostics.c
[3047/3781] Compiling source3/script/tests/timelimit.c
[3048/3781] Compiling source3/torture/rpc_open_tcp.c
[3049/3781] Compiling source3/param/test_lp_load.c
[3050/3781] Compiling source3/utils/dbwrap_tool.c
[3051/3781] Compiling source3/utils/dbwrap_torture.c
[3052/3781] Compiling source3/utils/split_tokens.c
[3053/3781] Compiling source3/printing/tests/vlp.c
[3054/3781] Compiling source3/smbd/pysmbd.c
In file included from /usr/include/python2.7/Python.h:8:0,
                 from ../source3/smbd/pysmbd.c:28:
/usr/include/python2.7/pyconfig.h:1161:0: warning: "_POSIX_C_SOURCE" redefined [enabled by default]
/usr/include/features.h:164:0: note: this is the location of the previous definition
/usr/include/python2.7/pyconfig.h:1183:0: warning: "_XOPEN_SOURCE" redefined [enabled by default]
/usr/include/features.h:166:0: note: this is the location of the previous definition
[3055/3781] Compiling source3/libsmb/pylibsmb.c
[3056/3781] Compiling source3/auth/token_util.c
[3057/3781] Compiling source3/auth/user_util.c
[3058/3781] Compiling source3/auth/auth_util.c
[3059/3781] Compiling source3/auth/check_samsec.c
[3060/3781] Compiling source3/auth/server_info.c
[3061/3781] Compiling source3/auth/server_info_sam.c
[3062/3781] Compiling source3/auth/user_info.c
[3063/3781] Compiling source3/auth/auth.c
[3064/3781] Compiling source3/auth/user_krb5.c
[3065/3781] Compiling source3/auth/auth_ntlmssp.c
[3066/3781] Compiling source3/auth/auth_generic.c
../source3/auth/auth_generic.c: In function âauth_generic_prepareâ:
../source3/auth/auth_generic.c:273:36: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
../source3/auth/auth_generic.c:276:36: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
../source3/auth/auth_generic.c:278:36: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
[3067/3781] Compiling source3/auth/auth_sam.c
[3068/3781] Compiling source3/auth/auth_unix.c
[3069/3781] Compiling source3/auth/auth_winbind.c
[3070/3781] Compiling source3/auth/auth_wbc.c
[3071/3781] Compiling source3/auth/auth_domain.c
[3072/3781] Compiling source3/auth/auth_builtin.c
[3073/3781] Compiling source3/auth/auth_script.c
[3074/3781] Compiling source3/auth/auth_samba4.c
[3075/3781] Compiling libgpo/gpext/gpext.c
[3076/3781] Compiling source3/lib/pthreadpool/pthreadpool.c
[3077/3781] Compiling source3/lib/pthreadpool/tests.c
[3078/3781] Compiling source3/lib/asys/asys.c
[3079/3781] Compiling source3/lib/asys/tests.c
[3080/3781] Compiling default/source3/librpc/gen_ndr/ndr_libnetapi.c
[3081/3781] Compiling default/source3/librpc/gen_ndr/ndr_libnet_join.c
[3082/3781] Compiling default/source3/librpc/gen_ndr/ndr_messaging.c
[3083/3781] Compiling default/source3/librpc/gen_ndr/ndr_open_files.c
[3084/3781] Compiling default/source3/librpc/gen_ndr/ndr_smbXsrv.c
[3085/3781] Compiling default/source3/librpc/gen_ndr/ndr_secrets.c
[3086/3781] Compiling default/source3/librpc/gen_ndr/ndr_perfcount.c
[3087/3781] Compiling default/source3/librpc/gen_ndr/ndr_wbint.c
[3088/3781] Compiling default/source3/librpc/gen_ndr/ndr_wbint_c.c
[3089/3781] Compiling default/source3/librpc/gen_ndr/srv_wbint.c
[3090/3781] Compiling source3/libsmb/libsmb_cache.c
[3091/3781] Compiling source3/libsmb/libsmb_compat.c
[3092/3781] Compiling source3/libsmb/libsmb_context.c
[3093/3781] Compiling source3/libsmb/libsmb_dir.c
../source3/libsmb/libsmb_dir.c: In function âSMBC_getdents_ctxâ:
../source3/libsmb/libsmb_dir.c:1128:23: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
[3094/3781] Compiling source3/libsmb/libsmb_file.c
[3095/3781] Compiling source3/libsmb/libsmb_misc.c
[3096/3781] Compiling source3/libsmb/libsmb_path.c
[3097/3781] Compiling source3/libsmb/libsmb_printjob.c
[3098/3781] Compiling source3/libsmb/libsmb_server.c
[3099/3781] Compiling source3/libsmb/libsmb_stat.c
[3100/3781] Compiling source3/libsmb/libsmb_xattr.c
[3101/3781] Compiling source3/libsmb/libsmb_setget.c
[3102/3781] Compiling source3/modules/nfs4_acls.c
[3103/3781] Compiling source3/modules/vfs_default.c
[3104/3781] Compiling source3/modules/vfs_audit.c
[3105/3781] Compiling source3/modules/vfs_extd_audit.c
[3106/3781] Compiling source3/modules/vfs_full_audit.c
[3107/3781] Compiling source3/modules/vfs_fake_perms.c
[3108/3781] Compiling source3/modules/vfs_recycle.c
[3109/3781] Compiling source3/modules/vfs_netatalk.c
[3110/3781] Compiling source3/modules/vfs_default_quota.c
[3111/3781] Compiling source3/modules/vfs_readonly.c
[3112/3781] Compiling source3/modules/getdate.c
[3113/3781] Compiling source3/modules/vfs_cap.c
[3114/3781] Compiling source3/modules/vfs_expand_msdfs.c
[3115/3781] Compiling source3/modules/vfs_shadow_copy.c
[3116/3781] Compiling source3/modules/vfs_shadow_copy2.c
[3117/3781] Compiling source3/modules/vfs_xattr_tdb.c
[3118/3781] Compiling source3/modules/vfs_posix_eadb.c
[3119/3781] Compiling source3/modules/vfs_posixacl.c
[3120/3781] Compiling source3/modules/vfs_catia.c
[3121/3781] Compiling source3/modules/vfs_streams_xattr.c
[3122/3781] Compiling source3/modules/vfs_streams_depot.c
[3123/3781] Compiling source3/modules/vfs_commit.c
[3124/3781] Compiling source3/modules/vfs_readahead.c
[3125/3781] Compiling source3/modules/vfs_fileid.c
[3126/3781] Compiling source3/modules/vfs_aio_fork.c
[3127/3781] Compiling source3/modules/vfs_aio_pthread.c
[3128/3781] Compiling source3/modules/vfs_aio_posix.c
[3129/3781] Compiling source3/modules/vfs_aio_linux.c
[3130/3781] Compiling source3/modules/vfs_preopen.c
[3131/3781] Compiling source3/modules/vfs_syncops.c
[3132/3781] Compiling source3/modules/vfs_acl_xattr.c
[3133/3781] Compiling source3/modules/vfs_acl_tdb.c
[3134/3781] Compiling source3/modules/vfs_smb_traffic_analyzer.c
../source3/modules/vfs_smb_traffic_analyzer.c: In function âsmb_traffic_analyzer_encryptâ:
../source3/modules/vfs_smb_traffic_analyzer.c:190:2: warning: passing argument 2 of âsamba_AES_encryptâ discards âconstâ qualifier from pointer target type [enabled by default]
../source3/../lib/crypto/aes.h:68:6: note: expected âunsigned char *â but argument is of type âconst unsigned char *â
[3135/3781] Compiling source3/modules/vfs_dirsort.c
[3136/3781] Compiling source3/modules/vfs_scannedonly.c
[3137/3781] Compiling source3/modules/vfs_crossrename.c
[3138/3781] Compiling source3/modules/vfs_linux_xfs_sgid.c
[3139/3781] Compiling source3/modules/vfs_time_audit.c
[3140/3781] Compiling source3/modules/vfs_media_harmony.c
../source3/modules/vfs_media_harmony.c: In function âstarts_with_media_dirâ:
../source3/modules/vfs_media_harmony.c:201:14: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
../source3/modules/vfs_media_harmony.c:204:14: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
../source3/modules/vfs_media_harmony.c: In function âdepth_from_media_dirâ:
../source3/modules/vfs_media_harmony.c:277:14: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
../source3/modules/vfs_media_harmony.c:280:14: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
[3141/3781] Compiling source3/modules/vfs_dfs_samba4.c
[3142/3781] Compiling source3/pam_smbpass/pam_smb_auth.c
[3143/3781] Compiling source3/pam_smbpass/pam_smb_passwd.c
[3144/3781] Compiling source3/pam_smbpass/pam_smb_acct.c
[3145/3781] Compiling source3/pam_smbpass/support.c
[3146/3781] Compiling source3/passdb/pdb_tdb.c
[3147/3781] Compiling source3/passdb/pdb_ldap.c
[3148/3781] Compiling source3/passdb/pdb_nds.c
[3149/3781] Compiling source3/passdb/pdb_ipa.c
[3150/3781] Compiling source3/passdb/pdb_smbpasswd.c
[3151/3781] Compiling source3/passdb/pdb_wbc_sam.c
[3152/3781] Compiling source3/passdb/pdb_samba_dsdb.c
../source3/passdb/pdb_samba_dsdb.c: In function âpdb_samba_dsdb_sid_to_idâ:
../source3/passdb/pdb_samba_dsdb.c:2068:13: warning: assignment discards âconstâ qualifier from pointer target type [enabled by default]
[3153/3781] Compiling source3/passdb/py_passdb.c
[3154/3781] Compiling source3/rpc_server/rpc_config.c
[3155/3781] Compiling source3/rpc_server/rpc_ncacn_np.c
[3156/3781] Compiling source3/rpc_server/rpc_handles.c
[3157/3781] Compiling source3/rpc_server/rpc_contexts.c
[3158/3781] Compiling source3/rpc_server/rpc_server.c
[3159/3781] Compiling source3/rpc_server/dcesrv_auth_generic.c
[3160/3781] Compiling source3/rpc_server/srv_pipe_register.c
[3161/3781] Compiling source3/rpc_server/rpc_ep_register.c
[3162/3781] Compiling source3/librpc/rpc/dcerpc_ep.c
[3163/3781] Compiling source3/rpc_server/epmd.c
[3164/3781] Compiling source3/rpc_server/lsasd.c
[3165/3781] Compiling source3/rpc_server/srv_access_check.c
[3166/3781] Compiling source3/rpc_server/samr/srv_samr_nt.c
[3167/3781] Compiling source3/rpc_server/samr/srv_samr_util.c
[3168/3781] Compiling source3/rpc_server/samr/srv_samr_chgpasswd.c
[3169/3781] Compiling default/librpc/gen_ndr/srv_samr.c
[3170/3781] Compiling source3/rpc_server/lsa/srv_lsa_nt.c
[3171/3781] Compiling default/librpc/gen_ndr/srv_lsa.c
[3172/3781] Compiling source3/rpc_server/winreg/srv_winreg_nt.c
[3173/3781] Compiling default/librpc/gen_ndr/srv_winreg.c
[3174/3781] Compiling source3/rpc_server/initshutdown/srv_initshutdown_nt.c
[3175/3781] Compiling default/librpc/gen_ndr/srv_initshutdown.c
[3176/3781] Compiling source3/rpc_server/dssetup/srv_dssetup_nt.c
[3177/3781] Compiling default/librpc/gen_ndr/srv_dssetup.c
[3178/3781] Compiling source3/rpc_server/wkssvc/srv_wkssvc_nt.c
[3179/3781] Compiling default/librpc/gen_ndr/srv_wkssvc.c
[3180/3781] Compiling source3/rpc_server/svcctl/srv_svcctl_nt.c
[3181/3781] Compiling source3/rpc_server/svcctl/srv_svcctl_reg.c
[3182/3781] Compiling default/librpc/gen_ndr/srv_svcctl.c
[3183/3781] Compiling source3/rpc_server/ntsvcs/srv_ntsvcs_nt.c
[3184/3781] Compiling default/librpc/gen_ndr/srv_ntsvcs.c
[3185/3781] Compiling source3/rpc_server/netlogon/srv_netlog_nt.c
[3186/3781] Compiling default/librpc/gen_ndr/srv_netlogon.c
[3187/3781] Compiling source3/rpc_server/dfs/srv_dfs_nt.c
[3188/3781] Compiling default/librpc/gen_ndr/srv_dfs.c
[3189/3781] Compiling source3/rpc_server/srvsvc/srv_srvsvc_nt.c
[3190/3781] Compiling default/librpc/gen_ndr/srv_srvsvc.c
[3191/3781] Compiling source3/rpc_server/spoolss/srv_spoolss_nt.c
[3192/3781] Compiling default/librpc/gen_ndr/srv_spoolss.c
[3193/3781] Compiling source3/rpc_server/spoolss/srv_spoolss_util.c
[3194/3781] Compiling source3/rpc_server/eventlog/srv_eventlog_nt.c
[3195/3781] Compiling source3/rpc_server/eventlog/srv_eventlog_reg.c
[3196/3781] Compiling default/librpc/gen_ndr/srv_eventlog.c
[3197/3781] Compiling source3/rpc_server/echo/srv_echo_nt.c
[3198/3781] Compiling default/librpc/gen_ndr/srv_echo.c
[3199/3781] Compiling source3/rpc_server/epmapper/srv_epmapper.c
[3200/3781] Compiling default/librpc/gen_ndr/srv_epmapper.c
[3201/3781] Compiling source3/rpc_server/srv_pipe_hnd.c
[3202/3781] Compiling source3/rpc_server/srv_pipe.c
In file included from ../source3/rpc_server/srv_pipe.c:37:0:
../source3/rpc_server/rpc_server.h:58:5: warning: âenum dcerpc_transport_tâ declared inside parameter list [enabled by default]
../source3/rpc_server/rpc_server.h:58:5: warning: its scope is only this definition or declaration, which is probably not what you want [enabled by default]
[3203/3781] Compiling source3/rpc_server/rpc_sock_helper.c
[3204/3781] Compiling source3/rpc_server/rpc_service_setup.c
[3205/3781] Compiling source3/winbindd/idmap.c
[3206/3781] Compiling source3/winbindd/idmap_util.c
[3207/3781] Compiling source3/winbindd/idmap_tdb_common.c
[3208/3781] Compiling source3/winbindd/idmap_rw.c
[3209/3781] Compiling source3/winbindd/idmap_hash/idmap_hash.c
[3210/3781] Compiling source3/winbindd/idmap_hash/mapfile.c
[3211/3781] Compiling source3/winbindd/idmap_ad.c
[3212/3781] Compiling source3/winbindd/idmap_rid.c
[3213/3781] Compiling source3/winbindd/idmap_passdb.c
[3214/3781] Compiling source3/winbindd/idmap_ldap.c
[3215/3781] Compiling source3/winbindd/idmap_nss.c
[3216/3781] Compiling source3/winbindd/idmap_tdb.c
[3217/3781] Compiling source3/winbindd/idmap_tdb2.c
[3218/3781] Compiling source3/winbindd/idmap_autorid.c
[3219/3781] Compiling source3/winbindd/nss_info.c
[3220/3781] Compiling source3/winbindd/nss_info_template.c
[3221/3781] Compiling examples/libsmbclient/testsmbc.c
[3222/3781] Compiling examples/libsmbclient/testacl.c
[3223/3781] Compiling examples/libsmbclient/testacl2.c
[3224/3781] Compiling examples/libsmbclient/testacl3.c
[3225/3781] Compiling examples/libsmbclient/testbrowse.c
[3226/3781] Compiling examples/libsmbclient/testbrowse2.c
[3227/3781] Compiling examples/libsmbclient/teststat.c
[3228/3781] Compiling examples/libsmbclient/teststat2.c
[3229/3781] Compiling examples/libsmbclient/teststat3.c
[3230/3781] Compiling examples/libsmbclient/teststatvfs.c
[3231/3781] Compiling examples/libsmbclient/testfstatvfs.c
[3232/3781] Compiling examples/libsmbclient/testtruncate.c
[3233/3781] Compiling examples/libsmbclient/testchmod.c
[3234/3781] Compiling examples/libsmbclient/testutime.c
[3235/3781] Compiling examples/libsmbclient/testread.c
[3236/3781] Compiling examples/libsmbclient/testwrite.c
[3237/3781] Compiling examples/libsmbclient/testctx.c
[3238/3781] Compiling source3/lib/netapi/tests/netapitest.c
[3239/3781] Compiling source3/lib/netapi/tests/netlocalgroup.c
[3240/3781] Compiling source3/lib/netapi/tests/netuser.c
[3241/3781] Compiling source3/lib/netapi/tests/netgroup.c
[3242/3781] Compiling source3/lib/netapi/tests/netdisplay.c
[3243/3781] Compiling source3/lib/netapi/tests/netshare.c
[3244/3781] Compiling source3/lib/netapi/tests/netfile.c
[3245/3781] Compiling source3/lib/netapi/tests/netserver.c
[3246/3781] Compiling source3/lib/netapi/tests/common.c
[3247/3781] Compiling source3/lib/netapi/examples/common.c
[3248/3781] Compiling source3/lib/netapi/examples/getdc/getdc.c
[3249/3781] Compiling source3/lib/netapi/examples/dsgetdc/dsgetdc.c
[3250/3781] Compiling source3/lib/netapi/examples/join/netdomjoin.c
[3251/3781] Compiling source3/lib/netapi/examples/join/getjoinableous.c
[3252/3781] Compiling source3/lib/netapi/examples/join/getjoininformation.c
[3253/3781] Compiling source3/lib/netapi/examples/join/rename_machine.c
[3254/3781] Compiling source3/lib/netapi/examples/user/user_add.c
[3255/3781] Compiling source3/lib/netapi/examples/user/user_del.c
[3256/3781] Compiling source3/lib/netapi/examples/user/user_enum.c
[3257/3781] Compiling source3/lib/netapi/examples/user/user_dispinfo.c
[3258/3781] Compiling source3/lib/netapi/examples/user/user_chgpwd.c
[3259/3781] Compiling source3/lib/netapi/examples/user/user_getinfo.c
[3260/3781] Compiling source3/lib/netapi/examples/user/user_setinfo.c
[3261/3781] Compiling source3/lib/netapi/examples/user/user_modalsget.c
[3262/3781] Compiling source3/lib/netapi/examples/user/user_modalsset.c
[3263/3781] Compiling source3/lib/netapi/examples/user/user_getgroups.c
[3264/3781] Compiling source3/lib/netapi/examples/user/user_setgroups.c
[3265/3781] Compiling source3/lib/netapi/examples/user/user_getlocalgroups.c
[3266/3781] Compiling source3/lib/netapi/examples/group/group_add.c
[3267/3781] Compiling source3/lib/netapi/examples/group/group_del.c
[3268/3781] Compiling source3/lib/netapi/examples/group/group_enum.c
[3269/3781] Compiling source3/lib/netapi/examples/group/group_setinfo.c
[3270/3781] Compiling source3/lib/netapi/examples/group/group_getinfo.c
[3271/3781] Compiling source3/lib/netapi/examples/group/group_adduser.c
[3272/3781] Compiling source3/lib/netapi/examples/group/group_deluser.c
[3273/3781] Compiling source3/lib/netapi/examples/group/group_getusers.c
[3274/3781] Compiling source3/lib/netapi/examples/group/group_setusers.c
[3275/3781] Compiling source3/lib/netapi/examples/localgroup/localgroup_add.c
[3276/3781] Compiling source3/lib/netapi/examples/localgroup/localgroup_del.c
[3277/3781] Compiling source3/lib/netapi/examples/localgroup/localgroup_getinfo.c
[3278/3781] Compiling source3/lib/netapi/examples/localgroup/localgroup_setinfo.c
[3279/3781] Compiling source3/lib/netapi/examples/localgroup/localgroup_enum.c
[3280/3781] Compiling source3/lib/netapi/examples/localgroup/localgroup_addmembers.c
[3281/3781] Compiling source3/lib/netapi/examples/localgroup/localgroup_delmembers.c
[3282/3781] Compiling source3/lib/netapi/examples/localgroup/localgroup_setmembers.c
[3283/3781] Compiling source3/lib/netapi/examples/localgroup/localgroup_getmembers.c
[3284/3781] Compiling source3/lib/netapi/examples/server/remote_tod.c
[3285/3781] Compiling source3/lib/netapi/examples/server/server_getinfo.c
[3286/3781] Compiling source3/lib/netapi/examples/share/share_add.c
[3287/3781] Compiling source3/lib/netapi/examples/share/share_del.c
[3288/3781] Compiling source3/lib/netapi/examples/share/share_enum.c
[3289/3781] Compiling source3/lib/netapi/examples/share/share_getinfo.c
[3290/3781] Compiling source3/lib/netapi/examples/share/share_setinfo.c
[3291/3781] Compiling source3/lib/netapi/examples/file/file_close.c
[3292/3781] Compiling source3/lib/netapi/examples/file/file_getinfo.c
[3293/3781] Compiling source3/lib/netapi/examples/file/file_enum.c
[3294/3781] Compiling source3/lib/netapi/examples/shutdown/shutdown_init.c
[3295/3781] Compiling source3/lib/netapi/examples/shutdown/shutdown_abort.c
[3296/3781] Compiling source3/lib/netapi/examples/netlogon/netlogon_control.c
[3297/3781] Compiling source3/lib/netapi/examples/netlogon/netlogon_control2.c
[3298/3781] Compiling source3/lib/netapi/examples/netlogon/nltest.c
[3299/3781] Compiling dfs_server/dfs_server_ad.c
[3300/3781] Compiling file_server/file_server.c
[3301/3781] Compiling lib/krb5_wrap/krb5_samba.c
[3302/3781] Compiling lib/krb5_wrap/gss_samba.c
[3303/3781] Compiling lib/krb5_wrap/keytab_util.c
[3304/3781] Compiling lib/krb5_wrap/enctype_convert.c
[3305/3781] Linking default/lib/util/libutil_setid.so
[3306/3781] Linking default/lib/talloc/libtalloc.so
[3307/3781] Linking default/lib/talloc/libpytalloc-util.so
[3308/3781] Linking default/lib/talloc/pytalloc.so
[3309/3781] Linking default/lib/tevent/libtevent.so
[3310/3781] Linking default/lib/tevent/pytevent.so
[3311/3781] Linking default/source4/heimdal_build/libroken-samba4.so
[3312/3781] Linking default/source4/heimdal_build/libasn1-samba4.so
[3313/3781] Linking default/source4/heimdal_build/libhcrypto-samba4.so
[3314/3781] Linking default/source4/heimdal_build/libwind-samba4.so
[3315/3781] Linking default/lib/ccan/libccan.so
[3316/3781] Linking default/lib/tdb/libtdb.so
[3317/3781] Linking default/lib/tdb/pytdb.so
[3318/3781] Linking default/lib/tdb_compat/libtdb_compat.so
[3319/3781] Linking default/lib/ldb/libldb.so
[3320/3781] Linking default/lib/ldb/libldb-paged-results.so
[3321/3781] Linking default/lib/ldb/libldb-asq.so
[3322/3781] Linking default/lib/ldb/libldb-server-sort.so
[3323/3781] Linking default/lib/ldb/libldb-paged-searches.so
[3324/3781] Linking default/lib/ldb/libldb-rdn-name.so
[3325/3781] Linking default/lib/ldb/libldb-sample.so
[3326/3781] Linking default/lib/ldb/libldb-skel.so
[3327/3781] Linking default/lib/ldb/libldb-tdb.so
[3328/3781] Linking default/lib/ldb/libldb-cmdline.so
[3329/3781] Linking default/source3/libsmbd_shim.so
[3330/3781] Linking default/nsswitch/libwinbind-client.so
[3331/3781] Linking default/nsswitch/libnss-wrapper-winbind.so
[3332/3781] Linking default/nsswitch/libnss-winbind.so
[3333/3781] Linking default/lib/iniparser/src/libiniparser.so
[3334/3781] Linking default/lib/subunit/c/libsubunit.so
[3335/3781] Linking default/source3/libsmbsharemodes.so
[3336/3781] Linking default/nsswitch/libwbclient/libwbclient.so
[3337/3781] Linking default/lib/ldb/libpyldb-util.so
[3338/3781] Linking default/source4/heimdal_build/libhx509-samba4.so
[3339/3781] Linking default/source4/heimdal_build/libheimbase-samba4.so
[3340/3781] Linking default/lib/util/libsamba-util.so
[3341/3781] Linking default/lib/socket/libinterfaces.so
[3342/3781] Linking default/libcli/util/liberrors.so
[3343/3781] Linking default/librpc/libndr.so
[3344/3781] Linking default/source4/heimdal_build/libkrb5-samba4.so
[3345/3781] Linking default/lib/ldb/pyldb.so
[3346/3781] Linking default/lib/param/libserver-role.so
[3347/3781] Linking default/libds/common/libflag_mapping.so
[3348/3781] Linking default/lib/util/libsamba-modules.so
[3349/3781] Linking default/source4/lib/samba3/libsmbpasswdparser.so
[3350/3781] Linking default/source3/libsamba3-util.so
[3351/3781] Linking default/source3/libCHARSET3.so
[3352/3781] Linking default/nsswitch/libwinbind-krb5-locator.so
[3353/3781] Linking default/source4/heimdal_build/libgssapi-samba4.so
[3354/3781] Linking default/lib/param/libsamba-hostconfig.so
[3355/3781] Linking default/libcli/security/libsamba-security.so
[3356/3781] Linking default/source4/lib/events/libevents.so
[3357/3781] Linking default/lib/util/libutil_tdb.so
[3358/3781] Linking default/auth/libauth_sam_reply.so
[3359/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-ranged-results.so
[3360/3781] Linking default/nsswitch/libpamwinbind.so
[3361/3781] Linking default/source4/heimdal_build/libheimntlm-samba4.so
[3362/3781] Linking default/source3/libsmbd_conn.so
[3363/3781] Linking default/source4/heimdal_build/libhdb-samba4.so
[3364/3781] Linking default/libcli/registry/libutil_reg.so
[3365/3781] Linking default/lib/util/libtevent-util.so
[3366/3781] Linking default/lib/util/libasn1util.so
[3367/3781] Linking default/lib/tdb_wrap/libtdb-wrap.so
[3368/3781] Linking default/lib/addns/libaddns.so
[3369/3781] Linking default/libcli/ldap/libcli-ldap-common.so
[3370/3781] Linking default/source4/lib/socket/libnetif.so
[3371/3781] Linking default/source4/param/pyparam.so
[3372/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samba3sam.so
[3373/3781] Linking default/lib/torture/libtorture.so
[3374/3781] Linking default/lib/dbwrap/libdbwrap.so
[3375/3781] Linking default/source4/nbt_server/libldb-wins-ldb.so
[3376/3781] Linking default/source4/heimdal_build/libkdc-samba4.so
[3377/3781] Linking default/source4/ntvfs/posix/libposix_eadb.so
[3378/3781] Linking default/source4/cluster/libcluster.so
[3379/3781] Linking default/libcli/security/pysecurity.so
[3380/3781] Linking default/librpc/libndr-nbt.so
[3381/3781] Linking default/libcli/smb/libsmb_transport.so
[3382/3781] Linking default/lib/krb5_wrap/libkrb5samba.so
[3383/3781] Linking default/lib/libsamba-sockets.so
[3384/3781] Linking default/librpc/libdcerpc-binding.so
[3385/3781] Linking default/source3/libsmbregistry.so
[3386/3781] Linking default/libcli/nbt/libcli-nbt.so
[3387/3781] Linking default/source4/smbd/libprocess_model.so
[3388/3781] Linking default/librpc/libndr-standard.so
[3389/3781] Linking default/libcli/nbt/python-netbios.so
[3390/3781] Linking default/librpc/libndr-krb5pac.so
[3391/3781] Linking default/librpc/libndr-samba.so
[3392/3781] Linking default/source4/librpc/libndr-samba4.so
[3393/3781] Linking default/libcli/auth/libcliauth.so
[3394/3781] Linking default/librpc/libdcerpc-samba.so
[3395/3781] Linking default/source4/auth/kerberos/libauthkrb5.so
[3396/3781] Linking default/libcli/named_pipe_auth/libnpa_tstream.so
[3397/3781] Linking default/source3/liblibcli_lsa3.so
[3398/3781] Linking default/source3/libxattr_tdb.so
[3399/3781] Linking default/source4/lib/com/pycom.so
[3400/3781] Linking default/source4/dsdb/libsamdb-common.so
[3401/3781] Linking default/lib/ldb-samba/libldbsamba.so
[3402/3781] Linking default/source4/smbd/libprocess-model-prefork.so
[3403/3781] Linking default/source4/smbd/libprocess-model-standard.so
[3404/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-simple-ldap-map.so
[3405/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-subtree-rename.so
[3406/3781] Linking default/auth/credentials/libsamba-credentials.so
[3407/3781] Linking default/source4/dsdb/libsamdb.so
[3408/3781] Linking default/dfs_server/libdfs_server_ad.so
[3409/3781] Linking default/source4/smbd/libprocess-model-onefork.so
[3410/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-local-password.so
[3411/3781] Linking default/source4/lib/cmdline/libcmdline-credentials.so
[3412/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-objectclass-attrs.so
[3413/3781] Linking default/auth/gensec/libgensec.so
[3414/3781] Linking default/lib/ldb-samba/libldbsamba-extensions.so
[3415/3781] Linking default/source4/dns_server/libdlz-bind9-9.so
[3416/3781] Linking default/source4/kdc/libdb-glue.so
[3417/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samba-secrets.so
[3418/3781] Linking default/source4/kdc/libpac.so
[3419/3781] Linking default/source4/auth/gensec/libgensec-krb5.so
[3420/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-resolve-oids.so
[3421/3781] Linking default/source4/kdc/libHDB_SAMBA4.so
[3422/3781] Linking default/source4/param/libshares.so
[3423/3781] Linking default/libcli/smb/libcli_smb_common.so
[3424/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-anr.so
[3425/3781] Linking default/source4/libcli/ldap/libcli-ldap.so
[3426/3781] Linking default/source4/kdc/libmit-samba.so
[3427/3781] Linking default/source4/dns_server/libdlz_bind9_for_torture.so
[3428/3781] Linking default/source4/dns_server/libdlz-bind9.so
[3429/3781] Linking default/source3/libsmbconf.so
[3430/3781] Linking default/source3/winbindd/libnss_info.so
[3431/3781] Linking default/source3/libsmbldap.so
[3432/3781] Linking default/source4/libcli/libsmbclient-raw.so
[3433/3781] Linking default/source3/libsecrets3.so
[3434/3781] Linking default/source3/libsmbldaphelper.so
[3435/3781] Linking default/source3/libutil_cmdline.so
[3436/3781] Linking default/source3/winbindd/libnss-info-hash.so
[3437/3781] Linking default/lib/ldb-samba/libldb-ildap.so
[3438/3781] Linking default/source3/libpdb.so
[3439/3781] Linking default/source3/pam_smbpass/libpamsmbpass.so
[3440/3781] Linking default/source3/libcli_spoolss.so
[3441/3781] Linking default/libcli/cldap/libcli_cldap.so
[3442/3781] Linking default/source3/pys3param.so
[3443/3781] Linking default/source4/librpc/libdcerpc.so
[3444/3781] Linking default/source3/liblibcli_netlogon3.so
[3445/3781] Linking default/source3/libgse.so
[3446/3781] Linking default/source3/winbindd/libidmap.so
[3447/3781] Linking default/source4/lib/registry/libregistry.so
[3448/3781] Linking default/source3/libpopt_samba3.so
[3449/3781] Linking default/source4/librpc/libdcerpc-atsvc.so
[3450/3781] Linking default/source3/libprinting_migrate.so
[3451/3781] Linking default/source4/librpc/libdcerpc-samba4.so
[3452/3781] Linking default/source4/librpc/libdcerpc-samr.so
[3453/3781] Linking default/source4/lib/messaging/libMESSAGING.so
[3454/3781] Linking default/source3/winbindd/libidmap-tdb2.so
[3455/3781] Linking default/source3/winbindd/libidmap-rid.so
[3456/3781] Linking default/source3/liblibsmb.so
[3457/3781] Linking default/source4/libcli/wbclient/libLIBWBCLIENT_OLD.so
[3458/3781] Linking default/python/libsamba_python.so
[3459/3781] Linking default/source4/libcli/pysmb.so
[3460/3781] Linking default/source4/librpc/python-dcerpc-smb-acl.so
[3461/3781] Linking default/source4/librpc/python-srvsvc.so
[3462/3781] Linking default/source4/dsdb/samdb/ldb_modules/libdsdb-module.so
[3463/3781] Linking default/source4/libnet/libsamba-net.so
[3464/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-schema-load.so
[3465/3781] Linking default/source4/libnet/python-dckeytab.so
[3466/3781] Linking default/source4/lib/messaging/python-messaging.so
[3467/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-password-hash.so
[3468/3781] Linking default/source4/dsdb/python-dsdb.so
[3469/3781] Linking default/source4/librpc/python-dcerpc-misc.so
[3470/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-objectguid.so
[3471/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-objectclass.so
[3472/3781] Linking default/source4/librpc/python-unixinfo.so
[3473/3781] Linking default/source4/librpc/python-dcerpc-xattr.so
[3474/3781] Linking default/source4/librpc/python-lsa.so
[3475/3781] Linking default/source4/librpc/python-dcerpc-nbt.so
[3476/3781] Linking default/source4/librpc/python-dcerpc-drsblobs.so
[3477/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-simple-dn.so
[3478/3781] Linking default/source3/winbindd/libidmap-hash.so
[3479/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-repl-meta-data.so
[3480/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samba-dsdb.so
[3481/3781] Linking default/source4/librpc/python-dcerpc-dnsp.so
[3482/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-extended-dn-in.so
[3483/3781] Linking default/source4/librpc/python-atsvc.so
[3484/3781] Linking default/source3/winbindd/libidmap-autorid.so
[3485/3781] Linking default/auth/credentials/pycredentials.so
[3486/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-show-deleted.so
[3487/3781] Linking default/source3/libnss-wins.so
[3488/3781] Linking default/source4/librpc/python-auth.so
[3489/3781] Linking default/source4/librpc/python-idmap.so
[3490/3781] Linking default/source4/librpc/python-winbind.so
[3491/3781] Linking default/source4/ntvfs/posix/python-posix-eadb.so
[3492/3781] Linking default/source3/libmsrpc3.so
[3493/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-subtree-delete.so
[3494/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-extended-dn-out.so
[3495/3781] Linking default/source4/librpc/python-samr.so
[3496/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-acl.so
[3497/3781] Linking default/source4/librpc/python-dfs.so
[3498/3781] Linking default/source4/librpc/python-dcerpc.so
[3499/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-dirsync.so
[3500/3781] Linking default/source3/libads.so
[3501/3781] Linking default/source4/librpc/python-echo.so
[3502/3781] Linking default/source4/librpc/python-netlogon.so
[3503/3781] Linking default/source4/librpc/python-dcerpc-idmap.so
[3504/3781] Linking default/source4/librpc/python-initshutdown.so
[3505/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-extended-dn-store.so
[3506/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-operational.so
[3507/3781] Linking default/source4/lib/policy/libsamba-policy.so
[3508/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-secrets-tdb-sync.so
[3509/3781] Linking default/source4/librpc/python-mgmt.so
[3510/3781] Linking default/lib/ldb-samba/python-samba--ldb.so
[3511/3781] Linking default/source4/librpc/python-winreg.so
[3512/3781] Linking default/source4/librpc/python-drsuapi.so
[3513/3781] Linking default/source4/ntvfs/posix/python-xattr-tdb.so
[3514/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-instancetype.so
[3515/3781] Linking default/python/python-glue.so
[3516/3781] Linking default/source4/libnet/python-net.so
[3517/3781] Linking default/source4/librpc/python-dnsserver.so
[3518/3781] Linking default/source4/librpc/python-krb5pac.so
[3519/3781] Linking default/source4/ntvfs/posix/python-xattr-native.so
[3520/3781] Linking default/source4/auth/libauth_unix_token.so
[3521/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-partition.so
[3522/3781] Linking default/source4/auth/ntlm/libauth4.so
[3523/3781] Linking default/source4/lib/policy/py-policy.so
[3524/3781] Linking default/source3/libtrusts_util.so
[3525/3781] Linking default/source4/auth/pyauth.so
[3526/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-descriptor.so
[3527/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samba3sid.so
[3528/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-rootdse.so
[3529/3781] Linking default/source4/librpc/python-wkssvc.so
[3530/3781] Linking default/source4/lib/registry/py-registry.so
[3531/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-schema-data.so
[3532/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samldb.so
[3533/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-aclread.so
[3534/3781] Linking default/source4/auth/gensec/pygensec.so
[3535/3781] Linking default/source4/librpc/python-server-id.so
[3536/3781] Linking default/source4/librpc/python-dcerpc-security.so
[3537/3781] Linking default/source4/librpc/python-svcctl.so
[3538/3781] Linking default/source4/librpc/python-epmapper.so
[3539/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-new-partition.so
[3540/3781] Linking default/source3/libsmb/libsmbclient.so
[3541/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-linked-attributes.so
[3542/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-lazy-commit.so
[3543/3781] Linking default/source4/smbd/libservice.so
[3544/3781] Linking default/source4/librpc/python-irpc.so
[3545/3781] Linking default/source4/librpc/python-dns.so
[3546/3781] Linking default/source3/passdb/pypassdb.so
[3547/3781] Linking default/source4/dsdb/samdb/ldb_modules/libldb-update-keytab.so
[3548/3781] Linking default/source4/dsdb/libservice-dns-update.so
[3549/3781] Linking default/source4/kdc/libservice-kdc.so
[3550/3781] Linking default/source3/libnet_keytab.so
[3551/3781] Linking default/source4/wrepl_server/libservice-wrepl.so
[3552/3781] Linking default/source4/ntvfs/libntvfs.so
[3553/3781] Linking default/source4/cldap_server/libservice-cldap.so
[3554/3781] Linking default/source4/ldap_server/libservice-ldap.so
[3555/3781] Linking default/source3/auth/libauth.so
[3556/3781] Linking default/source4/ntp_signd/libservice-ntp-signd.so
[3557/3781] Linking default/source3/libnetapi.so
[3558/3781] Linking default/source4/smb_server/libservice-smb.so
[3559/3781] Linking default/source4/dsdb/libservice-kcc.so
[3560/3781] Linking default/source4/dsdb/libservice-drepl.so
[3561/3781] Linking default/source3/pylibsmb.so
[3562/3781] Linking default/source4/winbind/libservice-winbind.so
[3563/3781] Linking default/source3/libgpo.so
[3564/3781] Linking default/source4/nbt_server/libservice-nbtd.so
[3565/3781] Linking default/source4/web_server/libservice-web.so
[3566/3781] Linking default/file_server/libservice-s3fs.so
[3567/3781] Linking default/source4/dns_server/libservice-dns.so
[3568/3781] Linking default/source3/libsmbd_base.so
[3569/3781] Linking default/source4/rpc_server/libdcerpc-server.so
[3570/3781] Linking default/source3/modules/libvfs-recycle.so
[3571/3781] Linking default/source3/modules/libvfs-default-quota.so
[3572/3781] Linking default/source3/modules/libvfs-smb-traffic-analyzer.so
[3573/3781] Linking default/source3/modules/libvfs-linux-xfs-sgid.so
[3574/3781] Linking default/source3/modules/libvfs-expand-msdfs.so
[3575/3781] Linking default/source3/modules/libvfs-acl-xattr.so
[3576/3781] Linking default/source3/modules/libvfs-media-harmony.so
[3577/3781] Linking default/source3/auth/libauth-script.so
[3578/3781] Linking default/source3/modules/libvfs-readonly.so
[3579/3781] Linking default/source3/modules/libvfs-readahead.so
[3580/3781] Linking default/source3/modules/libvfs-aio-pthread.so
[3581/3781] Linking default/source3/modules/libvfs-preopen.so
[3582/3781] Linking default/source3/modules/libvfs-streams-depot.so
[3583/3781] Linking default/source3/modules/libvfs-aio-linux.so
[3584/3781] Linking default/source3/modules/libvfs-acl-tdb.so
[3585/3781] Linking default/source3/modules/libvfs-audit.so
[3586/3781] Linking default/source3/modules/libvfs-scannedonly.so
[3587/3781] Linking default/source3/modules/libvfs-fake-perms.so
[3588/3781] Linking default/source4/rpc_server/libservice-dcerpc.so
[3589/3781] Linking default/source3/modules/libvfs-crossrename.so
[3590/3781] Linking default/source3/modules/libvfs-shadow-copy2.so
[3591/3781] Linking default/source3/modules/libvfs-xattr-tdb.so
[3592/3781] Linking default/source3/modules/libvfs-dirsort.so
[3593/3781] Linking default/source3/modules/libvfs-catia.so
[3594/3781] Linking default/source3/modules/libvfs-full-audit.so
[3595/3781] Linking default/source3/modules/libvfs-shadow-copy.so
[3596/3781] Linking default/source3/modules/libvfs-fileid.so
[3597/3781] Linking default/source3/modules/libvfs-time-audit.so
[3598/3781] Linking default/source3/modules/libvfs-posix-eadb.so
[3599/3781] Linking default/source3/modules/libvfs-netatalk.so
[3600/3781] Linking default/source3/modules/libvfs-streams-xattr.so
[3601/3781] Linking default/source3/modules/libvfs-aio-posix.so
[3602/3781] Linking default/source3/modules/libvfs-extd-audit.so
[3603/3781] Linking default/source3/modules/libvfs-commit.so
[3604/3781] Linking default/source3/modules/libvfs-syncops.so
[3605/3781] Linking default/source3/modules/libvfs-aio-fork.so
[3606/3781] Linking default/source3/modules/libvfs-cap.so
[3607/3781] Linking default/source3/pysmbd.so
[3608/3781] Linking default/lib/tdb/tdbtorture
[3609/3781] Linking default/lib/tdb/tdbrestore
[3610/3781] Linking default/lib/tdb/tdbdump
[3611/3781] Linking default/lib/tdb/tdbbackup
[3612/3781] Linking default/lib/tdb/tdbtool
[3613/3781] Linking default/lib/tdb/tdb1-run-3G-file
[3614/3781] Linking default/lib/tdb/tdb1-run-bad-tdb-header
[3615/3781] Linking default/lib/tdb/tdb1-run
[3616/3781] Linking default/lib/tdb/tdb1-run-check
[3617/3781] Linking default/lib/tdb/tdb1-run-corrupt
[3618/3781] Linking default/lib/tdb/tdb1-run-die-during-transaction
[3619/3781] Linking default/lib/tdb/tdb1-run-endian
[3620/3781] Linking default/lib/tdb/tdb1-run-incompatible
[3621/3781] Linking default/lib/tdb/tdb1-run-nested-transactions
[3622/3781] Linking default/lib/tdb/tdb1-run-nested-traverse
[3623/3781] Linking default/lib/tdb/tdb1-run-no-lock-during-traverse
[3624/3781] Linking default/lib/tdb/tdb1-run-oldhash
[3625/3781] Linking default/lib/tdb/tdb1-run-open-during-transaction
[3626/3781] Linking default/lib/tdb/tdb1-run-readonly-check
[3627/3781] Linking default/lib/tdb/tdb1-run-rescue
[3628/3781] Linking default/lib/tdb/tdb1-run-rescue-find_entry
[3629/3781] Linking default/lib/tdb/tdb1-run-rwlock-check
[3630/3781] Linking default/lib/tdb/tdb1-run-summary
[3631/3781] Linking default/lib/tdb/tdb1-run-transaction-expand
[3632/3781] Linking default/lib/tdb/tdb1-run-traverse-in-transaction
[3633/3781] Linking default/lib/tdb/tdb1-run-wronghash-fail
[3634/3781] Linking default/lib/tdb/tdb1-run-zero-append
[3635/3781] Linking default/lib/ldb/ldbadd
[3636/3781] Linking default/lib/ldb/ldbsearch
[3637/3781] Linking default/lib/ldb/ldbdel
[3638/3781] Linking default/lib/ldb/ldbmodify
[3639/3781] Linking default/lib/ldb/ldbedit
[3640/3781] Linking default/lib/ldb/ldbrename
[3641/3781] Linking default/lib/ldb/ldbtest
[3642/3781] Linking default/lib/ldb/ldbdump
[3643/3781] Linking default/librpc/tools/ndrdump
[3644/3781] Linking default/source4/smbd/samba
[3645/3781] Linking default/nsswitch/nsstest
[3646/3781] Linking default/nsswitch/wbinfo
[3647/3781] Linking default/source4/lib/registry/regdiff
[3648/3781] Linking default/source4/lib/registry/regpatch
[3649/3781] Linking default/source4/lib/registry/regshell
[3650/3781] Linking default/source4/lib/registry/regtree
[3651/3781] Linking default/source4/utils/ntlm_auth4
[3652/3781] Linking default/source4/utils/oLschema2ldif
[3653/3781] Linking default/source4/torture/smbtorture
[3654/3781] Linking default/source4/torture/gentest
[3655/3781] Linking default/source4/torture/masktest
[3656/3781] Linking default/source4/torture/locktest
[3657/3781] Linking default/source4/client/smbclient4
[3658/3781] Linking default/source4/client/cifsdd
[3659/3781] Linking default/libcli/nbt/nmblookup4
[3660/3781] Linking default/source4/heimdal_build/rkpty
[3661/3781] Linking default/source4/heimdal_build/samba4kinit
[3662/3781] Linking default/source4/heimdal_build/samba4kgetcred
[3663/3781] Linking default/source4/heimdal_build/samba4kpasswd
[3664/3781] Linking default/source3/smbd/smbd
[3665/3781] Linking default/source3/nmbd/nmbd
[3666/3781] Linking default/source3/winbindd/winbindd
[3667/3781] Linking default/source3/web/swat
[3668/3781] Linking default/source3/rpcclient/rpcclient
[3669/3781] Linking default/source3/client/smbclient
[3670/3781] Linking default/source3/net
[3671/3781] Linking default/source3/profiles
[3672/3781] Linking default/source3/smbspool
[3673/3781] Linking default/source3/testparm
[3674/3781] Linking default/source3/smbta-util
[3675/3781] Linking default/source3/smbstatus
[3676/3781] Linking default/source3/smbcontrol
[3677/3781] Linking default/source3/smbtree
[3678/3781] Linking default/source3/smbpasswd
[3679/3781] Linking default/source3/pdbedit
[3680/3781] Linking default/source3/smbget
[3681/3781] Linking default/source3/nmblookup
[3682/3781] Linking default/source3/smbtorture3
[3683/3781] Linking default/source3/smbconftort
[3684/3781] Linking default/source3/replacetort
[3685/3781] Linking default/source3/msgtest
[3686/3781] Linking default/source3/smbcacls
[3687/3781] Linking default/source3/smbcquotas
[3688/3781] Linking default/source3/eventlogadm
[3689/3781] Linking default/source3/sharesec
[3690/3781] Linking default/source3/pdbtest
[3691/3781] Linking default/source3/vfstest
[3692/3781] Linking default/source3/log2pcap
[3693/3781] Linking default/source3/locktest2
[3694/3781] Linking default/source3/debug2html
[3695/3781] Linking default/source3/smbfilter
[3696/3781] Linking default/source3/versiontest
[3697/3781] Linking default/source3/ntlm_auth
[3698/3781] Linking default/source3/timelimit
[3699/3781] Linking default/source3/rpc_open_tcp
[3700/3781] Linking default/source3/test_lp_load
[3701/3781] Linking default/source3/dbwrap_tool
[3702/3781] Linking default/source3/dbwrap_torture
[3703/3781] Linking default/source3/split_tokens
[3704/3781] Linking default/source3/vlp
[3705/3781] Linking default/source3/lib/pthreadpool/pthreadpooltest
[3706/3781] Linking default/source3/lib/asys/asystest
[3707/3781] Linking default/examples/libsmbclient/testsmbc
[3708/3781] Linking default/examples/libsmbclient/testacl
[3709/3781] Linking default/examples/libsmbclient/testacl2
[3710/3781] Linking default/examples/libsmbclient/testacl3
[3711/3781] Linking default/examples/libsmbclient/testbrowse
[3712/3781] Linking default/examples/libsmbclient/testbrowse2
[3713/3781] Linking default/examples/libsmbclient/teststat
[3714/3781] Linking default/examples/libsmbclient/teststat2
[3715/3781] Linking default/examples/libsmbclient/teststat3
[3716/3781] Linking default/examples/libsmbclient/teststatvfs
[3717/3781] Linking default/examples/libsmbclient/testfstatvfs
[3718/3781] Linking default/examples/libsmbclient/testtruncate
[3719/3781] Linking default/examples/libsmbclient/testchmod
[3720/3781] Linking default/examples/libsmbclient/testutime
[3721/3781] Linking default/examples/libsmbclient/testread
[3722/3781] Linking default/examples/libsmbclient/testwrite
[3723/3781] Linking default/examples/libsmbclient/testctx
[3724/3781] Linking default/source3/lib/netapi/tests/netapitest
[3725/3781] Linking default/source3/lib/netapi/examples/getdc/getdc
[3726/3781] Linking default/source3/lib/netapi/examples/dsgetdc/dsgetdc
[3727/3781] Linking default/source3/lib/netapi/examples/join/netdomjoin
[3728/3781] Linking default/source3/lib/netapi/examples/join/getjoinableous
[3729/3781] Linking default/source3/lib/netapi/examples/join/getjoininformation
[3730/3781] Linking default/source3/lib/netapi/examples/join/rename_machine
[3731/3781] Linking default/source3/lib/netapi/examples/user/user_add
[3732/3781] Linking default/source3/lib/netapi/examples/user/user_del
[3733/3781] Linking default/source3/lib/netapi/examples/user/user_enum
[3734/3781] Linking default/source3/lib/netapi/examples/user/user_dispinfo
[3735/3781] Linking default/source3/lib/netapi/examples/user/user_chgpwd
[3736/3781] Linking default/source3/lib/netapi/examples/user/user_getinfo
[3737/3781] Linking default/source3/lib/netapi/examples/user/user_setinfo
[3738/3781] Linking default/source3/lib/netapi/examples/user/user_modalsget
[3739/3781] Linking default/source3/lib/netapi/examples/user/user_modalsset
[3740/3781] Linking default/source3/lib/netapi/examples/user/user_getgroups
[3741/3781] Linking default/source3/lib/netapi/examples/user/user_setgroups
[3742/3781] Linking default/source3/lib/netapi/examples/user/user_getlocalgroups
[3743/3781] Linking default/source3/lib/netapi/examples/group/group_add
[3744/3781] Linking default/source3/lib/netapi/examples/group/group_del
[3745/3781] Linking default/source3/lib/netapi/examples/group/group_enum
[3746/3781] Linking default/source3/lib/netapi/examples/group/group_setinfo
[3747/3781] Linking default/source3/lib/netapi/examples/group/group_getinfo
[3748/3781] Linking default/source3/lib/netapi/examples/group/group_adduser
[3749/3781] Linking default/source3/lib/netapi/examples/group/group_deluser
[3750/3781] Linking default/source3/lib/netapi/examples/group/group_getusers
[3751/3781] Linking default/source3/lib/netapi/examples/group/group_setusers
[3752/3781] Linking default/source3/lib/netapi/examples/localgroup/localgroup_add
[3753/3781] Linking default/source3/lib/netapi/examples/localgroup/localgroup_del
[3754/3781] Linking default/source3/lib/netapi/examples/localgroup/localgroup_getinfo
[3755/3781] Linking default/source3/lib/netapi/examples/localgroup/localgroup_setinfo
[3756/3781] Linking default/source3/lib/netapi/examples/localgroup/localgroup_enum
[3757/3781] Linking default/source3/lib/netapi/examples/localgroup/localgroup_addmembers
[3758/3781] Linking default/source3/lib/netapi/examples/localgroup/localgroup_delmembers
[3759/3781] Linking default/source3/lib/netapi/examples/localgroup/localgroup_setmembers
[3760/3781] Linking default/source3/lib/netapi/examples/localgroup/localgroup_getmembers
[3761/3781] Linking default/source3/lib/netapi/examples/server/remote_tod
[3762/3781] Linking default/source3/lib/netapi/examples/server/server_getinfo
[3763/3781] Linking default/source3/lib/netapi/examples/share/share_add
[3764/3781] Linking default/source3/lib/netapi/examples/share/share_del
[3765/3781] Linking default/source3/lib/netapi/examples/share/share_enum
[3766/3781] Linking default/source3/lib/netapi/examples/share/share_getinfo
[3767/3781] Linking default/source3/lib/netapi/examples/share/share_setinfo
[3768/3781] Linking default/source3/lib/netapi/examples/file/file_close
[3769/3781] Linking default/source3/lib/netapi/examples/file/file_getinfo
[3770/3781] Linking default/source3/lib/netapi/examples/file/file_enum
[3771/3781] Linking default/source3/lib/netapi/examples/shutdown/shutdown_init
[3772/3781] Linking default/source3/lib/netapi/examples/shutdown/shutdown_abort
[3773/3781] Linking default/source3/lib/netapi/examples/netlogon/netlogon_control
[3774/3781] Linking default/source3/lib/netapi/examples/netlogon/netlogon_control2
[3775/3781] Linking default/source3/lib/netapi/examples/netlogon/nltest
[3776/3781] pidl.1p: pidl/pidl -> bin/default/pidl/pidl.1p
[3777/3781] Parse::Pidl::Dump.3pm: pidl/lib/Parse/Pidl/Dump.pm -> bin/default/pidl/Parse::Pidl::Dump.3pm
[3778/3781] Parse::Pidl::Wireshark::Conformance.3pm: pidl/lib/Parse/Pidl/Wireshark/Conformance.pm -> bin/default/pidl/Parse::Pidl::Wireshark::Conformance.3pm
[3779/3781] Parse::Pidl::Util.3pm: pidl/lib/Parse/Pidl/Util.pm -> bin/default/pidl/Parse::Pidl::Util.3pm
[3780/3781] Parse::Pidl::NDR.3pm: pidl/lib/Parse/Pidl/NDR.pm -> bin/default/pidl/Parse::Pidl::NDR.3pm
[3781/3781] Parse::Pidl::Wireshark::NDR.3pm: pidl/lib/Parse/Pidl/Wireshark/NDR.pm -> bin/default/pidl/Parse::Pidl::Wireshark::NDR.3pm
Waf: Leaving directory `/root/samba-4.0.9/bin'
'build' finished successfully (24m1.730s)
```

---

### Post by TheHammer101 on 2013-10-04
# make install
```
WAF_MAKE=1 python ./buildtools/bin/waf install
Waf: Entering directory `/root/samba-4.0.9/bin'
* creating /usr/local/samba/etc
* creating /usr/local/samba/private
* creating /usr/local/samba/var
* creating /usr/local/samba/private
* creating /usr/local/samba/var/lib
* creating /usr/local/samba/var/locks
* creating /usr/local/samba/var/cache
* creating /usr/local/samba/var/lock
* creating /usr/local/samba/var/run
* creating /usr/local/samba/var/run
        Selected embedded Heimdal build
Checking project rules ...
Project rules pass
[ 126/4084] Linking default/lib/replace/libreplace.inst.so
* installing bin/default/lib/replace/libreplace.inst.so as /usr/local/samba/lib/private/libreplace.so
[ 127/4084] Generating VERSION
[ 161/4084] Generating smbd/build_options.c
* installing bin/default/lib/param/samba-hostconfig.pc as /usr/local/samba/lib/pkgconfig/samba-hostconfig.pc
* installing bin/default/source4/librpc/dcerpc_samr.pc as /usr/local/samba/lib/pkgconfig/dcerpc_samr.pc
* installing bin/default/source4/librpc/dcerpc_atsvc.pc as /usr/local/samba/lib/pkgconfig/dcerpc_atsvc.pc
* installing bin/default/source4/librpc/dcerpc.pc as /usr/local/samba/lib/pkgconfig/dcerpc.pc
* installing bin/default/source4/dsdb/samdb.pc as /usr/local/samba/lib/pkgconfig/samdb.pc
* installing bin/default/auth/gensec/gensec.pc as /usr/local/samba/lib/pkgconfig/gensec.pc
* installing bin/default/auth/credentials/samba-credentials.pc as /usr/local/samba/lib/pkgconfig/samba-credentials.pc
* installing bin/default/nsswitch/libwbclient/wbclient.pc as /usr/local/samba/lib/pkgconfig/wbclient.pc
* installing bin/default/source4/lib/registry/registry.pc as /usr/local/samba/lib/pkgconfig/registry.pc
* installing bin/default/lib/util/samba-util.pc as /usr/local/samba/lib/pkgconfig/samba-util.pc
* installing bin/default/lib/torture/torture.pc as /usr/local/samba/lib/pkgconfig/torture.pc
* installing bin/default/source4/rpc_server/dcerpc_server.pc as /usr/local/samba/lib/pkgconfig/dcerpc_server.pc
* installing bin/default/librpc/ndr_krb5pac.pc as /usr/local/samba/lib/pkgconfig/ndr_krb5pac.pc
* installing bin/default/librpc/ndr_standard.pc as /usr/local/samba/lib/pkgconfig/ndr_standard.pc
* installing bin/default/librpc/ndr_nbt.pc as /usr/local/samba/lib/pkgconfig/ndr_nbt.pc
* installing bin/default/librpc/ndr.pc as /usr/local/samba/lib/pkgconfig/ndr.pc
* installing bin/default/source4/libcli/raw/smbclient-raw.pc as /usr/local/samba/lib/pkgconfig/smbclient-raw.pc
* installing bin/default/source4/lib/policy/samba-policy.pc as /usr/local/samba/lib/pkgconfig/samba-policy.pc
* installing bin/default/source4/scripting/bin/samba_dnsupdate.inst as /usr/local/samba/sbin/samba_dnsupdate
* installing bin/default/source4/scripting/bin/samba_spnupdate.inst as /usr/local/samba/sbin/samba_spnupdate
* installing bin/default/source4/scripting/bin/samba_upgradedns.inst as /usr/local/samba/sbin/samba_upgradedns
* installing bin/default/source4/scripting/bin/samba_kcc.inst as /usr/local/samba/sbin/samba_kcc
* installing bin/default/source4/scripting/bin/samba-tool.inst as /usr/local/samba/bin/samba-tool
* installing bin/default/lib/empty_file as /usr/local/samba/lib/python2.7/site-packages/samba/external/__init__.py
* installing bin/default/source3/libnet/netapi.pc as /usr/local/samba/lib/pkgconfig/netapi.pc
* installing bin/default/source3/libsmb/smbsharemodes.pc as /usr/local/samba/lib/pkgconfig/smbsharemodes.pc
* installing bin/default/source3/libsmb/smbclient.pc as /usr/local/samba/lib/pkgconfig/smbclient.pc
[ 224/4084] Linking default/source4/heimdal_build/asn1_compile.inst
[ 225/4084] Linking default/source4/heimdal_build/compile_et.inst
* installing bin/default/include/public/pytalloc.h as /usr/local/samba/include/pytalloc.h
* installing bin/default/include/public/param.h as /usr/local/samba/include/param.h
* installing bin/default/include/public/samba/version.h as /usr/local/samba/include/samba/version.h
* installing bin/default/include/public/charset.h as /usr/local/samba/include/charset.h
* installing bin/default/include/public/share.h as /usr/local/samba/include/share.h
* installing bin/default/include/public/gen_ndr/ndr_samr_c.h as /usr/local/samba/include/gen_ndr/ndr_samr_c.h
* installing bin/default/include/public/gen_ndr/ndr_atsvc_c.h as /usr/local/samba/include/gen_ndr/ndr_atsvc_c.h
* installing bin/default/include/public/dcerpc.h as /usr/local/samba/include/dcerpc.h
* installing bin/default/include/public/gen_ndr/mgmt.h as /usr/local/samba/include/gen_ndr/mgmt.h
* installing bin/default/include/public/gen_ndr/ndr_mgmt.h as /usr/local/samba/include/gen_ndr/ndr_mgmt.h
* installing bin/default/include/public/gen_ndr/ndr_mgmt_c.h as /usr/local/samba/include/gen_ndr/ndr_mgmt_c.h
* installing bin/default/include/public/gen_ndr/epmapper.h as /usr/local/samba/include/gen_ndr/epmapper.h
* installing bin/default/include/public/gen_ndr/ndr_epmapper.h as /usr/local/samba/include/gen_ndr/ndr_epmapper.h
* installing bin/default/include/public/gen_ndr/ndr_epmapper_c.h as /usr/local/samba/include/gen_ndr/ndr_epmapper_c.h
* installing bin/default/include/public/samba/session.h as /usr/local/samba/include/samba/session.h
* installing bin/default/include/public/gensec.h as /usr/local/samba/include/gensec.h
* installing bin/default/include/public/credentials.h as /usr/local/samba/include/credentials.h
* installing bin/default/include/public/wbclient.h as /usr/local/samba/include/wbclient.h
* installing bin/default/include/public/ldb_wrap.h as /usr/local/samba/include/ldb_wrap.h
* installing bin/default/include/public/registry.h as /usr/local/samba/include/registry.h
* installing bin/default/include/public/util/debug.h as /usr/local/samba/include/util/debug.h
* installing bin/default/include/public/util/attr.h as /usr/local/samba/include/util/attr.h
* installing bin/default/include/public/util/byteorder.h as /usr/local/samba/include/util/byteorder.h
* installing bin/default/include/public/util/data_blob.h as /usr/local/samba/include/util/data_blob.h
* installing bin/default/include/public/util/memory.h as /usr/local/samba/include/util/memory.h
* installing bin/default/include/public/util/safe_string.h as /usr/local/samba/include/util/safe_string.h
* installing bin/default/include/public/util/time.h as /usr/local/samba/include/util/time.h
* installing bin/default/include/public/util/talloc_stack.h as /usr/local/samba/include/util/talloc_stack.h
* installing bin/default/include/public/util/xfile.h as /usr/local/samba/include/util/xfile.h
* installing bin/default/include/public/dlinklist.h as /usr/local/samba/include/./dlinklist.h
* installing bin/default/include/public/samba_util.h as /usr/local/samba/include/./samba_util.h
* installing bin/default/include/public/util/string_wrappers.h as /usr/local/samba/include/util/string_wrappers.h
* installing bin/default/include/public/util/tevent_ntstatus.h as /usr/local/samba/include/util/tevent_ntstatus.h
* installing bin/default/include/public/util/tevent_unix.h as /usr/local/samba/include/util/tevent_unix.h
* installing bin/default/include/public/util/tevent_werror.h as /usr/local/samba/include/util/tevent_werror.h
* installing bin/default/include/public/util_ldb.h as /usr/local/samba/include/util_ldb.h
* installing bin/default/include/public/tdr.h as /usr/local/samba/include/tdr.h
* installing bin/default/include/public/tsocket.h as /usr/local/samba/include/tsocket.h
* installing bin/default/include/public/tsocket_internal.h as /usr/local/samba/include/tsocket_internal.h
* installing bin/default/include/public/torture.h as /usr/local/samba/include/torture.h
* installing bin/default/include/public/dcerpc_server.h as /usr/local/samba/include/dcerpc_server.h
* installing bin/default/include/public/gen_ndr/auth.h as /usr/local/samba/include/gen_ndr/auth.h
* installing bin/default/include/public/gen_ndr/server_id.h as /usr/local/samba/include/gen_ndr/server_id.h
* installing bin/default/include/public/gen_ndr/security.h as /usr/local/samba/include/gen_ndr/security.h
* installing bin/default/include/public/gen_ndr/ndr_dcerpc.h as /usr/local/samba/include/gen_ndr/ndr_dcerpc.h
* installing bin/default/include/public/gen_ndr/dcerpc.h as /usr/local/samba/include/gen_ndr/dcerpc.h
* installing bin/default/include/public/gen_ndr/ndr_drsuapi.h as /usr/local/samba/include/gen_ndr/ndr_drsuapi.h
* installing bin/default/include/public/gen_ndr/drsuapi.h as /usr/local/samba/include/gen_ndr/drsuapi.h
* installing bin/default/include/public/ndr/ndr_drsuapi.h as /usr/local/samba/include/ndr/ndr_drsuapi.h
* installing bin/default/include/public/gen_ndr/ndr_drsblobs.h as /usr/local/samba/include/gen_ndr/ndr_drsblobs.h
* installing bin/default/include/public/gen_ndr/drsblobs.h as /usr/local/samba/include/gen_ndr/drsblobs.h
* installing bin/default/include/public/ndr/ndr_drsblobs.h as /usr/local/samba/include/ndr/ndr_drsblobs.h
* installing bin/default/include/public/gen_ndr/krb5pac.h as /usr/local/samba/include/gen_ndr/krb5pac.h
* installing bin/default/include/public/gen_ndr/ndr_krb5pac.h as /usr/local/samba/include/gen_ndr/ndr_krb5pac.h
* installing bin/default/include/public/gen_ndr/samr.h as /usr/local/samba/include/gen_ndr/samr.h
* installing bin/default/include/public/gen_ndr/ndr_samr.h as /usr/local/samba/include/gen_ndr/ndr_samr.h
* installing bin/default/include/public/gen_ndr/lsa.h as /usr/local/samba/include/gen_ndr/lsa.h
* installing bin/default/include/public/gen_ndr/netlogon.h as /usr/local/samba/include/gen_ndr/netlogon.h
* installing bin/default/include/public/gen_ndr/atsvc.h as /usr/local/samba/include/gen_ndr/atsvc.h
* installing bin/default/include/public/gen_ndr/ndr_atsvc.h as /usr/local/samba/include/gen_ndr/ndr_atsvc.h
* installing bin/default/include/public/gen_ndr/ndr_svcctl.h as /usr/local/samba/include/gen_ndr/ndr_svcctl.h
* installing bin/default/include/public/gen_ndr/svcctl.h as /usr/local/samba/include/gen_ndr/svcctl.h
* installing bin/default/include/public/gen_ndr/nbt.h as /usr/local/samba/include/gen_ndr/nbt.h
* installing bin/default/include/public/gen_ndr/ndr_nbt.h as /usr/local/samba/include/gen_ndr/ndr_nbt.h
* installing bin/default/include/public/ndr/ndr_nbt.h as /usr/local/samba/include/ndr/ndr_nbt.h
* installing bin/default/include/public/gen_ndr/ndr_svcctl_c.h as /usr/local/samba/include/gen_ndr/ndr_svcctl_c.h
* installing bin/default/include/public/ndr/ndr_svcctl.h as /usr/local/samba/include/ndr/ndr_svcctl.h
* installing bin/default/include/public/gen_ndr/misc.h as /usr/local/samba/include/gen_ndr/misc.h
* installing bin/default/include/public/gen_ndr/ndr_misc.h as /usr/local/samba/include/gen_ndr/ndr_misc.h
* installing bin/default/include/public/ndr.h as /usr/local/samba/include/ndr.h
* installing bin/default/include/public/rpc_common.h as /usr/local/samba/include/rpc_common.h
* installing bin/default/include/public/ldap-util.h as /usr/local/samba/include/ldap-util.h
* installing bin/default/include/public/smb_composite.h as /usr/local/samba/include/smb_composite.h
* installing bin/default/include/public/smb_cli.h as /usr/local/samba/include/smb_cli.h
* installing bin/default/include/public/smb_request.h as /usr/local/samba/include/smb_request.h
* installing bin/default/include/public/smb_raw_signing.h as /usr/local/samba/include/smb_raw_signing.h
* installing bin/default/include/public/smb_cliraw.h as /usr/local/samba/include/smb_cliraw.h
* installing bin/default/include/public/smb_raw_interfaces.h as /usr/local/samba/include/smb_raw_interfaces.h
* installing bin/default/include/public/smb_raw.h as /usr/local/samba/include/smb_raw.h
* installing bin/default/include/public/smb_raw_trans2.h as /usr/local/samba/include/smb_raw_trans2.h
* installing bin/default/include/public/smb2.h as /usr/local/samba/include/smb2.h
* installing bin/default/include/public/read_smb.h as /usr/local/samba/include/read_smb.h
* installing bin/default/include/public/smb_common.h as /usr/local/samba/include/smb_common.h
* installing bin/default/include/public/smb2_constants.h as /usr/local/samba/include/smb2_constants.h
* installing bin/default/include/public/smb_constants.h as /usr/local/samba/include/smb_constants.h
* installing bin/default/include/public/smb_signing.h as /usr/local/samba/include/smb_signing.h
* installing bin/default/include/public/smb_seal.h as /usr/local/samba/include/smb_seal.h
* installing bin/default/include/public/smb2_create_blob.h as /usr/local/samba/include/smb2_create_blob.h
* installing bin/default/include/public/smb2_signing.h as /usr/local/samba/include/smb2_signing.h
* installing bin/default/include/public/smb_util.h as /usr/local/samba/include/smb_util.h
* installing bin/default/include/public/smb_unix_ext.h as /usr/local/samba/include/smb_unix_ext.h
* installing bin/default/include/public/core/error.h as /usr/local/samba/include/core/error.h
* installing bin/default/include/public/core/ntstatus.h as /usr/local/samba/include/core/ntstatus.h
* installing bin/default/include/public/core/doserr.h as /usr/local/samba/include/core/doserr.h
* installing bin/default/include/public/core/werror.h as /usr/local/samba/include/core/werror.h
* installing bin/default/include/public/ldap_message.h as /usr/local/samba/include/ldap_message.h
* installing bin/default/include/public/ldap_errors.h as /usr/local/samba/include/ldap_errors.h
* installing bin/default/include/public/ldap_ndr.h as /usr/local/samba/include/ldap_ndr.h
* installing bin/default/include/public/domain_credentials.h as /usr/local/samba/include/domain_credentials.h
* installing bin/default/include/public/policy.h as /usr/local/samba/include/policy.h
* installing bin/default/include/public/roles.h as /usr/local/samba/include/roles.h
* installing bin/default/include/public/netapi.h as /usr/local/samba/include/netapi.h
* installing bin/default/include/public/smb_share_modes.h as /usr/local/samba/include/smb_share_modes.h
* installing bin/default/include/public/passdb.h as /usr/local/samba/include/passdb.h
* installing bin/default/include/public/machine_sid.h as /usr/local/samba/include/machine_sid.h
* installing bin/default/include/public/lookup_sid.h as /usr/local/samba/include/lookup_sid.h
* installing bin/default/include/public/smbldap.h as /usr/local/samba/include/smbldap.h
* installing bin/default/include/public/smb_ldap.h as /usr/local/samba/include/smb_ldap.h
* installing bin/default/include/public/smbconf.h as /usr/local/samba/include/smbconf.h
* installing bin/default/include/public/libsmbclient.h as /usr/local/samba/include/libsmbclient.h
[ 722/4084] Compiling lib/ldb/common/ldb.c
../lib/ldb/common/ldb.c: In function âldb_initâ:
../lib/ldb/common/ldb.c:116:3: warning: âtevent_loop_allow_nestingâ is deprecated (declared at default/include/public/tevent.h:1609) [-Wdeprecated-declarations]
[ 737/4084] Compiling dynconfig/dynconfig.c
[2083/4084] Compiling source4/heimdal/lib/krb5/expand_path.c
[2084/4084] Compiling source4/heimdal/lib/krb5/plugin.c
[2085/4084] Compiling source4/heimdal/lib/krb5/context.c
* installing codepages/lowcase.dat as /usr/local/samba/share/codepages/lowcase.dat
* installing codepages/upcase.dat as /usr/local/samba/share/codepages/upcase.dat
* installing codepages/valid.dat as /usr/local/samba/share/codepages/valid.dat
* installing source4/setup/ad-schema/MS-AD_Schema_2K8_Attributes.txt as /usr/local/samba/share/setup/ad-schema/MS-AD_Schema_2K8_Attributes.txt
* installing source4/setup/ad-schema/MS-AD_Schema_2K8_Classes.txt as /usr/local/samba/share/setup/ad-schema/MS-AD_Schema_2K8_Classes.txt
* installing source4/setup/ad-schema/MS-AD_Schema_2K8_R2_Attributes.txt as /usr/local/samba/share/setup/ad-schema/MS-AD_Schema_2K8_R2_Attributes.txt
* installing source4/setup/ad-schema/MS-AD_Schema_2K8_R2_Classes.txt as /usr/local/samba/share/setup/ad-schema/MS-AD_Schema_2K8_R2_Classes.txt
* installing source4/setup/ad-schema/licence.txt as /usr/local/samba/share/setup/ad-schema/licence.txt
* installing source4/setup/display-specifiers/DisplaySpecifiers-Win2k0.txt as /usr/local/samba/share/setup/display-specifiers/DisplaySpecifiers-Win2k0.txt
* installing source4/setup/display-specifiers/DisplaySpecifiers-Win2k3.txt as /usr/local/samba/share/setup/display-specifiers/DisplaySpecifiers-Win2k3.txt
* installing source4/setup/display-specifiers/DisplaySpecifiers-Win2k3R2.txt as /usr/local/samba/share/setup/display-specifiers/DisplaySpecifiers-Win2k3R2.txt
* installing source4/setup/display-specifiers/DisplaySpecifiers-Win2k8.txt as /usr/local/samba/share/setup/display-specifiers/DisplaySpecifiers-Win2k8.txt
* installing source4/setup/display-specifiers/DisplaySpecifiers-Win2k8R2.txt as /usr/local/samba/share/setup/display-specifiers/DisplaySpecifiers-Win2k8R2.txt
* installing source4/setup/dns_update_list as /usr/local/samba/share/setup/dns_update_list
* installing source4/setup/spn_update_list as /usr/local/samba/share/setup/spn_update_list
* installing source4/setup/schema-map-fedora-ds-1.0 as /usr/local/samba/share/setup/schema-map-fedora-ds-1.0
* installing source4/setup/schema-map-openldap-2.3 as /usr/local/samba/share/setup/schema-map-openldap-2.3
* installing source4/setup/DB_CONFIG as /usr/local/samba/share/setup/DB_CONFIG
* installing source4/setup/fedorads.inf as /usr/local/samba/share/setup/fedorads.inf
* installing source4/setup/aggregate_schema.ldif as /usr/local/samba/share/setup/aggregate_schema.ldif
* installing source4/setup/cn=replicator.ldif as /usr/local/samba/share/setup/cn=replicator.ldif
* installing source4/setup/cn=samba-admin.ldif as /usr/local/samba/share/setup/cn=samba-admin.ldif
* installing source4/setup/cn=samba.ldif as /usr/local/samba/share/setup/cn=samba.ldif
* installing source4/setup/fedora-ds-init.ldif as /usr/local/samba/share/setup/fedora-ds-init.ldif
* installing source4/setup/fedorads-dna.ldif as /usr/local/samba/share/setup/fedorads-dna.ldif
* installing source4/setup/fedorads-index.ldif as /usr/local/samba/share/setup/fedorads-index.ldif
* installing source4/setup/fedorads-linked-attributes.ldif as /usr/local/samba/share/setup/fedorads-linked-attributes.ldif
* installing source4/setup/fedorads-pam.ldif as /usr/local/samba/share/setup/fedorads-pam.ldif
* installing source4/setup/fedorads-partitions.ldif as /usr/local/samba/share/setup/fedorads-partitions.ldif
* installing source4/setup/fedorads-refint-add.ldif as /usr/local/samba/share/setup/fedorads-refint-add.ldif
* installing source4/setup/fedorads-refint-delete.ldif as /usr/local/samba/share/setup/fedorads-refint-delete.ldif
* installing source4/setup/fedorads-samba.ldif as /usr/local/samba/share/setup/fedorads-samba.ldif
* installing source4/setup/fedorads-sasl.ldif as /usr/local/samba/share/setup/fedorads-sasl.ldif
* installing source4/setup/idmap_init.ldif as /usr/local/samba/share/setup/idmap_init.ldif
* installing source4/setup/olc_seed.ldif as /usr/local/samba/share/setup/olc_seed.ldif
* installing source4/setup/provision.ldif as /usr/local/samba/share/setup/provision.ldif
* installing source4/setup/provision_basedn.ldif as /usr/local/samba/share/setup/provision_basedn.ldif
* installing source4/setup/provision_basedn_modify.ldif as /usr/local/samba/share/setup/provision_basedn_modify.ldif
* installing source4/setup/provision_basedn_options.ldif as /usr/local/samba/share/setup/provision_basedn_options.ldif
* installing source4/setup/provision_basedn_references.ldif as /usr/local/samba/share/setup/provision_basedn_references.ldif
* installing source4/setup/provision_computers_add.ldif as /usr/local/samba/share/setup/provision_computers_add.ldif
* installing source4/setup/provision_computers_modify.ldif as /usr/local/samba/share/setup/provision_computers_modify.ldif
* installing source4/setup/provision_configuration.ldif as /usr/local/samba/share/setup/provision_configuration.ldif
* installing source4/setup/provision_configuration_basedn.ldif as /usr/local/samba/share/setup/provision_configuration_basedn.ldif
* installing source4/setup/provision_configuration_modify.ldif as /usr/local/samba/share/setup/provision_configuration_modify.ldif
* installing source4/setup/provision_configuration_references.ldif as /usr/local/samba/share/setup/provision_configuration_references.ldif
* installing source4/setup/provision_dns_accounts_add.ldif as /usr/local/samba/share/setup/provision_dns_accounts_add.ldif
* installing source4/setup/provision_dns_add_samba.ldif as /usr/local/samba/share/setup/provision_dns_add_samba.ldif
* installing source4/setup/provision_dnszones_add.ldif as /usr/local/samba/share/setup/provision_dnszones_add.ldif
* installing source4/setup/provision_dnszones_modify.ldif as /usr/local/samba/share/setup/provision_dnszones_modify.ldif
* installing source4/setup/provision_dnszones_partitions.ldif as /usr/local/samba/share/setup/provision_dnszones_partitions.ldif
* installing source4/setup/provision_group_policy.ldif as /usr/local/samba/share/setup/provision_group_policy.ldif
* installing source4/setup/provision_init.ldif as /usr/local/samba/share/setup/provision_init.ldif
* installing source4/setup/provision_partitions.ldif as /usr/local/samba/share/setup/provision_partitions.ldif
* installing source4/setup/provision_privilege.ldif as /usr/local/samba/share/setup/provision_privilege.ldif
* installing source4/setup/provision_rootdse_add.ldif as /usr/local/samba/share/setup/provision_rootdse_add.ldif
* installing source4/setup/provision_rootdse_modify.ldif as /usr/local/samba/share/setup/provision_rootdse_modify.ldif
* installing source4/setup/provision_schema_basedn.ldif as /usr/local/samba/share/setup/provision_schema_basedn.ldif
* installing source4/setup/provision_schema_basedn_modify.ldif as /usr/local/samba/share/setup/provision_schema_basedn_modify.ldif
* installing source4/setup/provision_self_join.ldif as /usr/local/samba/share/setup/provision_self_join.ldif
* installing source4/setup/provision_self_join_config.ldif as /usr/local/samba/share/setup/provision_self_join_config.ldif
* installing source4/setup/provision_self_join_modify.ldif as /usr/local/samba/share/setup/provision_self_join_modify.ldif
* installing source4/setup/provision_self_join_modify_config.ldif as /usr/local/samba/share/setup/provision_self_join_modify_config.ldif
* installing source4/setup/provision_users.ldif as /usr/local/samba/share/setup/provision_users.ldif
* installing source4/setup/provision_users_add.ldif as /usr/local/samba/share/setup/provision_users_add.ldif
* installing source4/setup/provision_users_modify.ldif as /usr/local/samba/share/setup/provision_users_modify.ldif
* installing source4/setup/provision_well_known_sec_princ.ldif as /usr/local/samba/share/setup/provision_well_known_sec_princ.ldif
* installing source4/setup/schema_samba4.ldif as /usr/local/samba/share/setup/schema_samba4.ldif
* installing source4/setup/secrets.ldif as /usr/local/samba/share/setup/secrets.ldif
* installing source4/setup/secrets_dns.ldif as /usr/local/samba/share/setup/secrets_dns.ldif
* installing source4/setup/secrets_init.ldif as /usr/local/samba/share/setup/secrets_init.ldif
* installing source4/setup/secrets_sasl_ldap.ldif as /usr/local/samba/share/setup/secrets_sasl_ldap.ldif
* installing source4/setup/secrets_simple_ldap.ldif as /usr/local/samba/share/setup/secrets_simple_ldap.ldif
* installing source4/setup/share.ldif as /usr/local/samba/share/setup/share.ldif
* installing source4/setup/ypServ30.ldif as /usr/local/samba/share/setup/ypServ30.ldif
* installing source4/setup/provision.reg as /usr/local/samba/share/setup/provision.reg
* installing source4/setup/provision.zone as /usr/local/samba/share/setup/provision.zone
* installing source4/setup/krb5.conf as /usr/local/samba/share/setup/krb5.conf
* installing source4/setup/memberof.conf as /usr/local/samba/share/setup/memberof.conf
* installing source4/setup/mmr_serverids.conf as /usr/local/samba/share/setup/mmr_serverids.conf
* installing source4/setup/mmr_syncrepl.conf as /usr/local/samba/share/setup/mmr_syncrepl.conf
* installing source4/setup/modules.conf as /usr/local/samba/share/setup/modules.conf
* installing source4/setup/named.conf as /usr/local/samba/share/setup/named.conf
* installing source4/setup/olc_mmr.conf as /usr/local/samba/share/setup/olc_mmr.conf
* installing source4/setup/olc_serverid.conf as /usr/local/samba/share/setup/olc_serverid.conf
* installing source4/setup/olc_syncrepl.conf as /usr/local/samba/share/setup/olc_syncrepl.conf
* installing source4/setup/olc_syncrepl_seed.conf as /usr/local/samba/share/setup/olc_syncrepl_seed.conf
* installing source4/setup/refint.conf as /usr/local/samba/share/setup/refint.conf
* installing source4/setup/slapd.conf as /usr/local/samba/share/setup/slapd.conf
* installing source4/setup/named.txt as /usr/local/samba/share/setup/named.txt
* installing source4/setup/prefixMap.txt as /usr/local/samba/share/setup/prefixMap.txt
* installing source4/setup/named.conf.update as /usr/local/samba/share/setup/named.conf.update
* installing source4/setup/named.conf.dlz as /usr/local/samba/share/setup/named.conf.dlz
[3320/4084] Linking default/lib/ldb/libldb.so
[3321/4084] Linking default/lib/ldb/libldb-paged-results.so
[3322/4084] Linking default/lib/ldb/libldb-asq.so
[3323/4084] Linking default/lib/ldb/libldb-server-sort.so
[3324/4084] Linking default/lib/ldb/libldb-paged-searches.so
[3325/4084] Linking default/lib/ldb/libldb-rdn-name.so
[3326/4084] Linking default/lib/ldb/libldb-sample.so
[3327/4084] Linking default/lib/ldb/libldb-skel.so
[3328/4084] Linking default/lib/ldb/libldb-tdb.so
[3329/4084] Linking default/lib/ldb/libldb-cmdline.so
[3337/4084] Linking default/lib/util/libsamba-util.inst.so
[3338/4084] Linking default/lib/util/libutil_setid.inst.so
[3339/4084] Linking default/lib/talloc/libtalloc.inst.so
[3340/4084] Linking default/lib/talloc/libpytalloc-util.inst.so
[3341/4084] Linking default/lib/talloc/pytalloc.inst.so
[3342/4084] Linking default/lib/tevent/libtevent.inst.so
[3343/4084] Linking default/lib/tevent/pytevent.inst.so
[3344/4084] Linking default/source4/heimdal_build/libheimbase-samba4.inst.so
[3345/4084] Linking default/source4/heimdal_build/libroken-samba4.inst.so
[3346/4084] Linking default/source4/heimdal_build/libasn1-samba4.inst.so
[3347/4084] Linking default/source4/heimdal_build/libhx509-samba4.inst.so
[3348/4084] Linking default/source4/heimdal_build/libhcrypto-samba4.inst.so
[3349/4084] Linking default/source4/heimdal_build/libwind-samba4.inst.so
[3350/4084] Linking default/lib/ccan/libccan.inst.so
[3351/4084] Linking default/lib/tdb/libtdb.inst.so
[3352/4084] Linking default/lib/tdb/pytdb.inst.so
[3353/4084] Linking default/lib/tdb_compat/libtdb_compat.inst.so
[3354/4084] Linking default/lib/ldb/libpyldb-util.inst.so
[3355/4084] Linking default/lib/ldb/libldb.inst.so
[3356/4084] Linking default/lib/ldb/libldb-paged-results.inst.so
[3357/4084] Linking default/lib/ldb/libldb-asq.inst.so
[3358/4084] Linking default/lib/ldb/libldb-server-sort.inst.so
[3359/4084] Linking default/lib/ldb/libldb-paged-searches.inst.so
[3360/4084] Linking default/lib/ldb/libldb-rdn-name.inst.so
[3361/4084] Linking default/lib/ldb/libldb-sample.inst.so
[3362/4084] Linking default/lib/ldb/libldb-skel.inst.so
[3363/4084] Linking default/lib/ldb/libldb-tdb.inst.so
[3364/4084] Linking default/lib/ldb/libldb-cmdline.inst.so
[3365/4084] Linking default/source3/libsmbd_shim.inst.so
[3366/4084] Linking default/nsswitch/libwbclient/libwbclient.inst.so
[3367/4084] Linking default/nsswitch/libwinbind-client.inst.so
[3368/4084] Linking default/nsswitch/libnss-winbind.inst.so
[3369/4084] Linking default/lib/iniparser/src/libiniparser.inst.so
[3370/4084] Linking default/lib/subunit/c/libsubunit.inst.so
[3371/4084] Linking default/source3/libsmbsharemodes.inst.so
[3374/4084] Linking default/source4/heimdal_build/libkrb5-samba4.so
[3375/4084] Linking default/source4/heimdal_build/libgssapi-samba4.so
[3376/4084] Linking default/lib/util/libsamba-util.so
[3377/4084] Linking default/libcli/util/liberrors.so
[3378/4084] Linking default/librpc/libndr.so
[3379/4084] Linking default/lib/ldb/libpyldb-util.so
[3380/4084] Linking default/lib/param/libserver-role.so
[3381/4084] Linking default/lib/param/libsamba-hostconfig.so
[3382/4084] Linking default/lib/tdb_wrap/libtdb-wrap.so
[3383/4084] Linking default/libcli/security/libsamba-security.so
[3384/4084] Linking default/lib/util/libasn1util.so
[3385/4084] Linking default/source4/lib/events/libevents.so
[3386/4084] Linking default/lib/util/libutil_tdb.so
[3387/4084] Linking default/lib/krb5_wrap/libkrb5samba.so
[3388/4084] Linking default/auth/libauth_sam_reply.so
[3389/4084] Linking default/lib/dbwrap/libdbwrap.so
[3390/4084] Linking default/source4/param/pyparam.so
[3392/4084] Linking default/source4/heimdal_build/libhdb-samba4.so
[3393/4084] Linking default/nsswitch/libwinbind-krb5-locator.so
[3394/4084] Linking default/lib/torture/libtorture.so
[3395/4084] Linking default/source4/ntvfs/posix/libposix_eadb.so
[3396/4084] Linking default/libcli/security/pysecurity.so
[3397/4084] Linking default/source4/heimdal_build/libheimntlm-samba4.so
[3398/4084] Linking default/lib/socket/libinterfaces.inst.so
[3399/4084] Linking default/lib/addns/libaddns.inst.so
[3400/4084] Linking default/source4/heimdal_build/libgssapi-samba4.inst.so
[3401/4084] Linking default/source4/heimdal_build/libkrb5-samba4.inst.so
[3402/4084] Linking default/lib/ldb/pyldb.inst.so
[3403/4084] Linking default/lib/param/libserver-role.inst.so
[3404/4084] Linking default/lib/param/libsamba-hostconfig.inst.so
[3405/4084] Linking default/lib/tdb_wrap/libtdb-wrap.inst.so
[3406/4084] Linking default/librpc/libndr-nbt.inst.so
[3407/4084] Linking default/libcli/security/libsamba-security.inst.so
[3408/4084] Linking default/source4/lib/events/libevents.inst.so
[3409/4084] Linking default/lib/util/libutil_tdb.inst.so
[3410/4084] Linking default/auth/libauth_sam_reply.inst.so
[3411/4084] Linking default/lib/dbwrap/libdbwrap.inst.so
[3412/4084] Linking default/lib/util/libsamba-modules.inst.so
[3413/4084] Linking default/source4/param/pyparam.inst.so
[3414/4084] Linking default/source4/lib/samba3/libsmbpasswdparser.inst.so
[3415/4084] Linking default/source4/heimdal_build/libhdb-samba4.inst.so
[3416/4084] Linking default/lib/torture/libtorture.inst.so
[3417/4084] Linking default/source4/ntvfs/posix/libposix_eadb.inst.so
[3418/4084] Linking default/libcli/security/pysecurity.inst.so
[3419/4084] Linking default/source4/heimdal_build/libkdc-samba4.inst.so
[3420/4084] Linking default/source4/heimdal_build/libheimntlm-samba4.inst.so
[3421/4084] Linking default/librpc/libndr-nbt.so
[3422/4084] Linking default/librpc/libndr-standard.so
[3423/4084] Linking default/librpc/libndr-krb5pac.so
[3424/4084] Linking default/lib/addns/libaddns.so
[3425/4084] Linking default/librpc/libndr-samba.so
[3426/4084] Linking default/lib/util/libtevent-util.so
[3427/4084] Linking default/libds/common/libflag_mapping.so
[3428/4084] Linking default/libcli/ldap/libcli-ldap-common.so
[3429/4084] Linking default/source4/lib/samba3/libsmbpasswdparser.so
[3431/4084] Linking default/source4/heimdal_build/libkdc-samba4.so
[3432/4084] Linking default/libcli/util/liberrors.inst.so
[3433/4084] Linking default/librpc/libndr.inst.so
[3434/4084] Linking default/source4/librpc/libndr-samba4.inst.so
[3435/4084] Linking default/lib/util/libtevent-util.inst.so
[3436/4084] Linking default/lib/libsamba-sockets.inst.so
[3437/4084] Linking default/libcli/ldap/libcli-ldap-common.inst.so
[3438/4084] Linking default/lib/krb5_wrap/libkrb5samba.inst.so
[3439/4084] Linking default/libcli/smb/libsmb_transport.inst.so
[3440/4084] Linking default/source4/cluster/libcluster.inst.so
[3441/4084] Linking default/libcli/registry/libutil_reg.inst.so
[3442/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-ranged-results.inst.so
[3443/4084] Linking default/nsswitch/libwinbind-krb5-locator.inst.so
[3444/4084] Linking default/source4/lib/com/pycom.inst.so
[3445/4084] Linking default/nsswitch/libpamwinbind.inst.so
[3446/4084] Linking default/source3/libsamba3-util.inst.so
[3447/4084] Linking default/libcli/auth/libcliauth.inst.so
[3448/4084] Linking default/libds/common/libflag_mapping.inst.so
[3449/4084] Linking default/lib/util/libasn1util.inst.so
[3450/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-ranged-results.so
[3451/4084] Linking default/source3/libsamba3-util.so
[3452/4084] Linking default/libcli/registry/libutil_reg.so
[3453/4084] Linking default/source3/libsmbregistry.so
[3454/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samba3sam.so
[3455/4084] Linking default/source4/cluster/libcluster.so
[3456/4084] Linking default/lib/util/libsamba-modules.so
[3457/4084] Linking default/libcli/smb/libsmb_transport.so
[3458/4084] Linking default/lib/ldb/pyldb.so
[3459/4084] Linking default/lib/socket/libinterfaces.so
[3460/4084] Linking default/lib/libsamba-sockets.so
[3461/4084] Linking default/libcli/auth/libcliauth.so
[3462/4084] Linking default/source3/libCHARSET3.so
[3463/4084] Linking default/libcli/named_pipe_auth/libnpa_tstream.so
[3464/4084] Linking default/source4/lib/com/pycom.so
[3465/4084] Linking default/librpc/libndr-krb5pac.inst.so
[3466/4084] Linking default/libcli/nbt/libcli-nbt.inst.so
[3467/4084] Linking default/source4/lib/socket/libnetif.inst.so
[3468/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samba3sam.inst.so
[3469/4084] Linking default/source4/smbd/libprocess_model.inst.so
[3470/4084] Linking default/source3/libxattr_tdb.inst.so
[3471/4084] Linking default/source4/dsdb/libsamdb-common.so
[3472/4084] Linking default/source4/smbd/libprocess_model.so
[3473/4084] Linking default/source3/libCHARSET3.inst.so
[3474/4084] Linking default/librpc/libdcerpc-binding.inst.so
[3475/4084] Linking default/source4/dsdb/libsamdb-common.inst.so
[3476/4084] Linking default/source3/libxattr_tdb.so
[3477/4084] Linking default/source4/lib/socket/libnetif.so
[3478/4084] Linking default/source4/auth/kerberos/libauthkrb5.so
[3479/4084] Linking default/lib/ldb-samba/libldbsamba.so
[3480/4084] Linking default/librpc/libndr-standard.inst.so
[3481/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-simple-ldap-map.inst.so
[3482/4084] Linking default/source3/libsmbregistry.inst.so
[3483/4084] Linking default/source4/smbd/libprocess-model-onefork.inst.so
[3484/4084] Linking default/libcli/named_pipe_auth/libnpa_tstream.inst.so
[3485/4084] Linking default/librpc/libndr-samba.inst.so
[3486/4084] Linking default/auth/credentials/libsamba-credentials.so
[3487/4084] Linking default/source4/librpc/libndr-samba4.so
[3488/4084] Linking default/librpc/libdcerpc-binding.so
[3489/4084] Linking default/source4/nbt_server/libldb-wins-ldb.so
[3490/4084] Linking default/source4/auth/kerberos/libauthkrb5.inst.so
[3491/4084] Linking default/source3/libsmbd_conn.inst.so
[3492/4084] Linking default/lib/ldb-samba/libldbsamba.inst.so
[3493/4084] Linking default/source3/libsmbd_conn.so
[3494/4084] Linking default/libcli/nbt/libcli-nbt.so
[3495/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-simple-ldap-map.so
[3496/4084] Linking default/source4/smbd/libprocess-model-standard.so
[3497/4084] Linking default/libcli/nbt/python-netbios.so
[3498/4084] Linking default/source4/smbd/libprocess-model-standard.inst.so
[3499/4084] Linking default/source4/lib/cmdline/libcmdline-credentials.inst.so
[3500/4084] Linking default/source4/nbt_server/libldb-wins-ldb.inst.so
[3501/4084] Linking default/libcli/nbt/python-netbios.inst.so
[3502/4084] Linking default/librpc/libdcerpc-samba.inst.so
[3503/4084] Linking default/librpc/libdcerpc-samba.so
[3504/4084] Linking default/source4/smbd/libprocess-model-prefork.inst.so
[3505/4084] Linking default/source4/smbd/libprocess-model-prefork.so
[3506/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-subtree-rename.inst.so
[3507/4084] Linking default/auth/credentials/libsamba-credentials.inst.so
[3508/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-subtree-rename.so
[3509/4084] Linking default/source4/lib/cmdline/libcmdline-credentials.so
[3510/4084] Linking default/source3/liblibcli_lsa3.inst.so
[3511/4084] Linking default/source4/dsdb/libsamdb.inst.so
[3512/4084] Linking default/source4/smbd/libprocess-model-onefork.so
[3513/4084] Linking default/source4/dsdb/libsamdb.so
[3514/4084] Linking default/source4/param/libshares.so
[3515/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-resolve-oids.inst.so
[3516/4084] Linking default/source4/kdc/libdb-glue.inst.so
[3517/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-local-password.inst.so
[3518/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-anr.so
[3519/4084] Linking default/source4/kdc/libdb-glue.so
[3520/4084] Linking default/source4/param/libshares.inst.so
[3521/4084] Linking default/source4/kdc/libHDB_SAMBA4.so
[3522/4084] Linking default/dfs_server/libdfs_server_ad.inst.so
[3523/4084] Linking default/source4/kdc/libHDB_SAMBA4.inst.so
[3524/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-objectclass-attrs.inst.so
[3525/4084] Linking default/auth/gensec/libgensec.so
[3526/4084] Linking default/libcli/smb/libcli_smb_common.inst.so
[3527/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-local-password.so
[3528/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samba-secrets.inst.so
[3529/4084] Linking default/source3/liblibcli_lsa3.so
[3530/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-anr.inst.so
[3531/4084] Linking default/dfs_server/libdfs_server_ad.so
[3532/4084] Linking default/source4/dns_server/libdlz_bind9_for_torture.inst.so
[3533/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-objectclass-attrs.so
[3534/4084] Linking default/source4/auth/gensec/libgensec-krb5.so
[3535/4084] Linking default/source4/dns_server/libdlz_bind9_for_torture.so
[3536/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-resolve-oids.so
[3537/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samba-secrets.so
[3538/4084] Linking default/source4/libcli/ldap/libcli-ldap.so
[3539/4084] Linking default/source4/dns_server/libdlz-bind9-9.so
[3540/4084] Linking default/source4/kdc/libpac.so
[3541/4084] Linking default/source4/kdc/libpac.inst.so
[3542/4084] Linking default/source4/kdc/libmit-samba.inst.so
[3543/4084] Linking default/lib/ldb-samba/libldb-ildap.so
[3544/4084] Linking default/auth/gensec/libgensec.inst.so
[3545/4084] Linking default/lib/ldb-samba/libldbsamba-extensions.inst.so
[3546/4084] Linking default/lib/ldb-samba/libldb-ildap.inst.so
[3547/4084] Linking default/source4/kdc/libmit-samba.so
[3548/4084] Linking default/source4/auth/gensec/libgensec-krb5.inst.so
[3549/4084] Linking default/source4/dns_server/libdlz-bind9.inst.so
[3550/4084] Linking default/source4/libcli/ldap/libcli-ldap.inst.so
[3551/4084] Linking default/lib/ldb-samba/libldbsamba-extensions.so
[3552/4084] Linking default/libcli/cldap/libcli_cldap.inst.so
[3553/4084] Linking default/libcli/smb/libcli_smb_common.so
[3554/4084] Linking default/source4/dns_server/libdlz-bind9.so
[3555/4084] Linking default/source4/dns_server/libdlz-bind9-9.inst.so
[3556/4084] Linking default/source4/libcli/libsmbclient-raw.inst.so
[3557/4084] Linking default/source3/libsmbconf.so
[3558/4084] Linking default/libcli/cldap/libcli_cldap.so
[3559/4084] Linking default/source3/liblibcli_netlogon3.inst.so
[3560/4084] Linking default/source3/libsmbldap.so
[3561/4084] Linking default/source3/pys3param.so
[3562/4084] Linking default/source3/libsmbconf.inst.so
[3563/4084] Linking default/source3/liblibcli_netlogon3.so
[3564/4084] Linking default/source3/libsecrets3.so
[3565/4084] Linking default/source3/winbindd/libnss_info.inst.so
[3566/4084] Linking default/source4/libcli/libsmbclient-raw.so
[3567/4084] Linking default/source4/librpc/libdcerpc.so
[3568/4084] Linking default/source3/libcli_spoolss.inst.so
[3569/4084] Linking default/source4/librpc/libdcerpc-atsvc.inst.so
[3570/4084] Linking default/source3/pys3param.inst.so
[3571/4084] Linking default/source3/libsmbldap.inst.so
[3572/4084] Linking default/source4/lib/registry/libregistry.inst.so
[3573/4084] Linking default/source4/lib/messaging/libMESSAGING.inst.so
[3574/4084] Linking default/source4/librpc/libdcerpc-atsvc.so
[3575/4084] Linking default/source3/libutil_cmdline.so
[3576/4084] Linking default/source3/libcli_spoolss.so
[3577/4084] Linking default/source3/libsecrets3.inst.so
[3578/4084] Linking default/source3/libpopt_samba3.so
[3579/4084] Linking default/source4/lib/registry/libregistry.so
[3580/4084] Linking default/source3/winbindd/libnss_info.so
[3581/4084] Linking default/source3/libsmbldaphelper.inst.so
[3582/4084] Linking default/source4/lib/messaging/libMESSAGING.so
[3583/4084] Linking default/python/libsamba_python.inst.so
[3584/4084] Linking default/source4/librpc/libdcerpc-samr.so
[3585/4084] Linking default/source3/libgse.inst.so
[3586/4084] Linking default/source4/dsdb/samdb/ldb_modules/libdsdb-module.inst.so
[3587/4084] Linking default/source3/libprinting_migrate.inst.so
[3588/4084] Linking default/source3/winbindd/libnss-info-hash.so
[3589/4084] Linking default/python/libsamba_python.so
[3590/4084] Linking default/source4/librpc/python-dns.inst.so
[3591/4084] Linking default/source4/librpc/python-dcerpc-misc.so
[3592/4084] Linking default/source4/librpc/python-winreg.so
[3593/4084] Linking default/source4/librpc/python-svcctl.inst.so
[3594/4084] Linking default/source4/librpc/python-mgmt.inst.so
[3595/4084] Linking default/source4/librpc/python-dcerpc-drsblobs.so
[3596/4084] Linking default/source4/librpc/python-lsa.so
[3597/4084] Linking default/source4/librpc/libdcerpc-samba4.inst.so
[3598/4084] Linking default/source4/lib/messaging/python-messaging.so
[3599/4084] Linking default/source4/librpc/python-idmap.inst.so
[3600/4084] Linking default/source4/auth/gensec/pygensec.inst.so
[3601/4084] Linking default/source4/librpc/python-irpc.inst.so
[3602/4084] Linking default/source4/librpc/python-unixinfo.so
[3603/4084] Linking default/source4/librpc/python-dcerpc-xattr.so
[3604/4084] Linking default/source4/librpc/python-auth.inst.so
[3605/4084] Linking default/source4/ntvfs/posix/python-posix-eadb.inst.so
[3606/4084] Linking default/source3/libsmbldaphelper.so
[3607/4084] Linking default/source4/librpc/python-dnsserver.so
[3608/4084] Linking default/source4/librpc/python-samr.so
[3609/4084] Linking default/source4/lib/registry/py-registry.so
[3610/4084] Linking default/source4/ntvfs/posix/python-xattr-tdb.inst.so
[3611/4084] Linking default/python/python-glue.inst.so
[3612/4084] Linking default/source4/librpc/python-lsa.inst.so
[3613/4084] Linking default/source4/libcli/pysmb.inst.so
[3614/4084] Linking default/source4/librpc/python-dcerpc-smb-acl.so
[3615/4084] Linking default/source4/librpc/python-dfs.inst.so
[3616/4084] Linking default/source4/librpc/python-initshutdown.so
[3617/4084] Linking default/source4/libnet/python-dckeytab.inst.so
[3618/4084] Linking default/source3/libpdb.inst.so
[3619/4084] Linking default/source4/librpc/python-dcerpc-security.inst.so
[3620/4084] Linking default/source4/librpc/python-netlogon.so
[3621/4084] Linking default/source4/dsdb/python-dsdb.so
[3622/4084] Linking default/source4/librpc/python-dns.so
[3623/4084] Linking default/source4/libnet/libsamba-net.so
[3624/4084] Linking default/source4/librpc/python-dnsserver.inst.so
[3625/4084] Linking default/source4/librpc/python-dcerpc-misc.inst.so
[3626/4084] Linking default/source4/librpc/python-atsvc.inst.so
[3627/4084] Linking default/source4/librpc/libdcerpc-samba4.so
[3628/4084] Linking default/source4/librpc/python-idmap.so
[3629/4084] Linking default/source4/librpc/python-mgmt.so
[3630/4084] Linking default/source4/librpc/python-dcerpc-nbt.so
[3631/4084] Linking default/source3/libprinting_migrate.so
[3632/4084] Linking default/source4/librpc/python-drsuapi.inst.so
[3633/4084] Linking default/source3/libutil_cmdline.inst.so
[3634/4084] Linking default/source4/librpc/python-dcerpc-drsblobs.inst.so
[3635/4084] Linking default/source4/libcli/wbclient/libLIBWBCLIENT_OLD.so
[3636/4084] Linking default/python/python-glue.so
[3637/4084] Linking default/source4/lib/policy/libsamba-policy.so
[3638/4084] Linking default/source4/librpc/python-svcctl.so
[3639/4084] Linking default/source4/librpc/python-auth.so
[3640/4084] Linking default/source3/libpdb.so
[3641/4084] Linking default/source3/pam_smbpass/libpamsmbpass.inst.so
[3642/4084] Linking default/source3/winbindd/libidmap.inst.so
[3643/4084] Linking default/source3/pam_smbpass/libpamsmbpass.so
[3644/4084] Linking default/source4/librpc/libdcerpc-samr.inst.so
[3645/4084] Linking default/source4/librpc/python-dcerpc-security.so
[3646/4084] Linking default/source4/librpc/python-unixinfo.inst.so
[3647/4084] Linking default/source4/librpc/python-initshutdown.inst.so
[3648/4084] Linking default/source4/libcli/wbclient/libLIBWBCLIENT_OLD.inst.so
[3649/4084] Linking default/source4/lib/registry/py-registry.inst.so
[3650/4084] Linking default/source3/libpopt_samba3.inst.so
[3651/4084] Linking default/source4/libnet/python-net.so
[3652/4084] Linking default/source3/libgse.so
[3653/4084] Linking default/source4/librpc/python-dcerpc-dnsp.inst.so
[3654/4084] Linking default/source4/libnet/python-net.inst.so
[3655/4084] Linking default/source3/passdb/pypassdb.so
[3656/4084] Linking default/source4/librpc/libdcerpc.inst.so
[3657/4084] Linking default/source4/dsdb/python-dsdb.inst.so
[3658/4084] Linking default/source4/librpc/python-dcerpc-xattr.inst.so
[3659/4084] Linking default/source4/librpc/python-samr.inst.so
[3660/4084] Linking default/source4/librpc/python-krb5pac.inst.so
[3661/4084] Linking default/source4/librpc/python-winbind.so
[3662/4084] Linking default/source4/ntvfs/posix/python-xattr-native.so
[3663/4084] Linking default/source4/auth/gensec/pygensec.so
[3664/4084] Linking default/source4/lib/policy/libsamba-policy.inst.so
[3665/4084] Linking default/source4/librpc/python-dcerpc-dnsp.so
[3666/4084] Linking default/lib/ldb-samba/python-samba--ldb.inst.so
[3667/4084] Linking default/source4/librpc/python-dcerpc.inst.so
[3668/4084] Linking default/source4/dsdb/samdb/ldb_modules/libdsdb-module.so
[3669/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-aclread.so
[3670/4084] Linking default/auth/credentials/pycredentials.so
[3671/4084] Linking default/source4/lib/policy/py-policy.so
[3672/4084] Linking default/source4/librpc/python-echo.so
[3673/4084] Linking default/source4/librpc/python-server-id.so
[3674/4084] Linking default/source4/librpc/python-dcerpc-smb-acl.inst.so
[3675/4084] Linking default/source3/winbindd/libnss-info-hash.inst.so
[3676/4084] Linking default/source4/librpc/python-dcerpc-nbt.inst.so
[3677/4084] Linking default/source4/librpc/python-drsuapi.so
[3678/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-objectguid.inst.so
[3679/4084] Linking default/source4/ntvfs/posix/python-xattr-tdb.so
[3680/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-extended-dn-out.inst.so
[3681/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samba-dsdb.so
[3682/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-operational.so
[3683/4084] Linking default/source3/liblibsmb.inst.so
[3684/4084] Linking default/source4/librpc/python-wkssvc.so
[3685/4084] Linking default/source4/librpc/python-dfs.so
[3686/4084] Linking default/source4/ntvfs/posix/python-posix-eadb.so
[3687/4084] Linking default/source4/libcli/pysmb.so
[3688/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samldb.inst.so
[3689/4084] Linking default/source4/librpc/python-srvsvc.inst.so
[3690/4084] Linking default/source4/librpc/python-dcerpc-idmap.so
[3691/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samba3sid.so
[3692/4084] Linking default/source4/librpc/python-winreg.inst.so
[3693/4084] Linking default/source4/librpc/python-epmapper.so
[3694/4084] Linking default/auth/credentials/pycredentials.inst.so
[3695/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-objectguid.so
[3696/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-lazy-commit.so
[3697/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-new-partition.so
[3698/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-simple-dn.so
[3699/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-instancetype.so
[3700/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-extended-dn-in.inst.so
[3701/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-instancetype.inst.so
[3702/4084] Linking default/source4/librpc/python-winbind.inst.so
[3703/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-password-hash.inst.so
[3704/4084] Linking default/source3/passdb/pypassdb.inst.so
[3705/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-lazy-commit.inst.so
[3706/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-linked-attributes.so
[3707/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-objectclass.so
[3708/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-extended-dn-store.inst.so
[3709/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-rootdse.so
[3710/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samba-dsdb.inst.so
[3711/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-subtree-delete.inst.so
[3712/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-repl-meta-data.so
[3713/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-show-deleted.so
[3714/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-simple-dn.inst.so
[3715/4084] Linking default/source4/librpc/python-irpc.so
[3716/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-dirsync.inst.so
[3717/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-extended-dn-out.so
[3718/4084] Linking default/source4/librpc/python-epmapper.inst.so
[3719/4084] Linking default/source4/librpc/python-server-id.inst.so
[3720/4084] Linking default/source3/winbindd/libidmap.so
[3721/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-password-hash.so
[3722/4084] Linking default/source4/librpc/python-srvsvc.so
[3723/4084] Linking default/source4/librpc/python-wkssvc.inst.so
[3724/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-update-keytab.so
[3725/4084] Linking default/source3/winbindd/libidmap-hash.so
[3726/4084] Linking default/source4/libnet/libsamba-net.inst.so
[3727/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-operational.inst.so
[3728/4084] Linking default/source4/librpc/python-echo.inst.so
[3729/4084] Linking default/source4/auth/libauth_unix_token.inst.so
[3730/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-secrets-tdb-sync.inst.so
[3731/4084] Linking default/source4/librpc/python-netlogon.inst.so
[3732/4084] Linking default/source4/librpc/python-dcerpc-idmap.inst.so
[3733/4084] Linking default/source4/libnet/python-dckeytab.so
[3734/4084] Linking default/lib/ldb-samba/python-samba--ldb.so
[3735/4084] Linking default/source4/librpc/python-krb5pac.so
[3736/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-aclread.inst.so
[3737/4084] Linking default/source4/lib/messaging/python-messaging.inst.so
[3738/4084] Linking default/source4/librpc/python-atsvc.so
[3739/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-schema-data.so
[3740/4084] Linking default/source4/librpc/python-dcerpc.so
[3741/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-rootdse.inst.so
[3742/4084] Linking default/source4/ntvfs/posix/python-xattr-native.inst.so
[3743/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-show-deleted.inst.so
[3744/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-schema-load.inst.so
[3745/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-dirsync.so
[3746/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-partition.inst.so
[3747/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-extended-dn-store.so
[3748/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samldb.so
[3749/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-acl.inst.so
[3750/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-partition.so
[3751/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-schema-load.so
[3752/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-extended-dn-in.so
[3753/4084] Linking default/source4/lib/policy/py-policy.inst.so
[3754/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-acl.so
[3755/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-update-keytab.inst.so
[3756/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-objectclass.inst.so
[3757/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-schema-data.inst.so
[3758/4084] Linking default/source3/liblibsmb.so
[3759/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-linked-attributes.inst.so
[3760/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-descriptor.inst.so
[3761/4084] Linking default/source4/auth/libauth_unix_token.so
[3762/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-subtree-delete.so
[3763/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-new-partition.inst.so
[3764/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-repl-meta-data.inst.so
[3765/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-secrets-tdb-sync.so
[3766/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-descriptor.so
[3767/4084] Linking default/source4/dsdb/samdb/ldb_modules/libldb-samba3sid.inst.so
[3768/4084] Linking default/source3/winbindd/libidmap-rid.inst.so
[3769/4084] Linking default/source3/winbindd/libidmap-tdb2.inst.so
[3770/4084] Linking default/source3/winbindd/libidmap-autorid.inst.so
[3771/4084] Linking default/source4/auth/ntlm/libauth4.inst.so
[3772/4084] Linking default/source4/auth/ntlm/libauth4.so
[3773/4084] Linking default/source4/ntvfs/libntvfs.so
[3774/4084] Linking default/source3/winbindd/libidmap-rid.so
[3775/4084] Linking default/source3/winbindd/libidmap-hash.inst.so
[3776/4084] Linking default/source3/libnss-wins.inst.so
[3777/4084] Linking default/source4/ntvfs/libntvfs.inst.so
[3778/4084] Linking default/source4/auth/pyauth.inst.so
[3779/4084] Linking default/source4/smbd/libservice.so
[3780/4084] Linking default/source3/libmsrpc3.inst.so
[3781/4084] Linking default/source3/winbindd/libidmap-autorid.so
[3782/4084] Linking default/source4/dsdb/libservice-kcc.so
[3783/4084] Linking default/source3/libmsrpc3.so
[3784/4084] Linking default/source4/dsdb/libservice-kcc.inst.so
[3785/4084] Linking default/source3/libnss-wins.so
[3786/4084] Linking default/source4/auth/pyauth.so
[3787/4084] Linking default/source4/dsdb/libservice-dns-update.so
[3788/4084] Linking default/source3/libtrusts_util.inst.so
[3789/4084] Linking default/source4/ldap_server/libservice-ldap.so
[3790/4084] Linking default/source4/web_server/libservice-web.so
[3791/4084] Linking default/source4/ldap_server/libservice-ldap.inst.so
[3792/4084] Linking default/source3/libtrusts_util.so
[3793/4084] Linking default/source3/winbindd/libidmap-tdb2.so
[3794/4084] Linking default/source4/smbd/libservice.inst.so
[3795/4084] Linking default/source4/dsdb/libservice-drepl.so
[3796/4084] Linking default/source4/kdc/libservice-kdc.inst.so
[3797/4084] Linking default/source4/wrepl_server/libservice-wrepl.inst.so
[3798/4084] Linking default/file_server/libservice-s3fs.inst.so
[3799/4084] Linking default/source4/cldap_server/libservice-cldap.so
[3800/4084] Linking default/source4/smb_server/libservice-smb.inst.so
[3801/4084] Linking default/source4/smb_server/libservice-smb.so
[3802/4084] Linking default/source4/winbind/libservice-winbind.so
[3803/4084] Linking default/source4/winbind/libservice-winbind.inst.so
[3804/4084] Linking default/source4/dsdb/libservice-dns-update.inst.so
[3805/4084] Linking default/source4/nbt_server/libservice-nbtd.so
[3806/4084] Linking default/source4/ntp_signd/libservice-ntp-signd.so
[3807/4084] Linking default/source4/cldap_server/libservice-cldap.inst.so
[3808/4084] Linking default/source3/libads.inst.so
[3809/4084] Linking default/source4/web_server/libservice-web.inst.so
[3810/4084] Linking default/file_server/libservice-s3fs.so
[3811/4084] Linking default/source4/nbt_server/libservice-nbtd.inst.so
[3812/4084] Linking default/source3/libsmb/libsmbclient.inst.so
[3813/4084] Linking default/source4/kdc/libservice-kdc.so
[3814/4084] Linking default/source3/libads.so
[3815/4084] Linking default/source4/dsdb/libservice-drepl.inst.so
[3816/4084] Linking default/source4/ntp_signd/libservice-ntp-signd.inst.so
ls [3817/4084] Linking default/source4/wrepl_server/libservice-wrepl.so
[3818/4084] Linking default/source3/auth/libauth.inst.so
/etc[3819/4084] Linking default/source3/libnet_keytab.inst.so
/i[3820/4084] Linking default/source3/libsmb/libsmbclient.so
nit.[3821/4084] Linking default/source3/libnet_keytab.so
d[3822/4084] Linking default/source3/pylibsmb.so
[3823/4084] Linking default/source3/auth/libauth.so
[3824/4084] Linking default/source3/auth/libauth-script.inst.so
[3825/4084] Linking default/source3/libgpo.inst.so
[3826/4084] Linking default/source4/dns_server/libservice-dns.so
[3827/4084] Linking default/source3/libgpo.so
[3828/4084] Linking default/source3/auth/libauth-script.so
[3829/4084] Linking default/source3/pylibsmb.inst.so
[3830/4084] Linking default/source3/libnetapi.inst.so
[3831/4084] Linking default/source3/libnetapi.so
[3832/4084] Linking default/source4/dns_server/libservice-dns.inst.so
[3833/4084] Linking default/source4/rpc_server/libdcerpc-server.inst.so
[3834/4084] Linking default/source4/rpc_server/libdcerpc-server.so
[3835/4084] Linking default/source3/libsmbd_base.so
[3836/4084] Linking default/source3/modules/libvfs-commit.inst.so
[3837/4084] Linking default/source3/modules/libvfs-streams-depot.so
[3838/4084] Linking default/source3/modules/libvfs-aio-pthread.inst.so
[3839/4084] Linking default/source3/modules/libvfs-aio-linux.so
[3840/4084] Linking default/source3/modules/libvfs-scannedonly.inst.so
[3841/4084] Linking default/source3/libsmbd_base.inst.so
[3842/4084] Linking default/source3/modules/libvfs-crossrename.inst.so
[3843/4084] Linking default/source3/modules/libvfs-aio-pthread.so
[3844/4084] Linking default/source3/modules/libvfs-media-harmony.so
[3845/4084] Linking default/source3/modules/libvfs-xattr-tdb.inst.so
[3846/4084] Linking default/source3/modules/libvfs-posix-eadb.so
[3847/4084] Linking default/source3/modules/libvfs-readahead.inst.so
[3848/4084] Linking default/source3/modules/libvfs-streams-xattr.so
[3849/4084] Linking default/source3/modules/libvfs-default-quota.inst.so
[3850/4084] Linking default/source3/modules/libvfs-shadow-copy.inst.so
[3851/4084] Linking default/source3/modules/libvfs-expand-msdfs.so
[3852/4084] Linking default/source3/modules/libvfs-xattr-tdb.so
[3853/4084] Linking default/source4/rpc_server/libservice-dcerpc.so
[3854/4084] Linking default/source3/modules/libvfs-netatalk.so
[3855/4084] Linking default/source3/modules/libvfs-posix-eadb.inst.so
[3856/4084] Linking default/source3/modules/libvfs-linux-xfs-sgid.inst.so
[3857/4084] Linking default/source3/modules/libvfs-preopen.so
[3858/4084] Linking default/source3/modules/libvfs-smb-traffic-analyzer.inst.so
[3859/4084] Linking default/source3/modules/libvfs-shadow-copy.so
[3860/4084] Linking default/source3/modules/libvfs-recycle.so
[3861/4084] Linking default/source3/pysmbd.so
[3862/4084] Linking default/source3/modules/libvfs-acl-xattr.so
[3863/4084] Linking default/source3/modules/libvfs-fileid.inst.so
[3864/4084] Linking default/source3/modules/libvfs-aio-posix.so
[3865/4084] Linking default/source3/modules/libvfs-cap.inst.so
[3866/4084] Linking default/source3/modules/libvfs-time-audit.so
[3867/4084] Linking default/source3/modules/libvfs-aio-linux.inst.so
[3868/4084] Linking default/source3/modules/libvfs-fake-perms.inst.so
[3869/4084] Linking default/source3/modules/libvfs-preopen.inst.so
[3870/4084] Linking default/source3/modules/libvfs-audit.inst.so
[3871/4084] Linking default/source3/modules/libvfs-audit.so
[3872/4084] Linking default/source3/modules/libvfs-default-quota.so
[3873/4084] Linking default/source3/modules/libvfs-full-audit.inst.so
[3874/4084] Linking default/source3/modules/libvfs-extd-audit.inst.so
[3875/4084] Linking default/source3/modules/libvfs-readahead.so
[3876/4084] Linking default/source3/modules/libvfs-aio-fork.inst.so
[3877/4084] Linking default/source3/modules/libvfs-smb-traffic-analyzer.so
[3878/4084] Linking default/source3/modules/libvfs-acl-xattr.inst.so
[3879/4084] Linking default/source4/rpc_server/libservice-dcerpc.inst.so
[3880/4084] Linking default/source3/modules/libvfs-full-audit.so
[3881/4084] Linking default/source3/modules/libvfs-shadow-copy2.inst.so
[3882/4084] Linking default/source3/modules/libvfs-extd-audit.so
[3883/4084] Linking default/source3/modules/libvfs-catia.inst.so
[3884/4084] Linking default/source3/modules/libvfs-dirsort.so
[3885/4084] Linking default/source3/modules/libvfs-catia.so
[3886/4084] Linking default/source3/modules/libvfs-acl-tdb.so
[3887/4084] Linking default/source3/modules/libvfs-syncops.inst.so
[3888/4084] Linking default/source3/modules/libvfs-aio-posix.inst.so
[3889/4084] Linking default/source3/modules/libvfs-crossrename.so
[3890/4084] Linking default/source3/modules/libvfs-streams-depot.inst.so
[3891/4084] Linking default/source3/modules/libvfs-syncops.so
[3892/4084] Linking default/source3/modules/libvfs-streams-xattr.inst.so
[3893/4084] Linking default/source3/modules/libvfs-dirsort.inst.so
[3894/4084] Linking default/source3/pysmbd.inst.so
[3895/4084] Linking default/source3/modules/libvfs-cap.so
[3896/4084] Linking default/source3/modules/libvfs-commit.so
[3897/4084] Linking default/source3/modules/libvfs-readonly.so
[3898/4084] Linking default/source3/modules/libvfs-scannedonly.so
[3899/4084] Linking default/source3/modules/libvfs-netatalk.inst.so
[3900/4084] Linking default/source3/modules/libvfs-readonly.inst.so
[3901/4084] Linking default/source3/modules/libvfs-expand-msdfs.inst.so
[3902/4084] Linking default/source3/modules/libvfs-fileid.so
[3903/4084] Linking default/source3/modules/libvfs-acl-tdb.inst.so
[3904/4084] Linking default/source3/modules/libvfs-fake-perms.so
[3905/4084] Linking default/source3/modules/libvfs-shadow-copy2.so
[3906/4084] Linking default/source3/modules/libvfs-aio-fork.so
[3907/4084] Linking default/source3/modules/libvfs-recycle.inst.so
[3908/4084] Linking default/source3/modules/libvfs-linux-xfs-sgid.so
[3909/4084] Linking default/source3/modules/libvfs-time-audit.inst.so
[3910/4084] Linking default/source3/modules/libvfs-media-harmony.inst.so
* installing swat/help/welcome-no-samba-doc.html as /usr/local/samba/share/swat/help/welcome-no-samba-doc.html
* installing swat/help/welcome.html as /usr/local/samba/share/swat/help/welcome.html
* installing swat/lang/tr/help/welcome.html as /usr/local/samba/share/swat/lang/tr/help/welcome.html
* installing swat/lang/tr/images/shares.gif as /usr/local/samba/share/swat/lang/tr/images/shares.gif
* installing swat/lang/tr/images/viewconfig.gif as /usr/local/samba/share/swat/lang/tr/images/viewconfig.gif
* installing swat/lang/tr/images/globals.gif as /usr/local/samba/share/swat/lang/tr/images/globals.gif
* installing swat/lang/tr/images/home.gif as /usr/local/samba/share/swat/lang/tr/images/home.gif
* installing swat/lang/tr/images/samba.gif as /usr/local/samba/share/swat/lang/tr/images/samba.gif
* installing swat/lang/tr/images/printers.gif as /usr/local/samba/share/swat/lang/tr/images/printers.gif
* installing swat/lang/tr/images/status.gif as /usr/local/samba/share/swat/lang/tr/images/status.gif
* installing swat/lang/tr/images/passwd.gif as /usr/local/samba/share/swat/lang/tr/images/passwd.gif
* installing swat/lang/ru/help/welcome-no-samba-doc.html as /usr/local/samba/share/swat/lang/ru/help/welcome-no-samba-doc.html
* installing swat/lang/ru/help/welcome.html as /usr/local/samba/share/swat/lang/ru/help/welcome.html
* installing swat/lang/ru/include/header.html as /usr/local/samba/share/swat/lang/ru/include/header.html
* installing swat/lang/ru/images/wizard.gif as /usr/local/samba/share/swat/lang/ru/images/wizard.gif
* installing swat/lang/ru/images/shares.gif as /usr/local/samba/share/swat/lang/ru/images/shares.gif
* installing swat/lang/ru/images/viewconfig.gif as /usr/local/samba/share/swat/lang/ru/images/viewconfig.gif
* installing swat/lang/ru/images/globals.gif as /usr/local/samba/share/swat/lang/ru/images/globals.gif
* installing swat/lang/ru/images/home.gif as /usr/local/samba/share/swat/lang/ru/images/home.gif
* installing swat/lang/ru/images/printers.gif as /usr/local/samba/share/swat/lang/ru/images/printers.gif
* installing swat/lang/ru/images/status.gif as /usr/local/samba/share/swat/lang/ru/images/status.gif
* installing swat/lang/ru/images/passwd.gif as /usr/local/samba/share/swat/lang/ru/images/passwd.gif
* installing swat/lang/ja/help/welcome.html as /usr/local/samba/share/swat/lang/ja/help/welcome.html
* installing swat/include/footer.html as /usr/local/samba/share/swat/include/footer.html
* installing swat/include/header.html as /usr/local/samba/share/swat/include/header.html
* installing swat/images/wizard.gif as /usr/local/samba/share/swat/images/wizard.gif
* installing swat/images/shares.gif as /usr/local/samba/share/swat/images/shares.gif
* installing swat/images/viewconfig.gif as /usr/local/samba/share/swat/images/viewconfig.gif
* installing swat/images/globals.gif as /usr/local/samba/share/swat/images/globals.gif
* installing swat/images/home.gif as /usr/local/samba/share/swat/images/home.gif
* installing swat/images/samba.gif as /usr/local/samba/share/swat/images/samba.gif
* installing swat/images/printers.gif as /usr/local/samba/share/swat/images/printers.gif
* installing swat/images/status.gif as /usr/local/samba/share/swat/images/status.gif
* installing swat/images/passwd.gif as /usr/local/samba/share/swat/images/passwd.gif
* installing source3/po/fi.msg as /usr/local/samba/share/codepages/fi.msg
* installing source3/po/ja.msg as /usr/local/samba/share/codepages/ja.msg
* installing source3/po/ru.msg as /usr/local/samba/share/codepages/ru.msg
* installing source3/po/de.msg as /usr/local/samba/share/codepages/de.msg
* installing source3/po/en.msg as /usr/local/samba/share/codepages/en.msg
* installing source3/po/it.msg as /usr/local/samba/share/codepages/it.msg
* installing source3/po/nl.msg as /usr/local/samba/share/codepages/nl.msg
* installing source3/po/pl.msg as /usr/local/samba/share/codepages/pl.msg
* installing source3/po/tr.msg as /usr/local/samba/share/codepages/tr.msg
* installing source3/po/fr.msg as /usr/local/samba/share/codepages/fr.msg
* installing bin/default/lib/socket/libinterfaces.inst.so as /usr/local/samba/lib/private/libinterfaces.so
* installing bin/default/lib/util/libsamba-util.inst.so as /usr/local/samba/lib/libsamba-util.so.0.0.1
* installing bin/default/lib/util/libutil_setid.inst.so as /usr/local/samba/lib/private/libutil_setid.so
* installing bin/default/lib/talloc/libtalloc.inst.so as /usr/local/samba/lib/private/libtalloc.so.2.0.7
* symlink /usr/local/samba/lib/private/libtalloc.so.2 (-> libtalloc.so.2.0.7)
* installing bin/default/lib/talloc/libpytalloc-util.inst.so as /usr/local/samba/lib/private/libpytalloc-util.so.2.0.7
* symlink /usr/local/samba/lib/private/libpytalloc-util.so.2 (-> libpytalloc-util.so.2.0.7)
* installing bin/default/lib/talloc/pytalloc.inst.so as /usr/local/samba/lib/python2.7/site-packages/talloc.so
* installing bin/default/lib/tevent/libtevent.inst.so as /usr/local/samba/lib/private/libtevent.so.0.9.18
* symlink /usr/local/samba/lib/private/libtevent.so.0 (-> libtevent.so.0.9.18)
* installing bin/default/lib/tevent/pytevent.inst.so as /usr/local/samba/lib/python2.7/site-packages/_tevent.so
* installing bin/default/lib/addns/libaddns.inst.so as /usr/local/samba/lib/private/libaddns.so
* installing bin/default/libcli/util/liberrors.inst.so as /usr/local/samba/lib/private/liberrors.so
* installing bin/default/librpc/libndr.inst.so as /usr/local/samba/lib/libndr.so.0.0.1
* installing bin/default/source4/heimdal_build/libgssapi-samba4.inst.so as /usr/local/samba/lib/private/libgssapi-samba4.so.2.0.0
* symlink /usr/local/samba/lib/private/libgssapi-samba4.so.2 (-> libgssapi-samba4.so.2.0.0)
* installing bin/default/source4/heimdal_build/libkrb5-samba4.inst.so as /usr/local/samba/lib/private/libkrb5-samba4.so.26.0.0
* symlink /usr/local/samba/lib/private/libkrb5-samba4.so.26 (-> libkrb5-samba4.so.26.0.0)
* installing bin/default/source4/heimdal_build/libheimbase-samba4.inst.so as /usr/local/samba/lib/private/libheimbase-samba4.so.1.0.0
* symlink /usr/local/samba/lib/private/libheimbase-samba4.so.1 (-> libheimbase-samba4.so.1.0.0)
* installing bin/default/source4/heimdal_build/libroken-samba4.inst.so as /usr/local/samba/lib/private/libroken-samba4.so.19.0.1
* symlink /usr/local/samba/lib/private/libroken-samba4.so.19 (-> libroken-samba4.so.19.0.1)
* installing bin/default/source4/heimdal_build/libasn1-samba4.inst.so as /usr/local/samba/lib/private/libasn1-samba4.so.8.0.0
* symlink /usr/local/samba/lib/private/libasn1-samba4.so.8 (-> libasn1-samba4.so.8.0.0)
* installing bin/default/source4/heimdal_build/libhx509-samba4.inst.so as /usr/local/samba/lib/private/libhx509-samba4.so.5.0.0
* symlink /usr/local/samba/lib/private/libhx509-samba4.so.5 (-> libhx509-samba4.so.5.0.0)
* installing bin/default/source4/heimdal_build/libhcrypto-samba4.inst.so as /usr/local/samba/lib/private/libhcrypto-samba4.so.5.0.1
* symlink /usr/local/samba/lib/private/libhcrypto-samba4.so.5 (-> libhcrypto-samba4.so.5.0.1)
* installing bin/default/source4/heimdal_build/libwind-samba4.inst.so as /usr/local/samba/lib/private/libwind-samba4.so.0.0.0
* symlink /usr/local/samba/lib/private/libwind-samba4.so.0 (-> libwind-samba4.so.0.0.0)
* installing bin/default/lib/ccan/libccan.inst.so as /usr/local/samba/lib/private/libccan.so
* installing bin/default/lib/tdb/libtdb.inst.so as /usr/local/samba/lib/private/libtdb.so.1.2.11
* symlink /usr/local/samba/lib/private/libtdb.so.1 (-> libtdb.so.1.2.11)
* installing bin/default/lib/tdb/pytdb.inst.so as /usr/local/samba/lib/python2.7/site-packages/tdb.so
* installing bin/default/lib/tdb_compat/libtdb_compat.inst.so as /usr/local/samba/lib/private/libtdb_compat.so
* installing bin/default/lib/ldb/libpyldb-util.inst.so as /usr/local/samba/lib/private/libpyldb-util.so.1.1.16
* symlink /usr/local/samba/lib/private/libpyldb-util.so.1 (-> libpyldb-util.so.1.1.16)
* installing bin/default/lib/ldb/libldb.inst.so as /usr/local/samba/lib/private/libldb.so.1.1.16
* symlink /usr/local/samba/lib/private/libldb.so.1 (-> libldb.so.1.1.16)
* installing bin/default/lib/ldb/pyldb.inst.so as /usr/local/samba/lib/python2.7/site-packages/ldb.so
* installing bin/default/lib/ldb/libldb-paged-results.inst.so as /usr/local/samba/lib/ldb/paged_results.so
* installing bin/default/lib/ldb/libldb-asq.inst.so as /usr/local/samba/lib/ldb/asq.so
* installing bin/default/lib/ldb/libldb-server-sort.inst.so as /usr/local/samba/lib/ldb/server_sort.so
* installing bin/default/lib/ldb/libldb-paged-searches.inst.so as /usr/local/samba/lib/ldb/paged_searches.so
* installing bin/default/lib/ldb/libldb-rdn-name.inst.so as /usr/local/samba/lib/ldb/rdn_name.so
* installing bin/default/lib/ldb/libldb-sample.inst.so as /usr/local/samba/lib/ldb/sample.so
* installing bin/default/lib/ldb/libldb-skel.inst.so as /usr/local/samba/lib/ldb/skel.so
* installing bin/default/lib/ldb/libldb-tdb.inst.so as /usr/local/samba/lib/ldb/tdb.so
* installing bin/default/lib/ldb/libldb-cmdline.inst.so as /usr/local/samba/lib/private/libldb-cmdline.so
* installing bin/default/lib/param/libserver-role.inst.so as /usr/local/samba/lib/private/libserver-role.so
* installing bin/default/lib/param/libsamba-hostconfig.inst.so as /usr/local/samba/lib/libsamba-hostconfig.so.0.0.1
* installing bin/default/python/libsamba_python.inst.so as /usr/local/samba/lib/private/libsamba_python.so
* installing bin/default/source4/lib/messaging/libMESSAGING.inst.so as /usr/local/samba/lib/private/libMESSAGING.so
* installing bin/default/lib/tdb_wrap/libtdb-wrap.inst.so as /usr/local/samba/lib/private/libtdb-wrap.so
* installing bin/default/source4/librpc/libndr-samba4.inst.so as /usr/local/samba/lib/private/libndr-samba4.so
* installing bin/default/librpc/libndr-samba.inst.so as /usr/local/samba/lib/private/libndr-samba.so
* installing bin/default/librpc/libndr-krb5pac.inst.so as /usr/local/samba/lib/libndr-krb5pac.so.0.0.1
* installing bin/default/librpc/libndr-standard.inst.so as /usr/local/samba/lib/libndr-standard.so.0.0.1
* installing bin/default/librpc/libndr-nbt.inst.so as /usr/local/samba/lib/libndr-nbt.so.0.0.1
* installing bin/default/libcli/security/libsamba-security.inst.so as /usr/local/samba/lib/private/libsamba-security.so
* installing bin/default/lib/util/libasn1util.inst.so as /usr/local/samba/lib/private/libasn1util.so
* installing bin/default/source4/librpc/libdcerpc.inst.so as /usr/local/samba/lib/libdcerpc.so.0.0.1
* installing bin/default/libcli/nbt/libcli-nbt.inst.so as /usr/local/samba/lib/private/libcli-nbt.so
* installing bin/default/lib/util/libtevent-util.inst.so as /usr/local/samba/lib/libtevent-util.so.0.0.1
* installing bin/default/lib/libsamba-sockets.inst.so as /usr/local/samba/lib/private/libsamba-sockets.so
* installing bin/default/source4/lib/events/libevents.inst.so as /usr/local/samba/lib/private/libevents.so
* installing bin/default/source4/libcli/libsmbclient-raw.inst.so as /usr/local/samba/lib/libsmbclient-raw.so.0.0.1
* installing bin/default/auth/credentials/libsamba-credentials.inst.so as /usr/local/samba/lib/libsamba-credentials.so.0.0.1
* installing bin/default/source4/dsdb/libsamdb-common.inst.so as /usr/local/samba/lib/private/libsamdb-common.so
* installing bin/default/libds/common/libflag_mapping.inst.so as /usr/local/samba/lib/private/libflag_mapping.so
* installing bin/default/libcli/ldap/libcli-ldap-common.inst.so as /usr/local/samba/lib/private/libcli-ldap-common.so
* installing bin/default/libcli/auth/libcliauth.inst.so as /usr/local/samba/lib/private/libcliauth.so
* installing bin/default/lib/util/libutil_tdb.inst.so as /usr/local/samba/lib/private/libutil_tdb.so
* installing bin/default/lib/krb5_wrap/libkrb5samba.inst.so as /usr/local/samba/lib/private/libkrb5samba.so
* installing bin/default/source4/auth/kerberos/libauthkrb5.inst.so as /usr/local/samba/lib/private/libauthkrb5.so
* installing bin/default/auth/libauth_sam_reply.inst.so as /usr/local/samba/lib/private/libauth_sam_reply.so
* installing bin/default/lib/ldb-samba/libldbsamba.inst.so as /usr/local/samba/lib/private/libldbsamba.so
* installing bin/default/lib/dbwrap/libdbwrap.inst.so as /usr/local/samba/lib/private/libdbwrap.so
* installing bin/default/libcli/smb/libcli_smb_common.inst.so as /usr/local/samba/lib/private/libcli_smb_common.so
* installing bin/default/libcli/smb/libsmb_transport.inst.so as /usr/local/samba/lib/private/libsmb_transport.so
* installing bin/default/auth/gensec/libgensec.inst.so as /usr/local/samba/lib/libgensec.so.0.0.1
* installing bin/default/lib/util/libsamba-modules.inst.so as /usr/local/samba/lib/private/libsamba-modules.so
* installing bin/default/source4/dsdb/libsamdb.inst.so as /usr/local/samba/lib/libsamdb.so.0.0.1
* installing bin/default/librpc/libdcerpc-binding.inst.so as /usr/local/samba/lib/libdcerpc-binding.so.0.0.1
* installing bin/default/libcli/cldap/libcli_cldap.inst.so as /usr/local/samba/lib/private/libcli_cldap.so
* installing bin/default/source4/libcli/ldap/libcli-ldap.inst.so as /usr/local/samba/lib/private/libcli-ldap.so
* installing bin/default/source4/lib/socket/libnetif.inst.so as /usr/local/samba/lib/private/libnetif.so
* installing bin/default/librpc/libdcerpc-samba.inst.so as /usr/local/samba/lib/private/libdcerpc-samba.so
* installing bin/default/source4/cluster/libcluster.inst.so as /usr/local/samba/lib/private/libcluster.so
* installing bin/default/python/python-glue.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/_glue.so
* installing bin/default/source4/param/pyparam.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/param.so
* installing bin/default/source4/param/libshares.inst.so as /usr/local/samba/lib/private/libshares.so
* installing bin/default/source4/librpc/libdcerpc-samba4.inst.so as /usr/local/samba/lib/private/libdcerpc-samba4.so
* installing bin/default/source4/librpc/libdcerpc-samr.inst.so as /usr/local/samba/lib/libdcerpc-samr.so.0.0.1
* installing bin/default/source4/librpc/libdcerpc-atsvc.inst.so as /usr/local/samba/lib/libdcerpc-atsvc.so.0.0.1
* installing bin/default/source4/librpc/python-dcerpc.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/base.so
* installing bin/default/source4/librpc/python-srvsvc.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/srvsvc.so
* installing bin/default/source4/librpc/python-echo.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/echo.so
* installing bin/default/source4/librpc/python-dns.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/dns.so
* installing bin/default/source4/librpc/python-auth.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/auth.so
* installing bin/default/source4/librpc/python-krb5pac.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/krb5pac.so
* installing bin/default/source4/librpc/python-winreg.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/winreg.so
* installing bin/default/source4/librpc/python-dcerpc-misc.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/misc.so
* installing bin/default/source4/librpc/python-initshutdown.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/initshutdown.so
* installing bin/default/source4/librpc/python-epmapper.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/epmapper.so
* installing bin/default/source4/librpc/python-mgmt.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/mgmt.so
* installing bin/default/source4/librpc/python-atsvc.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/atsvc.so
* installing bin/default/source4/librpc/python-dcerpc-nbt.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/nbt.so
* installing bin/default/source4/librpc/python-samr.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/samr.so
* installing bin/default/source4/librpc/python-svcctl.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/svcctl.so
* installing bin/default/source4/librpc/python-lsa.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/lsa.so
* installing bin/default/source4/librpc/python-wkssvc.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/wkssvc.so
* installing bin/default/source4/librpc/python-dfs.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/dfs.so
* installing bin/default/source4/librpc/python-unixinfo.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/unixinfo.so
* installing bin/default/source4/librpc/python-irpc.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/irpc.so
* installing bin/default/source4/librpc/python-server-id.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/server_id.so
* installing bin/default/source4/librpc/python-winbind.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/winbind.so
* installing bin/default/source4/librpc/python-netlogon.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/netlogon.so
* installing bin/default/source4/librpc/python-idmap.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/idmap.so
* installing bin/default/source4/librpc/python-drsuapi.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/drsuapi.so
* installing bin/default/source4/librpc/python-dcerpc-security.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/security.so
* installing bin/default/source4/librpc/python-dcerpc-drsblobs.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/drsblobs.so
* installing bin/default/source4/librpc/python-dcerpc-dnsp.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/dnsp.so
* installing bin/default/source4/librpc/python-dcerpc-xattr.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/xattr.so
* installing bin/default/source4/librpc/python-dcerpc-idmap.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/idmap.so
* installing bin/default/source4/librpc/python-dnsserver.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/dnsserver.so
* installing bin/default/source4/librpc/python-dcerpc-smb-acl.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dcerpc/smb_acl.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libdsdb-module.inst.so as /usr/local/samba/lib/private/libdsdb-module.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-samba-dsdb.inst.so as /usr/local/samba/lib/ldb/samba_dsdb.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-samba-secrets.inst.so as /usr/local/samba/lib/ldb/samba_secrets.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-objectguid.inst.so as /usr/local/samba/lib/ldb/objectguid.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-repl-meta-data.inst.so as /usr/local/samba/lib/ldb/repl_meta_data.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-schema-load.inst.so as /usr/local/samba/lib/ldb/schema_load.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-schema-data.inst.so as /usr/local/samba/lib/ldb/schema_data.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-samldb.inst.so as /usr/local/samba/lib/ldb/samldb.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-samba3sam.inst.so as /usr/local/samba/lib/ldb/samba3sam.so
* installing bin/default/source4/lib/samba3/libsmbpasswdparser.inst.so as /usr/local/samba/lib/private/libsmbpasswdparser.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-samba3sid.inst.so as /usr/local/samba/lib/ldb/samba3sid.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-simple-ldap-map.inst.so as /usr/local/samba/lib/ldb/simple_ldap_map.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-rootdse.inst.so as /usr/local/samba/lib/ldb/rootdse.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-password-hash.inst.so as /usr/local/samba/lib/ldb/password_hash.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-local-password.inst.so as /usr/local/samba/lib/ldb/local_password.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-extended-dn-in.inst.so as /usr/local/samba/lib/ldb/extended_dn_in.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-extended-dn-out.inst.so as /usr/local/samba/lib/ldb/extended_dn_out.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-extended-dn-store.inst.so as /usr/local/samba/lib/ldb/extended_dn_store.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-show-deleted.inst.so as /usr/local/samba/lib/ldb/show_deleted.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-partition.inst.so as /usr/local/samba/lib/ldb/partition.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-new-partition.inst.so as /usr/local/samba/lib/ldb/new_partition.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-update-keytab.inst.so as /usr/local/samba/lib/ldb/update_keytab.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-secrets-tdb-sync.inst.so as /usr/local/samba/lib/ldb/secrets_tdb_sync.so
* installing bin/default/source3/libsecrets3.inst.so as /usr/local/samba/lib/private/libsecrets3.so
* installing bin/default/source3/libsmbconf.inst.so as /usr/local/samba/lib/libsmbconf.so.0
* installing bin/default/source3/libsmbregistry.inst.so as /usr/local/samba/lib/private/libsmbregistry.so
* installing bin/default/libcli/registry/libutil_reg.inst.so as /usr/local/samba/lib/private/libutil_reg.so
* installing bin/default/source3/libsmbd_shim.inst.so as /usr/local/samba/lib/private/libsmbd_shim.so
* installing bin/default/source3/libsamba3-util.inst.so as /usr/local/samba/lib/private/libsamba3-util.so
* installing bin/default/source3/libCHARSET3.inst.so as /usr/local/samba/lib/private/libCHARSET3.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-objectclass.inst.so as /usr/local/samba/lib/ldb/objectclass.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-objectclass-attrs.inst.so as /usr/local/samba/lib/ldb/objectclass_attrs.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-subtree-rename.inst.so as /usr/local/samba/lib/ldb/subtree_rename.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-subtree-delete.inst.so as /usr/local/samba/lib/ldb/subtree_delete.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-linked-attributes.inst.so as /usr/local/samba/lib/ldb/linked_attributes.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-ranged-results.inst.so as /usr/local/samba/lib/ldb/ranged_results.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-anr.inst.so as /usr/local/samba/lib/ldb/anr.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-instancetype.inst.so as /usr/local/samba/lib/ldb/instancetype.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-operational.inst.so as /usr/local/samba/lib/ldb/operational.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-descriptor.inst.so as /usr/local/samba/lib/ldb/descriptor.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-resolve-oids.inst.so as /usr/local/samba/lib/ldb/resolve_oids.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-acl.inst.so as /usr/local/samba/lib/ldb/acl.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-lazy-commit.inst.so as /usr/local/samba/lib/ldb/lazy_commit.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-aclread.inst.so as /usr/local/samba/lib/ldb/aclread.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-simple-dn.inst.so as /usr/local/samba/lib/ldb/simple_dn.so
* installing bin/default/source4/dsdb/samdb/ldb_modules/libldb-dirsync.inst.so as /usr/local/samba/lib/ldb/dirsync.so
* installing bin/default/source4/dsdb/libservice-drepl.inst.so as /usr/local/samba/lib/service/drepl.so
* installing bin/default/source4/smbd/libservice.inst.so as /usr/local/samba/lib/private/libservice.so
* installing bin/default/source4/auth/ntlm/libauth4.inst.so as /usr/local/samba/lib/private/libauth4.so
* installing bin/default/nsswitch/libwbclient/libwbclient.inst.so as /usr/local/samba/lib/libwbclient.so.0.11
* installing bin/default/nsswitch/libwinbind-client.inst.so as /usr/local/samba/lib/private/libwinbind-client.so
* installing bin/default/source4/auth/libauth_unix_token.inst.so as /usr/local/samba/lib/private/libauth_unix_token.so
* installing bin/default/source4/libcli/wbclient/libLIBWBCLIENT_OLD.inst.so as /usr/local/samba/lib/private/libLIBWBCLIENT_OLD.so
* installing bin/default/libcli/named_pipe_auth/libnpa_tstream.inst.so as /usr/local/samba/lib/private/libnpa_tstream.so
* installing bin/default/source4/smbd/libprocess_model.inst.so as /usr/local/samba/lib/private/libprocess_model.so
* installing bin/default/source4/dsdb/libservice-kcc.inst.so as /usr/local/samba/lib/service/kcc.so
* installing bin/default/source4/dsdb/libservice-dns-update.inst.so as /usr/local/samba/lib/service/dns_update.so
* installing bin/default/source4/dsdb/python-dsdb.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dsdb.so
* installing bin/default/source4/smbd/libprocess-model-standard.inst.so as /usr/local/samba/lib/process_model/standard.so
* installing bin/default/source4/smbd/libprocess-model-prefork.inst.so as /usr/local/samba/lib/process_model/prefork.so
* installing bin/default/source4/smbd/libprocess-model-onefork.inst.so as /usr/local/samba/lib/process_model/onefork.so
* installing bin/default/source4/libnet/libsamba-net.inst.so as /usr/local/samba/lib/private/libsamba-net.so
* installing bin/default/source4/libnet/python-net.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/net.so
* installing bin/default/source4/libnet/python-dckeytab.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/dckeytab.so
* installing bin/default/source4/kdc/libHDB_SAMBA4.inst.so as /usr/local/samba/lib/private/libHDB_SAMBA4.so
* installing bin/default/source4/kdc/libdb-glue.inst.so as /usr/local/samba/lib/private/libdb-glue.so
* installing bin/default/source4/heimdal_build/libhdb-samba4.inst.so as /usr/local/samba/lib/private/libhdb-samba4.so.11.0.2
* symlink /usr/local/samba/lib/private/libhdb-samba4.so.11 (-> libhdb-samba4.so.11.0.2)
* installing bin/default/source4/auth/gensec/libgensec-krb5.inst.so as /usr/local/samba/lib/gensec/krb5.so
* installing bin/default/source4/auth/gensec/pygensec.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/gensec.so
* installing bin/default/source4/auth/pyauth.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/auth.so
* installing bin/default/auth/credentials/pycredentials.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/credentials.so
* installing bin/default/source4/lib/cmdline/libcmdline-credentials.inst.so as /usr/local/samba/lib/private/libcmdline-credentials.so
* installing bin/default/nsswitch/libnss-winbind.inst.so as /usr/local/samba/lib/libnss_winbind.so.2
* installing bin/default/nsswitch/libpamwinbind.inst.so as /usr/local/samba/lib/security/pam_winbind.so
* installing bin/default/lib/iniparser/src/libiniparser.inst.so as /usr/local/samba/lib/private/libiniparser.so
* installing bin/default/nsswitch/libwinbind-krb5-locator.inst.so as /usr/local/samba/lib/winbind_krb5_locator.so
* installing bin/default/lib/ldb-samba/python-samba--ldb.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/_ldb.so
* installing bin/default/lib/ldb-samba/libldbsamba-extensions.inst.so as /usr/local/samba/lib/ldb/ldbsamba_extensions.so
* installing bin/default/lib/ldb-samba/libldb-ildap.inst.so as /usr/local/samba/lib/ldb/ildap.so
* installing bin/default/source4/lib/registry/libregistry.inst.so as /usr/local/samba/lib/libregistry.so.0.0.1
* installing bin/default/source4/lib/registry/py-registry.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/registry.so
* installing bin/default/source4/lib/messaging/python-messaging.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/messaging.so
* installing bin/default/lib/torture/libtorture.inst.so as /usr/local/samba/lib/libtorture.so.0.0.1
* installing bin/default/lib/subunit/c/libsubunit.inst.so as /usr/local/samba/lib/private/libsubunit.so
* installing bin/default/source4/lib/com/pycom.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/com.so
* installing bin/default/source4/dns_server/libservice-dns.inst.so as /usr/local/samba/lib/service/dns.so
* installing bin/default/source3/auth/libauth.inst.so as /usr/local/samba/lib/private/libauth.so
* installing bin/default/source3/liblibcli_lsa3.inst.so as /usr/local/samba/lib/private/liblibcli_lsa3.so
* installing bin/default/source3/liblibcli_netlogon3.inst.so as /usr/local/samba/lib/private/liblibcli_netlogon3.so
* installing bin/default/source3/libtrusts_util.inst.so as /usr/local/samba/lib/private/libtrusts_util.so
* installing bin/default/source3/libmsrpc3.inst.so as /usr/local/samba/lib/private/libmsrpc3.so
* installing bin/default/source3/liblibsmb.inst.so as /usr/local/samba/lib/private/liblibsmb.so
* installing bin/default/source3/libgse.inst.so as /usr/local/samba/lib/private/libgse.so
* installing bin/default/source3/libutil_cmdline.inst.so as /usr/local/samba/lib/private/libutil_cmdline.so
* installing bin/default/source3/libpdb.inst.so as /usr/local/samba/lib/libpdb.so.0
* installing bin/default/source3/libsmbldap.inst.so as /usr/local/samba/lib/libsmbldap.so.0
* installing bin/default/source3/libsmbldaphelper.inst.so as /usr/local/samba/lib/private/libsmbldaphelper.so
* installing bin/default/source3/libads.inst.so as /usr/local/samba/lib/private/libads.so
* installing bin/default/source4/dns_server/libdlz-bind9.inst.so as /usr/local/samba/lib/bind9/dlz_bind9.so
* installing bin/default/source4/dns_server/libdlz-bind9-9.inst.so as /usr/local/samba/lib/bind9/dlz_bind9_9.so
* installing bin/default/source4/dns_server/libdlz_bind9_for_torture.inst.so as /usr/local/samba/lib/private/libdlz_bind9_for_torture.so
* installing bin/default/source4/smb_server/libservice-smb.inst.so as /usr/local/samba/lib/service/smb.so
* installing bin/default/dfs_server/libdfs_server_ad.inst.so as /usr/local/samba/lib/private/libdfs_server_ad.so
* installing bin/default/source4/ntvfs/libntvfs.inst.so as /usr/local/samba/lib/private/libntvfs.so
* installing bin/default/source4/ntvfs/posix/libposix_eadb.inst.so as /usr/local/samba/lib/private/libposix_eadb.so
* installing bin/default/source4/rpc_server/libdcerpc-server.inst.so as /usr/local/samba/lib/libdcerpc-server.so.0.0.1
* installing bin/default/source4/rpc_server/libservice-dcerpc.inst.so as /usr/local/samba/lib/service/dcerpc.so
* installing bin/default/source4/ldap_server/libservice-ldap.inst.so as /usr/local/samba/lib/service/ldap.so
* installing bin/default/source4/web_server/libservice-web.inst.so as /usr/local/samba/lib/service/web.so
* installing bin/default/source4/winbind/libservice-winbind.inst.so as /usr/local/samba/lib/service/winbind.so
* installing bin/default/source4/nbt_server/libldb-wins-ldb.inst.so as /usr/local/samba/lib/ldb/wins_ldb.so
* installing bin/default/source4/nbt_server/libservice-nbtd.inst.so as /usr/local/samba/lib/service/nbtd.so
* installing bin/default/source4/wrepl_server/libservice-wrepl.inst.so as /usr/local/samba/lib/service/wrepl.so
* installing bin/default/source4/cldap_server/libservice-cldap.inst.so as /usr/local/samba/lib/service/cldap.so
* installing bin/default/source4/ntp_signd/libservice-ntp-signd.inst.so as /usr/local/samba/lib/service/ntp_signd.so
* installing bin/default/source4/ntvfs/posix/python-xattr-native.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/xattr_native.so
* installing bin/default/source4/ntvfs/posix/python-posix-eadb.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/posix_eadb.so
* installing bin/default/source4/ntvfs/posix/python-xattr-tdb.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/xattr_tdb.so
* installing bin/default/source3/libxattr_tdb.inst.so as /usr/local/samba/lib/private/libxattr_tdb.so
* installing bin/default/source4/libcli/pysmb.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/smb.so
* installing bin/default/libcli/security/pysecurity.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/security.so
* installing bin/default/libcli/nbt/python-netbios.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/netbios.so
* installing bin/default/source4/lib/policy/libsamba-policy.inst.so as /usr/local/samba/lib/libsamba-policy.so.0.0.1
* installing bin/default/source4/lib/policy/py-policy.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/policy.so
* installing bin/default/source4/kdc/libservice-kdc.inst.so as /usr/local/samba/lib/service/kdc.so
* installing bin/default/source4/heimdal_build/libkdc-samba4.inst.so as /usr/local/samba/lib/private/libkdc-samba4.so.2.0.0
* symlink /usr/local/samba/lib/private/libkdc-samba4.so.2 (-> libkdc-samba4.so.2.0.0)
* installing bin/default/source4/heimdal_build/libheimntlm-samba4.inst.so as /usr/local/samba/lib/private/libheimntlm-samba4.so.1.0.1
* symlink /usr/local/samba/lib/private/libheimntlm-samba4.so.1 (-> libheimntlm-samba4.so.1.0.1)
* installing bin/default/source4/kdc/libpac.inst.so as /usr/local/samba/lib/private/libpac.so
* installing bin/default/source4/kdc/libmit-samba.inst.so as /usr/local/samba/lib/mit_samba.so
* installing bin/default/source3/libnetapi.inst.so as /usr/local/samba/lib/libnetapi.so.0
* installing bin/default/source3/libnet_keytab.inst.so as /usr/local/samba/lib/private/libnet_keytab.so
* installing bin/default/source3/libsmbsharemodes.inst.so as /usr/local/samba/lib/libsmbsharemodes.so.0
* installing bin/default/source3/libnss-wins.inst.so as /usr/local/samba/lib/libnss_wins.so.2
* installing bin/default/source3/libgpo.inst.so as /usr/local/samba/lib/private/libgpo.so
* installing bin/default/source3/pys3param.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/samba3/param.so
* installing bin/default/source3/libpopt_samba3.inst.so as /usr/local/samba/lib/private/libpopt_samba3.so
* installing bin/default/source3/libsmbd_conn.inst.so as /usr/local/samba/lib/private/libsmbd_conn.so
* installing bin/default/source3/libsmbd_base.inst.so as /usr/local/samba/lib/private/libsmbd_base.so
* installing bin/default/source3/libprinting_migrate.inst.so as /usr/local/samba/lib/private/libprinting_migrate.so
* installing bin/default/source3/libcli_spoolss.inst.so as /usr/local/samba/lib/private/libcli_spoolss.so
* installing bin/default/source3/pysmbd.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/samba3/smbd.so
* installing bin/default/source3/pylibsmb.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/samba3/libsmb_samba_internal.so
* installing bin/default/source3/libsmb/libsmbclient.inst.so as /usr/local/samba/lib/libsmbclient.so.0.2.0
* installing bin/default/source3/auth/libauth-script.inst.so as /usr/local/samba/lib/auth/script.so
* installing bin/default/source3/modules/libvfs-audit.inst.so as /usr/local/samba/lib/vfs/audit.so
* installing bin/default/source3/modules/libvfs-extd-audit.inst.so as /usr/local/samba/lib/vfs/extd_audit.so
* installing bin/default/source3/modules/libvfs-full-audit.inst.so as /usr/local/samba/lib/vfs/full_audit.so
* installing bin/default/source3/modules/libvfs-fake-perms.inst.so as /usr/local/samba/lib/vfs/fake_perms.so
* installing bin/default/source3/modules/libvfs-recycle.inst.so as /usr/local/samba/lib/vfs/recycle.so
* installing bin/default/source3/modules/libvfs-netatalk.inst.so as /usr/local/samba/lib/vfs/netatalk.so
* installing bin/default/source3/modules/libvfs-default-quota.inst.so as /usr/local/samba/lib/vfs/default_quota.so
* installing bin/default/source3/modules/libvfs-readonly.inst.so as /usr/local/samba/lib/vfs/readonly.so
* installing bin/default/source3/modules/libvfs-cap.inst.so as /usr/local/samba/lib/vfs/cap.so
* installing bin/default/source3/modules/libvfs-expand-msdfs.inst.so as /usr/local/samba/lib/vfs/expand_msdfs.so
* installing bin/default/source3/modules/libvfs-shadow-copy.inst.so as /usr/local/samba/lib/vfs/shadow_copy.so
* installing bin/default/source3/modules/libvfs-shadow-copy2.inst.so as /usr/local/samba/lib/vfs/shadow_copy2.so
* installing bin/default/source3/modules/libvfs-xattr-tdb.inst.so as /usr/local/samba/lib/vfs/xattr_tdb.so
* installing bin/default/source3/modules/libvfs-posix-eadb.inst.so as /usr/local/samba/lib/vfs/posix_eadb.so
* installing bin/default/source3/modules/libvfs-catia.inst.so as /usr/local/samba/lib/vfs/catia.so
* installing bin/default/source3/modules/libvfs-streams-xattr.inst.so as /usr/local/samba/lib/vfs/streams_xattr.so
* installing bin/default/source3/modules/libvfs-streams-depot.inst.so as /usr/local/samba/lib/vfs/streams_depot.so
* installing bin/default/source3/modules/libvfs-commit.inst.so as /usr/local/samba/lib/vfs/commit.so
* installing bin/default/source3/modules/libvfs-readahead.inst.so as /usr/local/samba/lib/vfs/readahead.so
* installing bin/default/source3/modules/libvfs-fileid.inst.so as /usr/local/samba/lib/vfs/fileid.so
* installing bin/default/source3/modules/libvfs-aio-fork.inst.so as /usr/local/samba/lib/vfs/aio_fork.so
* installing bin/default/source3/modules/libvfs-aio-pthread.inst.so as /usr/local/samba/lib/vfs/aio_pthread.so
* installing bin/default/source3/modules/libvfs-aio-posix.inst.so as /usr/local/samba/lib/vfs/aio_posix.so
* installing bin/default/source3/modules/libvfs-aio-linux.inst.so as /usr/local/samba/lib/vfs/aio_linux.so
* installing bin/default/source3/modules/libvfs-preopen.inst.so as /usr/local/samba/lib/vfs/preopen.so
* installing bin/default/source3/modules/libvfs-syncops.inst.so as /usr/local/samba/lib/vfs/syncops.so
* installing bin/default/source3/modules/libvfs-acl-xattr.inst.so as /usr/local/samba/lib/vfs/acl_xattr.so
* installing bin/default/source3/modules/libvfs-acl-tdb.inst.so as /usr/local/samba/lib/vfs/acl_tdb.so
* installing bin/default/source3/modules/libvfs-smb-traffic-analyzer.inst.so as /usr/local/samba/lib/vfs/smb_traffic_analyzer.so
* installing bin/default/source3/modules/libvfs-dirsort.inst.so as /usr/local/samba/lib/vfs/dirsort.so
* installing bin/default/source3/modules/libvfs-scannedonly.inst.so as /usr/local/samba/lib/vfs/scannedonly.so
* installing bin/default/source3/modules/libvfs-crossrename.inst.so as /usr/local/samba/lib/vfs/crossrename.so
* installing bin/default/source3/modules/libvfs-linux-xfs-sgid.inst.so as /usr/local/samba/lib/vfs/linux_xfs_sgid.so
* installing bin/default/source3/modules/libvfs-time-audit.inst.so as /usr/local/samba/lib/vfs/time_audit.so
* installing bin/default/source3/modules/libvfs-media-harmony.inst.so as /usr/local/samba/lib/vfs/media_harmony.so
* installing bin/default/source3/pam_smbpass/libpamsmbpass.inst.so as /usr/local/samba/lib/security/pam_smbpass.so
* installing bin/default/source3/passdb/pypassdb.inst.so as /usr/local/samba/lib/python2.7/site-packages/samba/samba3/passdb.so
* installing bin/default/source3/winbindd/libidmap.inst.so as /usr/local/samba/lib/private/libidmap.so
* installing bin/default/source3/winbindd/libidmap-rid.inst.so as /usr/local/samba/lib/idmap/rid.so
* installing bin/default/source3/winbindd/libidmap-tdb2.inst.so as /usr/local/samba/lib/idmap/tdb2.so
* installing bin/default/source3/winbindd/libidmap-hash.inst.so as /usr/local/samba/lib/idmap/hash.so
* installing bin/default/source3/winbindd/libidmap-autorid.inst.so as /usr/local/samba/lib/idmap/autorid.so
* installing bin/default/source3/winbindd/libnss_info.inst.so as /usr/local/samba/lib/private/libnss_info.so
* installing bin/default/source3/winbindd/libnss-info-hash.inst.so as /usr/local/samba/lib/nss_info/hash.so
* installing bin/default/file_server/libservice-s3fs.inst.so as /usr/local/samba/lib/service/s3fs.so
[3911/4084] Linking default/lib/tdb/tdbtorture.inst
[3912/4084] Linking default/lib/tdb/tdbrestore.inst
[3913/4084] Linking default/lib/tdb/tdbdump.inst
[3914/4084] Linking default/lib/tdb/tdbbackup.inst
[3915/4084] Linking default/lib/tdb/tdbtool.inst
[3916/4084] Linking default/lib/tdb/tdb1-run-3G-file.inst
[3917/4084] Linking default/lib/tdb/tdb1-run-bad-tdb-header.inst
[3918/4084] Linking default/lib/tdb/tdb1-run.inst
[3919/4084] Linking default/lib/tdb/tdb1-run-check.inst
[3920/4084] Linking default/lib/tdb/tdb1-run-corrupt.inst
[3921/4084] Linking default/lib/tdb/tdb1-run-die-during-transaction.inst
[3922/4084] Linking default/lib/tdb/tdb1-run-endian.inst
[3923/4084] Linking default/lib/tdb/tdb1-run-incompatible.inst
[3924/4084] Linking default/lib/tdb/tdb1-run-nested-transactions.inst
[3925/4084] Linking default/lib/tdb/tdb1-run-nested-traverse.inst
[3926/4084] Linking default/lib/tdb/tdb1-run-no-lock-during-traverse.inst
[3927/4084] Linking default/lib/tdb/tdb1-run-oldhash.inst
[3928/4084] Linking default/lib/tdb/tdb1-run-open-during-transaction.inst
[3929/4084] Linking default/lib/tdb/tdb1-run-readonly-check.inst
[3930/4084] Linking default/lib/tdb/tdb1-run-rescue.inst
[3931/4084] Linking default/lib/tdb/tdb1-run-rescue-find_entry.inst
[3932/4084] Linking default/lib/tdb/tdb1-run-rwlock-check.inst
[3933/4084] Linking default/lib/tdb/tdb1-run-summary.inst
[3934/4084] Linking default/lib/tdb/tdb1-run-transaction-expand.inst
[3935/4084] Linking default/lib/tdb/tdb1-run-traverse-in-transaction.inst
[3936/4084] Linking default/lib/tdb/tdb1-run-wronghash-fail.inst
[3937/4084] Linking default/lib/tdb/tdb1-run-zero-append.inst
[3938/4084] Linking default/lib/ldb/ldbadd.inst
[3939/4084] Linking default/lib/ldb/ldbsearch.inst
[3940/4084] Linking default/lib/ldb/ldbdel.inst
[3941/4084] Linking default/lib/ldb/ldbmodify.inst
[3942/4084] Linking default/lib/ldb/ldbedit.inst
[3943/4084] Linking default/lib/ldb/ldbrename.inst
[3944/4084] Linking default/lib/ldb/ldbtest.inst
[3945/4084] Linking default/lib/ldb/ldbdump.inst
[3946/4084] Linking default/librpc/tools/ndrdump.inst
[3947/4084] Linking default/source4/smbd/samba.inst
[3948/4084] Linking default/nsswitch/nsstest.inst
[3949/4084] Linking default/nsswitch/wbinfo.inst
[3950/4084] Linking default/source4/lib/registry/regdiff.inst
[3951/4084] Linking default/source4/lib/registry/regpatch.inst
[3952/4084] Linking default/source4/lib/registry/regshell.inst
[3953/4084] Linking default/source4/lib/registry/regtree.inst
[3954/4084] Linking default/source4/utils/ntlm_auth4.inst
[3955/4084] Linking default/source4/utils/oLschema2ldif.inst
[3956/4084] Linking default/source4/torture/smbtorture.inst
[3957/4084] Linking default/source4/torture/gentest.inst
[3958/4084] Linking default/source4/torture/masktest.inst
[3959/4084] Linking default/source4/torture/locktest.inst
[3960/4084] Linking default/source4/client/smbclient4.inst
[3961/4084] Linking default/source4/client/cifsdd.inst
[3962/4084] Linking default/libcli/nbt/nmblookup4.inst
[3963/4084] Linking default/source4/heimdal_build/rkpty.inst
[3964/4084] Linking default/source4/heimdal_build/samba4kinit.inst
[3965/4084] Linking default/source4/heimdal_build/samba4kgetcred.inst
[3966/4084] Linking default/source4/heimdal_build/samba4kpasswd.inst
[3967/4084] Linking default/source3/smbd/smbd.inst
[3968/4084] Linking default/source3/nmbd/nmbd.inst
[3969/4084] Linking default/source3/winbindd/winbindd.inst
[3970/4084] Linking default/source3/web/swat.inst
[3971/4084] Linking default/source3/rpcclient/rpcclient.inst
[3972/4084] Linking default/source3/client/smbclient.inst
[3973/4084] Linking default/source3/net.inst
[3974/4084] Linking default/source3/profiles.inst
[3975/4084] Linking default/source3/smbspool.inst
[3976/4084] Linking default/source3/testparm.inst
[3977/4084] Linking default/source3/smbta-util.inst
[3978/4084] Linking default/source3/smbstatus.inst
[3979/4084] Linking default/source3/smbcontrol.inst
[3980/4084] Linking default/source3/smbtree.inst
[3981/4084] Linking default/source3/smbpasswd.inst
[3982/4084] Linking default/source3/pdbedit.inst
[3983/4084] Linking default/source3/smbget.inst
[3984/4084] Linking default/source3/nmblookup.inst
[3985/4084] Linking default/source3/smbtorture3.inst
[3986/4084] Linking default/source3/smbconftort.inst
[3987/4084] Linking default/source3/replacetort.inst
[3988/4084] Linking default/source3/msgtest.inst
[3989/4084] Linking default/source3/smbcacls.inst
[3990/4084] Linking default/source3/smbcquotas.inst
[3991/4084] Linking default/source3/eventlogadm.inst
[3992/4084] Linking default/source3/sharesec.inst
[3993/4084] Linking default/source3/pdbtest.inst
[3994/4084] Linking default/source3/vfstest.inst
[3995/4084] Linking default/source3/log2pcap.inst
[3996/4084] Linking default/source3/locktest2.inst
[3997/4084] Linking default/source3/debug2html.inst
[3998/4084] Linking default/source3/smbfilter.inst
[3999/4084] Linking default/source3/versiontest.inst
[4000/4084] Linking default/source3/ntlm_auth.inst
[4001/4084] Linking default/source3/timelimit.inst
[4002/4084] Linking default/source3/rpc_open_tcp.inst
[4003/4084] Linking default/source3/test_lp_load.inst
[4004/4084] Linking default/source3/dbwrap_tool.inst
[4005/4084] Linking default/source3/dbwrap_torture.inst
[4006/4084] Linking default/source3/split_tokens.inst
[4007/4084] Linking default/source3/vlp.inst
[4008/4084] Linking default/source3/lib/pthreadpool/pthreadpooltest.inst
[4009/4084] Linking default/source3/lib/asys/asystest.inst
[4010/4084] Linking default/examples/libsmbclient/testsmbc.inst
[4011/4084] Linking default/examples/libsmbclient/testacl.inst
[4012/4084] Linking default/examples/libsmbclient/testacl2.inst
[4013/4084] Linking default/examples/libsmbclient/testacl3.inst
[4014/4084] Linking default/examples/libsmbclient/testbrowse.inst
[4015/4084] Linking default/examples/libsmbclient/testbrowse2.inst
[4016/4084] Linking default/examples/libsmbclient/teststat.inst
[4017/4084] Linking default/examples/libsmbclient/teststat2.inst
[4018/4084] Linking default/examples/libsmbclient/teststat3.inst
[4019/4084] Linking default/examples/libsmbclient/teststatvfs.inst
[4020/4084] Linking default/examples/libsmbclient/testfstatvfs.inst
[4021/4084] Linking default/examples/libsmbclient/testtruncate.inst
[4022/4084] Linking default/examples/libsmbclient/testchmod.inst
[4023/4084] Linking default/examples/libsmbclient/testutime.inst
[4024/4084] Linking default/examples/libsmbclient/testread.inst
[4025/4084] Linking default/examples/libsmbclient/testwrite.inst
[4026/4084] Linking default/examples/libsmbclient/testctx.inst
[4027/4084] Linking default/source3/lib/netapi/tests/netapitest.inst
[4028/4084] Linking default/source3/lib/netapi/examples/getdc/getdc.inst
[4029/4084] Linking default/source3/lib/netapi/examples/dsgetdc/dsgetdc.inst
[4030/4084] Linking default/source3/lib/netapi/examples/join/netdomjoin.inst
[4031/4084] Linking default/source3/lib/netapi/examples/join/getjoinableous.inst
[4032/4084] Linking default/source3/lib/netapi/examples/join/getjoininformation.inst
[4033/4084] Linking default/source3/lib/netapi/examples/join/rename_machine.inst
[4034/4084] Linking default/source3/lib/netapi/examples/user/user_add.inst
[4035/4084] Linking default/source3/lib/netapi/examples/user/user_del.inst
[4036/4084] Linking default/source3/lib/netapi/examples/user/user_enum.inst
[4037/4084] Linking default/source3/lib/netapi/examples/user/user_dispinfo.inst
[4038/4084] Linking default/source3/lib/netapi/examples/user/user_chgpwd.inst
[4039/4084] Linking default/source3/lib/netapi/examples/user/user_getinfo.inst
[4040/4084] Linking default/source3/lib/netapi/examples/user/user_setinfo.inst
[4041/4084] Linking default/source3/lib/netapi/examples/user/user_modalsget.inst
[4042/4084] Linking default/source3/lib/netapi/examples/user/user_modalsset.inst
[4043/4084] Linking default/source3/lib/netapi/examples/user/user_getgroups.inst
[4044/4084] Linking default/source3/lib/netapi/examples/user/user_setgroups.inst
[4045/4084] Linking default/source3/lib/netapi/examples/user/user_getlocalgroups.inst
[4046/4084] Linking default/source3/lib/netapi/examples/group/group_add.inst
[4047/4084] Linking default/source3/lib/netapi/examples/group/group_del.inst
[4048/4084] Linking default/source3/lib/netapi/examples/group/group_enum.inst
[4049/4084] Linking default/source3/lib/netapi/examples/group/group_setinfo.inst
[4050/4084] Linking default/source3/lib/netapi/examples/group/group_getinfo.inst
[4051/4084] Linking default/source3/lib/netapi/examples/group/group_adduser.inst
[4052/4084] Linking default/source3/lib/netapi/examples/group/group_deluser.inst
[4053/4084] Linking default/source3/lib/netapi/examples/group/group_getusers.inst
[4054/4084] Linking default/source3/lib/netapi/examples/group/group_setusers.inst
[4055/4084] Linking default/source3/lib/netapi/examples/localgroup/localgroup_add.inst
[4056/4084] Linking default/source3/lib/netapi/examples/localgroup/localgroup_del.inst
[4057/4084] Linking default/source3/lib/netapi/examples/localgroup/localgroup_getinfo.inst
[4058/4084] Linking default/source3/lib/netapi/examples/localgroup/localgroup_setinfo.inst
[4059/4084] Linking default/source3/lib/netapi/examples/localgroup/localgroup_enum.inst
[4060/4084] Linking default/source3/lib/netapi/examples/localgroup/localgroup_addmembers.inst
[4061/4084] Linking default/source3/lib/netapi/examples/localgroup/localgroup_delmembers.inst
[4062/4084] Linking default/source3/lib/netapi/examples/localgroup/localgroup_setmembers.inst
[4063/4084] Linking default/source3/lib/netapi/examples/localgroup/localgroup_getmembers.inst
[4064/4084] Linking default/source3/lib/netapi/examples/server/remote_tod.inst
[4065/4084] Linking default/source3/lib/netapi/examples/server/server_getinfo.inst
[4066/4084] Linking default/source3/lib/netapi/examples/share/share_add.inst
[4067/4084] Linking default/source3/lib/netapi/examples/share/share_del.inst
[4068/4084] Linking default/source3/lib/netapi/examples/share/share_enum.inst
[4069/4084] Linking default/source3/lib/netapi/examples/share/share_getinfo.inst
[4070/4084] Linking default/source3/lib/netapi/examples/share/share_setinfo.inst
[4071/4084] Linking default/source3/lib/netapi/examples/file/file_close.inst
[4072/4084] Linking default/source3/lib/netapi/examples/file/file_getinfo.inst
[4073/4084] Linking default/source3/lib/netapi/examples/file/file_enum.inst
[4074/4084] Linking default/source3/lib/netapi/examples/shutdown/shutdown_init.inst
[4075/4084] Linking default/source3/lib/netapi/examples/shutdown/shutdown_abort.inst
[4076/4084] Linking default/source3/lib/netapi/examples/netlogon/netlogon_control.inst
[4077/4084] Linking default/source3/lib/netapi/examples/netlogon/netlogon_control2.inst
[4078/4084] Linking default/source3/lib/netapi/examples/netlogon/nltest.inst
* installing bin/default/lib/tdb/tdbrestore.inst as /usr/local/samba/bin/tdbrestore
* installing bin/default/lib/tdb/tdbdump.inst as /usr/local/samba/bin/tdbdump
* installing bin/default/lib/tdb/tdbbackup.inst as /usr/local/samba/bin/tdbbackup
* installing bin/default/lib/tdb/tdbtool.inst as /usr/local/samba/bin/tdbtool
* installing bin/default/lib/ldb/ldbadd.inst as /usr/local/samba/bin/ldbadd
* installing bin/default/lib/ldb/ldbsearch.inst as /usr/local/samba/bin/ldbsearch
* installing bin/default/lib/ldb/ldbdel.inst as /usr/local/samba/bin/ldbdel
* installing bin/default/lib/ldb/ldbmodify.inst as /usr/local/samba/bin/ldbmodify
* installing bin/default/lib/ldb/ldbedit.inst as /usr/local/samba/bin/ldbedit
* installing bin/default/lib/ldb/ldbrename.inst as /usr/local/samba/bin/ldbrename
* installing bin/default/librpc/tools/ndrdump.inst as /usr/local/samba/bin/ndrdump
* installing bin/default/source4/smbd/samba.inst as /usr/local/samba/sbin/samba
* installing bin/default/nsswitch/wbinfo.inst as /usr/local/samba/bin/wbinfo
* installing bin/default/source4/lib/registry/regdiff.inst as /usr/local/samba/bin/regdiff
* installing bin/default/source4/lib/registry/regpatch.inst as /usr/local/samba/bin/regpatch
* installing bin/default/source4/lib/registry/regshell.inst as /usr/local/samba/bin/regshell
* installing bin/default/source4/lib/registry/regtree.inst as /usr/local/samba/bin/regtree
* installing bin/default/source4/utils/oLschema2ldif.inst as /usr/local/samba/bin/oLschema2ldif
* installing bin/default/source4/torture/smbtorture.inst as /usr/local/samba/bin/smbtorture
* installing bin/default/source4/torture/gentest.inst as /usr/local/samba/bin/gentest
* installing bin/default/source4/torture/masktest.inst as /usr/local/samba/bin/masktest
* installing bin/default/source4/torture/locktest.inst as /usr/local/samba/bin/locktest
* installing bin/default/source4/client/smbclient4.inst as /usr/local/samba/bin/smbclient4
* installing bin/default/source4/client/cifsdd.inst as /usr/local/samba/bin/cifsdd
* installing bin/default/libcli/nbt/nmblookup4.inst as /usr/local/samba/bin/nmblookup4
* installing bin/default/source3/smbd/smbd.inst as /usr/local/samba/sbin/smbd
* installing bin/default/source3/nmbd/nmbd.inst as /usr/local/samba/sbin/nmbd
* installing bin/default/source3/winbindd/winbindd.inst as /usr/local/samba/sbin/winbindd
* installing bin/default/source3/web/swat.inst as /usr/local/samba/sbin/swat
* installing bin/default/source3/rpcclient/rpcclient.inst as /usr/local/samba/bin/rpcclient
* installing bin/default/source3/client/smbclient.inst as /usr/local/samba/bin/smbclient
* installing bin/default/source3/net.inst as /usr/local/samba/bin/net
* installing bin/default/source3/profiles.inst as /usr/local/samba/bin/profiles
* installing bin/default/source3/smbspool.inst as /usr/local/samba/bin/smbspool
* installing bin/default/source3/testparm.inst as /usr/local/samba/bin/testparm
* installing bin/default/source3/smbta-util.inst as /usr/local/samba/bin/smbta-util
* installing bin/default/source3/smbstatus.inst as /usr/local/samba/bin/smbstatus
* installing bin/default/source3/smbcontrol.inst as /usr/local/samba/bin/smbcontrol
* installing bin/default/source3/smbtree.inst as /usr/local/samba/bin/smbtree
* installing bin/default/source3/smbpasswd.inst as /usr/local/samba/bin/smbpasswd
* installing bin/default/source3/pdbedit.inst as /usr/local/samba/bin/pdbedit
* installing bin/default/source3/smbget.inst as /usr/local/samba/bin/smbget
* installing bin/default/source3/nmblookup.inst as /usr/local/samba/bin/nmblookup
* installing bin/default/source3/smbcacls.inst as /usr/local/samba/bin/smbcacls
* installing bin/default/source3/smbcquotas.inst as /usr/local/samba/bin/smbcquotas
* installing bin/default/source3/eventlogadm.inst as /usr/local/samba/bin/eventlogadm
* installing bin/default/source3/sharesec.inst as /usr/local/samba/bin/sharesec
* installing bin/default/source3/ntlm_auth.inst as /usr/local/samba/bin/ntlm_auth
* installing bin/default/source3/dbwrap_tool.inst as /usr/local/samba/bin/dbwrap_tool
* installing bin/default/pidl/pidl.1p as /usr/local/samba/share/man/man1/pidl.1p
* installing bin/default/pidl/Parse::Pidl::Dump.3pm as /usr/local/samba/share/man/man3/Parse::Pidl::Dump.3pm
* installing bin/default/pidl/Parse::Pidl::Wireshark::Conformance.3pm as /usr/local/samba/share/man/man3/Parse::Pidl::Wireshark::Conformance.3pm
* installing bin/default/pidl/Parse::Pidl::Util.3pm as /usr/local/samba/share/man/man3/Parse::Pidl::Util.3pm
* installing bin/default/pidl/Parse::Pidl::NDR.3pm as /usr/local/samba/share/man/man3/Parse::Pidl::NDR.3pm
* installing bin/default/pidl/Parse::Pidl::Wireshark::NDR.3pm as /usr/local/samba/share/man/man3/Parse::Pidl::Wireshark::NDR.3pm
Waf: Leaving directory `/root/samba-4.0.9/bin'
'install' finished successfully (7m58.217s)
```

---

### Post by TheHammer101 on 2013-10-16
So, pretty much these forums f*cking suck. Ubuntu has been nothing more than a complete pain in my ass on more than one front. I'm done with this junk software. I'm going to just move to some form of Linux that can actually properly document the changes they make. What a load of trash.

---

### Post by clayb226 on 2013-11-08
You did not mention how you were trying to start samba. It looked to me like all went as planned, and installed. You installed it in /usr/local/samba, so you would have to run the start up script from where it installed it, which will not be in your environmental path, unless you put it there, so you would have to use the full path. If you would of added the --prefix variable during the configuration process, you could of modified where it was installed. Sorry you had a bad experience, I have been using LTS server since 6.10 or so, and think they work good. Hope you like your new distro.

---

