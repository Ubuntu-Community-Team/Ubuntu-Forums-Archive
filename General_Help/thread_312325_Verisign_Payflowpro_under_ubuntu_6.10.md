---
title: "Verisign Payflowpro under ubuntu 6.10"
date: 2006-12-04
forum: General Help
---

### Post by analog on 2006-12-04
Folks,

I'm hoping someone can help in anyway.

I need to install the Verisign Payflowpro API on my ubuntu 6.10 and I'm not having any luck at all.

Below is what happens when I do the "Make" - Any ideas?

TIA - Chris

```

root@localhost:/home/analog/paypal_blp/payflowpro/linuxrh9/perl# make
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"0.03\" -DXS_VERSION=\"0.03\" -fPIC "-I/usr/lib/perl/5.8/CORE"   PFProAPI.c
In file included from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/perl.h:420:24: error: sys/types.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:451:19: error: ctype.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:463:23: error: locale.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:480:20: error: setjmp.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:486:26: error: sys/param.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:491:23: error: stdlib.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:496:23: error: unistd.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:776:23: error: string.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:925:27: error: netinet/in.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:929:26: error: arpa/inet.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:939:25: error: sys/stat.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:961:21: error: time.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:968:25: error: sys/time.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:975:27: error: sys/times.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:982:19: error: errno.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:997:25: error: sys/socket.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:1024:21: error: netdb.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:1127:24: error: sys/ioctl.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:1156:23: error: dirent.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from /usr/lib/perl/5.8/CORE/perl.h:1510,
                 from PFProAPI.xs:10:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perl.h:2120,
                 from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/handy.h:136:25: error: inttypes.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perl.h:2284,
                 from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/unixish.h:106:21: error: signal.h: No such file or directory
In file included from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/perl.h:2421:33: error: pthread.h: No such file or directory
In file included from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/perl.h:2423: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘perl_os_thread’
/usr/lib/perl/5.8/CORE/perl.h:2424: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘perl_mutex’
/usr/lib/perl/5.8/CORE/perl.h:2425: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘perl_cond’
/usr/lib/perl/5.8/CORE/perl.h:2426: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘perl_key’
In file included from /usr/lib/perl/5.8/CORE/iperlsys.h:51,
                 from /usr/lib/perl/5.8/CORE/perl.h:2733,
                 from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/perlio.h:65:19: error: stdio.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/iperlsys.h:51,
                 from /usr/lib/perl/5.8/CORE/perl.h:2733,
                 from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/perlio.h:259: error: expected ‘)’ before ‘*’ token
/usr/lib/perl/5.8/CORE/perlio.h:262: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/lib/perl/5.8/CORE/perlio.h:265: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/lib/perl/5.8/CORE/perlio.h:268: error: expected declaration specifiers or ‘...’ before ‘FILE’
In file included from /usr/lib/perl/5.8/CORE/perl.h:2747,
                 from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/sv.h:389: error: expected specifier-qualifier-list before ‘DIR’
In file included from /usr/lib/perl/5.8/CORE/op.h:497,
                 from /usr/lib/perl/5.8/CORE/perl.h:2754,
                 from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/reentr.h:72:20: error: pwd.h: No such file or directory
/usr/lib/perl/5.8/CORE/reentr.h:75:20: error: grp.h: No such file or directory
/usr/lib/perl/5.8/CORE/reentr.h:85:26: error: crypt.h: No such file or directory
/usr/lib/perl/5.8/CORE/reentr.h:90:27: error: shadow.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/op.h:497,
                 from /usr/lib/perl/5.8/CORE/perl.h:2754,
                 from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/reentr.h:612: error: field ‘_crypt_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:620: error: field ‘_drand48_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:624: error: field ‘_grent_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:635: error: field ‘_hostent_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:654: error: field ‘_netent_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:669: error: field ‘_protoent_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:684: error: field ‘_pwent_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:695: error: field ‘_servent_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:710: error: field ‘_spent_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:721: error: field ‘_gmtime_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:724: error: field ‘_localtime_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:771: error: field ‘_random_struct’ has incomplete type
/usr/lib/perl/5.8/CORE/reentr.h:772: error: expected specifier-qualifier-list before ‘int32_t’
In file included from /usr/lib/perl/5.8/CORE/perl.h:2756,
                 from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/av.h:13: error: expected specifier-qualifier-list before ‘ssize_t’
In file included from /usr/lib/perl/5.8/CORE/perl.h:2759,
                 from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/scope.h:232: error: expected specifier-qualifier-list before ‘sigjmp_buf’
In file included from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/perl.h:2931: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘getuid’
/usr/lib/perl/5.8/CORE/perl.h:2932: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘geteuid’
/usr/lib/perl/5.8/CORE/perl.h:2933: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘getgid’
/usr/lib/perl/5.8/CORE/perl.h:2934: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘getegid’
In file included from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/perl.h:3238:22: error: math.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perl.h:3881,
                 from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/thrdvar.h:85: error: field ‘Tstatbuf’ has incomplete type
/usr/lib/perl/5.8/CORE/thrdvar.h:86: error: field ‘Tstatcache’ has incomplete type
/usr/lib/perl/5.8/CORE/thrdvar.h:91: error: field ‘Ttimesbuf’ has incomplete type
In file included from /usr/lib/perl/5.8/CORE/perl.h:3883,
                 from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/intrpvar.h:66: error: expected specifier-qualifier-list before ‘time_t’
In file included from /usr/lib/perl/5.8/CORE/perl.h:3950,
                 from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/proto.h:128: error: expected declaration specifiers or ‘...’ before ‘mode_t’
/usr/lib/perl/5.8/CORE/proto.h:128: error: expected declaration specifiers or ‘...’ before ‘uid_t’
/usr/lib/perl/5.8/CORE/proto.h:297: error: expected declaration specifiers or ‘...’ before ‘off64_t’
/usr/lib/perl/5.8/CORE/proto.h:299: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Perl_do_sysseek’
/usr/lib/perl/5.8/CORE/proto.h:300: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Perl_do_tell’
/usr/lib/perl/5.8/CORE/proto.h:411: error: expected declaration specifiers or ‘...’ before ‘gid_t’
/usr/lib/perl/5.8/CORE/proto.h:411: error: expected declaration specifiers or ‘...’ before ‘uid_t’
/usr/lib/perl/5.8/CORE/proto.h:736: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Perl_my_fork’
/usr/lib/perl/5.8/CORE/proto.h:1020: error: expected declaration specifiers or ‘...’ before ‘pid_t’
/usr/lib/perl/5.8/CORE/proto.h:1300: error: expected declaration specifiers or ‘...’ before ‘pid_t’
/usr/lib/perl/5.8/CORE/proto.h:1456: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/lib/perl/5.8/CORE/proto.h:2001: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Perl_PerlIO_read’
/usr/lib/perl/5.8/CORE/proto.h:2002: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Perl_PerlIO_write’
/usr/lib/perl/5.8/CORE/proto.h:2003: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Perl_PerlIO_unread’
/usr/lib/perl/5.8/CORE/proto.h:2004: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘Perl_PerlIO_tell’
/usr/lib/perl/5.8/CORE/proto.h:2005: error: expected declaration specifiers or ‘...’ before ‘off64_t’
In file included from /usr/lib/perl/5.8/CORE/perl.h:3988,
                 from PFProAPI.xs:10:
/usr/lib/perl/5.8/CORE/perlvars.h:31: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PL_thr_key’
/usr/lib/perl/5.8/CORE/perlvars.h:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PL_op_mutex’
/usr/lib/perl/5.8/CORE/perlvars.h:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PL_dollarzero_mutex’
/usr/lib/perl/5.8/CORE/perl.h:4485:24: error: sys/ipc.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:4486:24: error: sys/sem.h: No such file or directory
/usr/lib/perl/5.8/CORE/perl.h:4611:24: error: sys/file.h: No such file or directory
In file included from /usr/lib/perl/5.8/CORE/perlapi.h:38,
                 from /usr/lib/perl/5.8/CORE/XSUB.h:349,
                 from PFProAPI.xs:11:
/usr/lib/perl/5.8/CORE/intrpvar.h:66: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/lib/perl/5.8/CORE/intrpvar.h:237: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/lib/perl/5.8/CORE/intrpvar.h:238: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/lib/perl/5.8/CORE/intrpvar.h:239: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/lib/perl/5.8/CORE/intrpvar.h:240: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from /usr/lib/perl/5.8/CORE/perlapi.h:39,
                 from /usr/lib/perl/5.8/CORE/XSUB.h:349,
                 from PFProAPI.xs:11:
/usr/lib/perl/5.8/CORE/perlvars.h:31: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/lib/perl/5.8/CORE/perlvars.h:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/lib/perl/5.8/CORE/perlvars.h:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
PFProAPI.xs:19: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pthread_self’
PFProAPI.xs:20: error: expected ‘)’ before ‘*’ token
PFProAPI.xs:21: error: expected ‘)’ before ‘*’ token
PFProAPI.xs:22: error: expected ‘)’ before ‘*’ token
PFProAPI.xs:24: error: expected ‘)’ before ‘*’ token
PFProAPI.c: In function ‘XS_PFProAPI_pfproInit’:
PFProAPI.c:48: error: invalid type argument of ‘unary *’
PFProAPI.c:48: error: invalid type argument of ‘unary *’
PFProAPI.c:48: error: invalid type argument of ‘unary *’
PFProAPI.c:50: error: invalid type argument of ‘unary *’
PFProAPI.c:53: error: invalid type argument of ‘unary *’
PFProAPI.c:53: error: invalid type argument of ‘unary *’
PFProAPI.c:53: error: invalid type argument of ‘unary *’
PFProAPI.c:53: error: invalid type argument of ‘unary *’
PFProAPI.c:56: error: invalid type argument of ‘unary *’
PFProAPI.c:56: error: invalid type argument of ‘unary *’
PFProAPI.c:56: error: invalid type argument of ‘unary *’
PFProAPI.c:58: error: invalid type argument of ‘unary *’
PFProAPI.c:58: error: invalid type argument of ‘unary *’
PFProAPI.c: In function ‘XS_PFProAPI_pfproCleanup’:
PFProAPI.c:65: error: invalid type argument of ‘unary *’
PFProAPI.c:65: error: invalid type argument of ‘unary *’
PFProAPI.c:65: error: invalid type argument of ‘unary *’
PFProAPI.c:67: error: invalid type argument of ‘unary *’
PFProAPI.c:72: error: invalid type argument of ‘unary *’
PFProAPI.c:72: error: invalid type argument of ‘unary *’
PFProAPI.c: In function ‘XS_PFProAPI_pfproCreateContext’:
PFProAPI.c:79: error: invalid type argument of ‘unary *’
PFProAPI.c:79: error: invalid type argument of ‘unary *’
PFProAPI.c:79: error: invalid type argument of ‘unary *’
PFProAPI.c:81: error: invalid type argument of ‘unary *’
PFProAPI.c:83: error: invalid type argument of ‘unary *’
PFProAPI.c:83: error: invalid type argument of ‘unary *’
PFProAPI.c:83: error: invalid type argument of ‘unary *’
PFProAPI.c:83: error: invalid type argument of ‘unary *’
PFProAPI.c:84: error: invalid type argument of ‘unary *’
PFProAPI.c:84: error: invalid type argument of ‘unary *’
PFProAPI.c:84: error: invalid type argument of ‘unary *’
PFProAPI.c:84: error: invalid type argument of ‘unary *’
PFProAPI.c:85: error: invalid type argument of ‘unary *’
PFProAPI.c:85: error: invalid type argument of ‘unary *’
PFProAPI.c:85: error: invalid type argument of ‘unary *’
PFProAPI.c:85: error: invalid type argument of ‘unary *’
PFProAPI.c:86: error: invalid type argument of ‘unary *’
PFProAPI.c:86: error: invalid type argument of ‘unary *’
PFProAPI.c:86: error: invalid type argument of ‘unary *’
PFProAPI.c:86: error: invalid type argument of ‘unary *’
PFProAPI.c:87: error: invalid type argument of ‘unary *’
PFProAPI.c:87: error: invalid type argument of ‘unary *’
PFProAPI.c:87: error: invalid type argument of ‘unary *’
PFProAPI.c:87: error: invalid type argument of ‘unary *’
PFProAPI.c:88: error: invalid type argument of ‘unary *’
PFProAPI.c:88: error: invalid type argument of ‘unary *’
PFProAPI.c:88: error: invalid type argument of ‘unary *’
PFProAPI.c:88: error: invalid type argument of ‘unary *’
PFProAPI.c:89: error: invalid type argument of ‘unary *’
PFProAPI.c:89: error: invalid type argument of ‘unary *’
PFProAPI.c:89: error: invalid type argument of ‘unary *’
PFProAPI.c:89: error: invalid type argument of ‘unary *’
PFProAPI.c:90: error: invalid type argument of ‘unary *’
PFProAPI.c:90: error: invalid type argument of ‘unary *’
PFProAPI.c:90: error: invalid type argument of ‘unary *’
PFProAPI.c:90: error: invalid type argument of ‘unary *’
PFProAPI.c:92: error: invalid type argument of ‘unary *’
PFProAPI.c:92: error: invalid type argument of ‘unary *’
PFProAPI.c:92: error: invalid type argument of ‘unary *’
PFProAPI.c:92: error: invalid type argument of ‘unary *’
PFProAPI.c:95: error: invalid type argument of ‘unary *’
PFProAPI.c:95: error: invalid type argument of ‘unary *’
PFProAPI.c:96: error: invalid type argument of ‘unary *’
PFProAPI.c:96: error: invalid type argument of ‘unary *’
PFProAPI.c:96: error: invalid type argument of ‘unary *’
PFProAPI.c:97: error: invalid type argument of ‘unary *’
PFProAPI.c:97: error: invalid type argument of ‘unary *’
PFProAPI.c:97: error: invalid type argument of ‘unary *’
PFProAPI.c:99: error: invalid type argument of ‘unary *’
PFProAPI.c:99: error: invalid type argument of ‘unary *’
PFProAPI.c: In function ‘XS_PFProAPI_pfproDestroyContext’:
PFProAPI.c:106: error: invalid type argument of ‘unary *’
PFProAPI.c:106: error: invalid type argument of ‘unary *’
PFProAPI.c:106: error: invalid type argument of ‘unary *’
PFProAPI.c:108: error: invalid type argument of ‘unary *’
PFProAPI.c:110: error: invalid type argument of ‘unary *’
PFProAPI.c:110: error: invalid type argument of ‘unary *’
PFProAPI.c:110: error: invalid type argument of ‘unary *’
PFProAPI.c:110: error: invalid type argument of ‘unary *’
PFProAPI.c:112: error: invalid type argument of ‘unary *’
PFProAPI.c:112: error: invalid type argument of ‘unary *’
PFProAPI.c:112: error: invalid type argument of ‘unary *’
PFProAPI.c:112: error: invalid type argument of ‘unary *’
PFProAPI.c:115: error: invalid type argument of ‘unary *’
PFProAPI.c:115: error: invalid type argument of ‘unary *’
PFProAPI.c:115: error: invalid type argument of ‘unary *’
PFProAPI.c:117: error: invalid type argument of ‘unary *’
PFProAPI.c:117: error: invalid type argument of ‘unary *’
PFProAPI.c: In function ‘XS_PFProAPI_pfproSubmitTransaction’:
PFProAPI.c:124: error: invalid type argument of ‘unary *’
PFProAPI.c:124: error: invalid type argument of ‘unary *’
PFProAPI.c:124: error: invalid type argument of ‘unary *’
PFProAPI.c:126: error: invalid type argument of ‘unary *’
PFProAPI.c:128: error: invalid type argument of ‘unary *’
PFProAPI.c:128: error: invalid type argument of ‘unary *’
PFProAPI.c:128: error: invalid type argument of ‘unary *’
PFProAPI.c:128: error: invalid type argument of ‘unary *’
PFProAPI.c:129: error: invalid type argument of ‘unary *’
PFProAPI.c:129: error: invalid type argument of ‘unary *’
PFProAPI.c:129: error: invalid type argument of ‘unary *’
PFProAPI.c:129: error: invalid type argument of ‘unary *’
PFProAPI.c:130: error: invalid type argument of ‘unary *’
PFProAPI.c:130: error: invalid type argument of ‘unary *’
PFProAPI.c:130: error: invalid type argument of ‘unary *’
PFProAPI.c:130: error: invalid type argument of ‘unary *’
PFProAPI.c:131: error: invalid type argument of ‘unary *’
PFProAPI.c:131: error: invalid type argument of ‘unary *’
PFProAPI.c:131: error: invalid type argument of ‘unary *’
PFProAPI.c:131: error: invalid type argument of ‘unary *’
PFProAPI.c:133: error: invalid type argument of ‘unary *’
PFProAPI.c:133: error: invalid type argument of ‘unary *’
PFProAPI.c:133: error: invalid type argument of ‘unary *’
PFProAPI.c:133: error: invalid type argument of ‘unary *’
PFProAPI.xs:72: warning: incompatible implicit declaration of built-in function ‘strstr’
PFProAPI.xs:74: warning: incompatible implicit declaration of built-in function ‘malloc’
PFProAPI.xs:74: warning: incompatible implicit declaration of built-in function ‘strlen’
PFProAPI.xs:75: warning: incompatible implicit declaration of built-in function ‘strcpy’
PFProAPI.xs:76: warning: incompatible implicit declaration of built-in function ‘strcat’
PFProAPI.xs:79: warning: incompatible implicit declaration of built-in function ‘strlen’
PFProAPI.xs:81: error: invalid type argument of ‘unary *’
PFProAPI.xs:81: error: invalid type argument of ‘unary *’
PFProAPI.xs:81: error: invalid type argument of ‘unary *’
PFProAPI.xs:81: error: invalid type argument of ‘unary *’
PFProAPI.xs:82: warning: incompatible implicit declaration of built-in function ‘strcpy’
PFProAPI.c:153: error: invalid type argument of ‘unary *’
PFProAPI.c:153: error: invalid type argument of ‘unary *’
PFProAPI.c:154: error: invalid type argument of ‘unary *’
PFProAPI.c:154: error: invalid type argument of ‘unary *’
PFProAPI.c:154: error: invalid type argument of ‘unary *’
PFProAPI.c:156: error: invalid type argument of ‘unary *’
PFProAPI.c:156: error: invalid type argument of ‘unary *’
PFProAPI.c: In function ‘boot_PFProAPI’:
PFProAPI.c:165: error: invalid type argument of ‘unary *’
PFProAPI.c:165: error: invalid type argument of ‘unary *’
PFProAPI.c:165: error: invalid type argument of ‘unary *’
PFProAPI.c:168: error: invalid type argument of ‘unary *’
PFProAPI.c:168: error: invalid type argument of ‘unary *’
PFProAPI.c:168: error: invalid type argument of ‘unary *’
PFProAPI.c:168: error: invalid type argument of ‘unary *’
PFProAPI.c:168: error: invalid type argument of ‘unary *’
PFProAPI.c:168: error: invalid type argument of ‘unary *’
PFProAPI.c:168: error: invalid type argument of ‘unary *’
PFProAPI.c:168: error: invalid type argument of ‘unary *’
PFProAPI.c:168: error: invalid type argument of ‘unary *’
PFProAPI.c:168: error: invalid type argument of ‘unary *’
PFProAPI.c:168: error: invalid type argument of ‘unary *’
PFProAPI.c:170: error: invalid type argument of ‘unary *’
PFProAPI.c:171: error: invalid type argument of ‘unary *’
PFProAPI.c:172: error: invalid type argument of ‘unary *’
PFProAPI.c:173: error: invalid type argument of ‘unary *’
PFProAPI.c:174: error: invalid type argument of ‘unary *’
PFProAPI.c:175: error: invalid type argument of ‘unary *’
PFProAPI.c:175: error: invalid type argument of ‘unary *’
PFProAPI.c:175: error: invalid type argument of ‘unary *’
PFProAPI.c:175: error: invalid type argument of ‘unary *’
make: *** [PFProAPI.o] Error 1


```

---

### Post by analog on 2006-12-05
bump - anyone?? I'm desperate...

---

