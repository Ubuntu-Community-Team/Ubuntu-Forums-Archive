---
title: "valgrind wrongly installed?"
date: 2005-10-21
forum: General Help
---

### Post by enric on 2005-10-21
When I run this minimal program through valgrind

```
int main(){return 42;}
```

I get tons of errors.  My breezy installation is clean (dist-updated from hoary without problems), so this problem should be reproducible.

The output of the command

```
valgrind -v --tool=memcheck ./a.out
```

follows.  Notice the CRC errors, are they important?

I can write a suppression file for that, but this problem should'nt happen in the first place.

```
==13252== Memcheck, a memory error detector.
==13252== Copyright (C) 2002-2005, and GNU GPL'd, by Julian Seward et al.
==13252== Using LibVEX rev 1367, a library for dynamic binary translation.
==13252== Copyright (C) 2004-2005, and GNU GPL'd, by OpenWorks LLP.
==13252== Using valgrind-3.0.1, a dynamic binary instrumentation framework.
==13252== Copyright (C) 2000-2005, and GNU GPL'd, by Julian Seward et al.
--13252-- Valgrind library directory: /usr/lib/valgrind
--13252-- Command line
--13252--    ./a.out
--13252-- Startup, with flags:
--13252--    -v
--13252--    --tool=memcheck
--13252-- Contents of /proc/version:
--13252--   Linux version 2.6.12-9-686-smp (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 SMP Mon Oct 10 13:36:57 BST 2005
--13252-- Reading syms from /home/coco/fines/plips/a.out (0x8048000)
--13252-- Reading syms from /lib/ld-2.3.5.so (0x1B8E4000)
--13252-- Reading debug info from /lib/ld-2.3.5.so...
--13252-- ... CRC mismatch (computed 800128CC wanted 1E4DA335)
--13252--    object doesn't have a symbol table
--13252-- Reading syms from /usr/lib/valgrind/stage2 (0xB0000000)
--13252-- Reading suppressions file: /usr/lib/valgrind/default.supp
==13252== 
--13252-- Reading syms from /usr/lib/valgrind/vg_preload_core.so (0x1B8FD000)
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8F4C7D: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8EA24D: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E483C: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8EF105: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4908: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E72F0: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
==13252== 
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8F4C8C: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8EA24D: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E483C: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8EF105: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4908: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E72F0: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
==13252== 
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8F4C9B: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8EA24D: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E483C: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8EF105: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4908: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E72F0: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
--13252-- Reading syms from /usr/lib/valgrind/vgpreload_memcheck.so (0x1B8FF000)
--13252-- Reading syms from /lib/tls/i686/cmov/libc-2.3.5.so (0x1B919000)
--13252-- Reading debug info from /lib/tls/i686/cmov/libc-2.3.5.so...
--13252-- ... CRC mismatch (computed 704BED0A wanted 3F3A62A9)
--13252--    object doesn't have a symbol table
--13252-- Reading syms from /lib/tls/i686/cmov/libdl-2.3.5.so (0x1BA47000)
--13252-- Reading debug info from /lib/tls/i686/cmov/libdl-2.3.5.so...
--13252-- ... CRC mismatch (computed D54E3219 wanted 2A495871)
--13252--    object doesn't have a symbol table
==13252== 
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8EC82D: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E6403: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
==13252== 
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8EC852: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E6403: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
==13252== 
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8EC6F7: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E6455: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
==13252== 
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8EC700: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E6455: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
==13252== 
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8EC852: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E6455: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
--13252-- REDIR: 0x1B9834A0 (rindex) redirected to 0x1B902192 (rindex)
--13252-- REDIR: 0x1B97C240 (free) redirected to 0x1B9013D1 (free)
--13252-- REDIR: 0x1B9842F0 (memset) redirected to 0x1B9025F5 (memset)
==13252== 
==13252== ERROR SUMMARY: 16 errors from 8 contexts (suppressed: 0 from 0)
==13252== 
==13252== 1 errors in context 1 of 8:
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8EC852: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E6455: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
==13252== 
==13252== 1 errors in context 2 of 8:
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8EC700: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E6455: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
==13252== 
==13252== 1 errors in context 3 of 8:
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8EC6F7: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E6455: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
==13252== 
==13252== 1 errors in context 4 of 8:
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8F4C9B: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8EA24D: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E483C: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8EF105: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4908: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E72F0: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
==13252== 
==13252== 1 errors in context 5 of 8:
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8F4C8C: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8EA24D: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E483C: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8EF105: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4908: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E72F0: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
==13252== 
==13252== 1 errors in context 6 of 8:
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8F4C7D: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8EA24D: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E483C: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8EF105: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4908: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E72F0: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
==13252== 
==13252== 5 errors in context 7 of 8:
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8EC852: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E6403: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
==13252== 
==13252== 5 errors in context 8 of 8:
==13252== Conditional jump or move depends on uninitialised value(s)
==13252==    at 0x1B8EC82D: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E6403: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8F254A: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4CE6: (within /lib/ld-2.3.5.so)
==13252==    by 0x1B8E4796: (within /lib/ld-2.3.5.so)
==13252== IN SUMMARY: 16 errors from 8 contexts (suppressed: 0 from 0)
==13252== 
==13252== malloc/free: in use at exit: 0 bytes in 0 blocks.
==13252== malloc/free: 0 allocs, 0 frees, 0 bytes allocated.
==13252== 
==13252== No malloc'd blocks -- no leaks are possible.
--13252--  memcheck: sanity checks: 0 cheap, 1 expensive
--13252--  memcheck: auxmaps: 0 auxmap entries (0k, 0M) in use
--13252--  memcheck: auxmaps: 0 searches, 0 comparisons
--13252--  memcheck: secondaries: 8 issued (512k, 0M)
--13252--  memcheck: secondaries: 18 accessible and distinguished (1152k, 1M)
--13252--     tt/tc: 3234 tt lookups requiring 3287 probes
--13252--     tt/tc: 3234 fast-cache updates, 2 flushes
--13252-- translate: new        1617 (33775 -> 559056; ratio 165:10) [0 scs]
--13252-- translate: dumped     0 (0 -> ??)
--13252-- translate: discarded  0 (0 -> ??)
--13252-- scheduler: 30833 jumps (bb entries).
--13252-- scheduler: 0/1727 major/minor sched events.
--13252--    sanity: 1 cheap, 1 expensive checks.
--13252--    exectx: 4999 lists, 8 contexts (avg 0 per list)
--13252--    exectx: 16 searches, 8 full compares (500 per 1000)
--13252--    exectx: 0 cmp2, 44 cmp4, 0 cmpAll
```

---

### Post by rante on 2006-03-30
why does that happen on ubuntu? A friend of mine also has the same problem (besides me). Valgrind gives that inicial output when runned with any C program. I have seen this personaly in 3 diferent computers. Any one knows whats the problem?

thanks!

---

### Post by rante on 2006-04-02
nobody has the same problem?

---

